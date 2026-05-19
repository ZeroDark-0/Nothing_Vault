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


## Exercise 1.1 – Test your knowledge

Try to answer the following questions, remembering that although most answers can be found in this chapter, you should do some online research or code writing to answer others:

1. Is Visual Studio 2022 better than Visual Studio Code?
2. Are .NET 5 and later better than .NET Framework?
3. What is .NET Standard and why is it still important?
4. Why can a programmer use different languages, for example, C# and F#, to write applications that run on .NET?
5. What is a top-level program and how do you access any command-line arguments?
6. What is the name of the entry point method of a .NET console app and how should it be explicitly declared if you are not using the top-level program feature?
7. What namespace is the `Program` class defined in with a top-level program?
8. Where would you look for help for a C# keyword?
9. Where would you look first for solutions to common programming problems?
10. What should you do after getting an AI to write code for you?

#### <code style = "color:red">Answer:</code>

1. yes it is better. the thing is that VS2022 is an IDE meanwhile the VS-code is <code style="color:cyan">source code editor</code>. if we are working for service like backend or like making a software/heavy working backend it is said to use VS2022 because it have supported framework and the packages for that purpose..vscode is light weight meanwhile vs2022 isn't.
2. Yes, .NET 5 and later are generally better — they offer superior performance, cross-platform support (Linux/Mac/Windows), open-source codebase, better cloud/container support, and a unified platform. However, .NET Framework still exists for legacy Windows-only applications and isn't going away anytime soon.
3. 