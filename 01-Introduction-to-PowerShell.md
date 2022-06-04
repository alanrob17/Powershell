# Chapter 1 - Introduction to Powershell

## What is PowerShell?

PowerShell is a mixture of a command line, a functional programming language, and an object-oriented programming language. PowerShell is based on Microsoft .NET, which gives it a level of open flexibility that was not available in Microsoft's scripting languages (such as VBScript or batch) before this.

## Getting help

Gaining confidence using the built-in help system is an important part of working with PowerShell. In PowerShell, help is extensive; authors can easily write their own help content when working with functions, scripts, and script modules.

A number of commands are available to interact with the help system, as follows:

* Get-Help
* Save-Help
* Update-Help

### Update-Help

Help may not be available on your system after installation so we need to install or update it.

#### Which modules support updatable help?

A list of modules that support updatable help may be viewed by running the following command:

```powershell
    Get-Module -ListAvailable | Where-Object HelpInfoURI -like *
```

**Note:**  The first time ``Get-Help`` is run, you will be prompted to update help.

### The Get-Help command

Without any arguments or parameters, Get-Help will show introductory help about the help system. This content is taken from the default help file (Get-Help default);

```powershell
    Get-Help
```

A snippet of the help is.

> TOPIC     
>   PowerShell Help System        
>       
> SHORT DESCRIPTION     
>   Displays help about PowerShell cmdlets and concepts.        
>       
> LONG DESCRIPTION      
> PowerShell Help describes PowerShell cmdlets, functions, scripts, and     
> modules, and explains concepts, including the elements of the PowerShell      
> language.     
> ...
