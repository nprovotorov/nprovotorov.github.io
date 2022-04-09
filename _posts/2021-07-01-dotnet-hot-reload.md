---
title: 'dotNET Hot Reload is Awesome'
date: '2021-07-01'
categories:
- Development
tags: 
- "dotNET"
- "ASP.NET Core"
- "Inner loop"
---

## Why do I need it?

Ever done something like this?

1. Build your app
2. Wait for it to start
3. Recognize that you need to change something
4. Stop your app
5. Change the code
6. `GOTO 1` and wait again and again

With `.NET 6` you can do this:

1. Build your app
2. Wait for it to start
3. Recognize that you need to change something
4. Change the code
5. Immediately see the result

No more rebuilding and restarting for every little change.

That makes the developer's inner loop faster by reducing the time between code change and seeing the result.

*Note: some other languages had this feature for YEARS.*

## What is .NET Hot Reload?

[Improve inner-loop performance for .NET developers](https://github.com/dotnet/core/issues/5510) is one of the main themes for `.NET 6`.

This theme aims at two goals:

- Improving developer's inner loop and boosting productivity
- Attracting developers from other platforms. Since most of them already have hot reloading, the absence of it in `.NET` is a blocker for switching.

`.NET Hot Reload` watches your source files and applies supported code changes to your running app without restarting it. Application state also preserved.
Unsupported changes (see Limitations section) will lead to rebuild and restart.

Internaly `.NET Hot Reload` uses [Roslyn Edit&Continue](https://github.com/dotnet/roslyn/blob/main/docs/wiki/EnC-Supported-Edits.md) feature.

## How do I use it?

### What you need

You will need [.NET 6.0](https://dotnet.microsoft.com/download/dotnet/6.0):

- `Visual Studio 2019 v.16.11 Preview 1+` or
- `.NET 6 Preview 4+` if you plan to use `Visual Studio Code` or other IDE through the `dotnet watch` command
  
### How to use with Visual Studio 2019

1. Run your app
2. Make _supported_(see Limitations section) code change
3. Press the `Apply code changes` button
4. PROFIT! You will see changes when updated code is re-executed

### How to use VS Code (or other IDE)

1. Run your favorite `Terminal` app
2. Go to your project directory
3. Run `dotnet watch` - it should indicate that `Hot reload enabled`
4. Make _supported_ code change and Save the file
5. Wait a little :)
6. ROFIT! You will see changes when updated code is re-executed

![Hot Reload Enabled](/assets/images/dotnet-hot-reload/dotnet-hot-reload-sc1.png)

## What are the Limitations?

### What types of applications support .NET Hot Reload

`.NET Hot Reload` will work with (it may not correctly work right now, but it will at final release on November'21):

- WPF
- Windows Forms
- .NET MAUI
- ASP.NET Core (including Blazor, Razor pages, MVC)
- Console apps
- and maybe something else

### What changes are _supported_

Not all changes are supported.

Documentation is still in progress, but you can read [Edit&Continue Roslyn docs](https://github.com/dotnet/roslyn/blob/main/docs/wiki/EnC-Supported-Edits.md) and [E&C in Visual Studio](https://docs.microsoft.com/en-gb/visualstudio/debugger/supported-code-changes-csharp?view=vs-2019) for the current list of supported edits.

## When can I use it in Production?

You can start immediately - the `Bing` team [uses](https://devblogs.microsoft.com/dotnet/migration-of-bings-workflow-engine-to-net-5/) `.NET 6` in Production since `Preview 1`.

Or you can wait for `.NET 6 Release` - **November 2021**.
