---
title: 'C# 9 Record type'
date: '2021-07-03'
categories:
- Development
tags:
- dotNET
- CSharp
---

## When I should consider using record?

You want:

- reference type, but the comparison should be based on values of properties
- immutable entity. Usage of immutable entities is widely recommended as it increases the application's behavior predictability and reduces the number of bugs and issues
- support for inheritance hierarchies

**TLDR**: you want to store immutable data, preserving the ability to pass instances by reference.

## How to use it?

`record` type is available starting with .NET 5 and C# 9.0.

### Declaring records records

You can declare `record` using positional constructor:

```csharp
public record Car(string Manufacturer, string Model, decimal Price);
```

or more traditional syntax:

```csharp
public record Vehicle()
{
    public string Manufacturer { get; init; } // technically, you can
    public string Model { get; init; } // declare it as { get;set; }
    public decimal Price { get; init; } // but don't do it :)
}
```

or you can declare standard properties in addition to positionals:

```csharp
public record CarWithMileage(string Manufacturer, string Model, decimal Price)
{
    public int Mileage { get; init; }
}
```

### Using records

```csharp
// create new instance
var car = new Car("Tesla", "Model S", 50000.00m);
// you can do like this
var otherCar = new Car(Manufacturer: "Ford", Model: "Explorer", Price: 60000.0m);
```

or like this, if you don't have positional properties:

```csharp
Vehicle another = new Vehicle()
{
    Manufacturer = "Toyota",
    Model = "Camry",
    Price = 25000.0m
};

```

or like this if you have positional and standard properties:

```csharp
var carWithMileage = new CarWithMileage("VAZ", "2109", 100.0m)
{
    Mileage = 340000
};
```

### Record comparison

`record`s are compared by values:

```csharp
var car = new Car("Tesla", "Model S", 50000.00m);
var sameCar = new Car("Tesla", "Model S", 50000.00m);
Console.WriteLine(car == sameCar); // true
```

![same picture meme](/assets/images/dotnet-records/same_pic.jpg)

For comparison repeat this with `class` type:

```csharp
public class ClassCar
{
    public ClassCar(string manufacturer, string model, decimal price)
    {
        Manufacturer = manufacturer;
        Model = model;
        Price = price;
    }
    public string Manufacturer { get; init; }
    public string Model { get; init; }
    public decimal Price { get; init; }
}

// ...

var classCar = new ClassCar("Tesla", "Model S", 50000.00m);
var sameClassCar = new ClassCar("Tesla", "Model S", 50000.00m);
Console.WriteLine(classCar == sameClassCar); // false
```

## Mutating records (or editing them)

So, how do you mutate the immutable?

![mutate the immutable](/assets/images/dotnet-records/mutate.jpg)

You should use `with` expression to make a new `record` instance based on existing `record` with some modifications - this is called `nondestructive mutation`.

```csharp
var car = new Car("Tesla", "Model S", 50000.0m);
var carWithDiscount = car with { Price = 45000.0m };
Console.WriteLine(car); // Car { Manufacturer = Tesla, Model = Model S, Price = 50000.0 }
Console.WriteLine(carWithDiscount); // Car { Manufacturer = Tesla, Model = Model S, Price = 45000.0 }
```

_Note: `with` makes a shallow copy - reference properties will reference the same object as they were in original `record`._

JavaScript users use `spread syntax` to achieve the same thing:

```javascript
const updatedObject = { ...oldObject, someProperty: 'new value' }
```

## Nice features

### Record inheritance

Just works. But only for `record`s - you can't inherit `class`.
If you want to compare `record`s both instances should be of the same run-time type or they will be considered non-equal without comparing their properties.

### ToString() Formatting

ToString method returns human readable data:

```csharp
Car { Manufacturer = Tesla, Model = Model S, Price = 50000.0 }
```

You can customize this by providing own `PrintMembers` method (see [here](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/records#define-compiler-synthesized-methods)).

### Deconstruction

Have you ever envied JavaScript programmers because they could do this?

```javascript
const user = {
  id: 42,
  is_verified: true,
}

const { id, is_verified } = user // destructuring

console.log(id) // 42
console.log(is_verified) // true
```

_Example from [Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#object_destructuring)_

Now you can do this:

```csharp
var (manufacturer, model, price) = car;
```

But this only works with positional properties - for standard properties you will need to provide `Deconstruct` method (see [here](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/functional/deconstruct#user-defined-types)):

```csharp
public void Deconstruct(out string something, out string otherthing)
```

### Performance

`record`s value equality works measurably faster than struct's one.

## How to choose between class, struct, record (class vs record)

Use

- `class` - if you want reference types, supporting hierarchies and focusing on class' responsibility and behavoir
- `record` - if you want immutable reference types, supporting hierarchies and focusing on storing data
- `struct` - if you want just to store some data and don't need anything above

## Records and Entity Framework Core

With `EFCore` you will need some additional actions to update a record:

```csharp
var report = dbContext.Set<MyReport>().AsNoTracking().First(...some linq query...);
var updatedReport = report with {ReadyToUse = true};
dbContext.Update(updatedRecord);
dbContext.SaveChanges();
```

via RenierGlez@[StackOverflow](https://stackoverflow.com/a/65868071).

## How does it work?

Compiler generates `class` and augments it with some synthesized methods and overrides:

- Object.Equals(Object)
- virtual Equals(T)
- Object.GetHashCode()
- operator== and operator!=
- implements `System.IEquatable<T>`
- ToString()

For `with` expression compiler generates a clone method and a copy constructor.

Here are some IL code for `Car` `record`:

```csharp
// so it's a class
.class /* 02000006 */ public auto ansi beforefieldinit RecordExample.Car
	extends [System.Runtime]System.Object
	implements class [System.Runtime]System.IEquatable`1<class RecordExample.Car>

// ...
// ToString implementation
.method /* 0600000F */ public hidebysig virtual
		instance string ToString () cil managed
	{
// ...
// Clone method
.method /* 06000016 */ public hidebysig newslot virtual
		instance class RecordExample.Car '<Clone>$' () cil managed

```
