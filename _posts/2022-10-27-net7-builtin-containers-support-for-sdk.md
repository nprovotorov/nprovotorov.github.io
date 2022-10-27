---
title: '.NET 7 Built-in container support for the .NET SDK'
date: '2021-07-03'
categories:
- Development
tags:
- dotNET
- Docker
---

Recently .NET team 
[announced](https://devblogs.microsoft.com/dotnet/announcing-builtin-container-support-for-the-dotnet-sdk/)
 built-in container support for the .NET SDK.

# What does it mean?

You can skip learning Docker, Dockerfiles, etc. and instead just YOLO:

``` bash
# create app
dotnet new mvc -n my-shiny-app
cd my-shiny-app

# build, publish and run docker container
dotnet add package Microsoft.NET.Build.Containers # you will not need this after final Release of this feature
dotnet publish --os linux --arch x64 -c Release -p:PublishProfile=DefaultContainer
docker run -it --rm -p 5010:80 my-shiny-app:1.0.0
```
This will give you a fully working docker image, pushed to your local docker daemon 
registry.

![YOLO everywhere](../assets/images/2022-10-27-net7-builtin-containers-support-for-sdk/yolo-yolo-everywhere.jpg)

# Pros of built-in container support in .NET 7 SDK

1. Simplification - it is built-in into your standard toolchain - no need 
(both for you and for your CI/CD pipeline) to learn new instruments, use new 
tools
2. Unification - it uses some standard approaches to build images and _may_ 
(or may not - couldn't find any roadmap on that matter) apply and enforce some 
best practices (maybe even security checks) - but it is not doing that as of now

# Cons of built-in container support in .NET 7 SDK

1. Black magic - this is black magic happening behind the scenes and we 
don't have good visibility on what's going on and how exactly these containers 
are built
2. As of now only `linux-x64` images are supported (will be fixed in future)
3. As of now you can't publish images to docker registries with authentication 
(will be fixed in future)

# Are there any analogues for built-in container support in .NET 7 SDK in other technology stacks?

It appears - Yes:
1. [Jib](https://github.com/GoogleContainerTools/jib) for Java
2. [Ko](https://github.com/ko-build/ko) for Go
3. [Konet](https://github.com/lippertmarkus/konet) for .NET

But all of the tools above highlight that they don't use `docker` to build images
 and that they do it super fast.
It doesn't seem to be the case with the new `dotnet publish`  - 
I couldn't build an image until I launched docker daemon.

# Should I use built-in container support in .NET 7 SDK (my humble opinion)

I don't think I like this feature in the way it works right now - 
it's perfectly OK for simple use cases, hello worlds, etc. but in large production
projects (especially in multi-tech-stacks companies) I would most likely 
refrain from using in.

We already have a standardized way of describing, building, checking, etc. for
containers and, most important, it doesn't depend on what technology you
are using for your application. It is always the same way. 

So our engineers, who know how to work with docker, can work with any app and 
don't care too much about what was it built with. But with that kind of tool,
they will have to care.

Considering all of that tools have their own different configurations, different defaults,
different CLIs, this will increase complexity and reduce our ability to
abstract ourselves from underlying technology and use common tools like 
Dockerfiles linting. 

By using different tools, depending on the app's technology stack, to build 
containers we no longer have one standard way of building containers (but still
 have more or less standardized ways of running them) - which I don't see as a 
 good thing (at least for now).

I think we need some very good reasons and profit from using such tools to 
consider using them at scale. I don't see them yet for .NET SDK (but, hey, 
that's me - maybe you do).