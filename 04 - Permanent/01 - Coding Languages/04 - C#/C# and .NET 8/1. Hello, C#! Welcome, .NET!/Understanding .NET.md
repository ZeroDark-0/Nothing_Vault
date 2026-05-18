---
date: 2025-12-28T23:21
tags: []
---

## <code style = "color:blue">Understanding .NET  support</code> 

So the .NET have some types of version like **LTS(Long Term Support**, **STS(Short Term Support)**, and **Preview**.
Basically there are the type for the updates you will be getting on .NET described as follows..

+ ***LTS*** >> do not intend to update frequently, LTS releases are supported by Microsoft for 3 years after **General Availability** (**GA**).
  
+ ***STS*** >> releases include features that may change based on feedback, STS releases are supported by Microsoft for 18 months after GA.
  
+ ***Preview*** >> releases are for public testing, Preview releases are not usually supported by Microsoft, but some preview or **Release Candidate** (**RC**) releases may be declared **Go Live**, meaning they are supported by Microsoft in production.


## <code style = "color:cyan">Understanding intermediate language</code>

The C# complier (named <code style="color:orange"><b>Roslyn</b></code>) used by the dotnet CLI tool converts C# code into Intermediate Language and then save that in the assembly ***(DLL or EXE)***. The Intermediate language are like assembly language which are executed by .NET's virtual machine known as CoreCLR. 

At the runtime, CoreCLR loads the Intermediate Language from the assembly, the just-in-time(JIT complier) compiles it into naive CPU instruction, and then it executed by the CPU on your machine..

#### -> why the two step compilation?

this can create Common Language Runtimes (CLRs) for Linux and macOS as well as Windows..
