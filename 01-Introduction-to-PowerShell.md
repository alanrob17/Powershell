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

Or, because the help is usually long.

```powershell
    Get-Help | more
```

An even better method is available in Windows Powershell but not Windows Powershell Core.

```powershell
    Get-Help -ShowWindow
```

This pops up a window with the help contents.

To see a list of all the Help contents.

```powershell
    Get-Help *
```

Or.

```powershell
    Get-Help -Category All
```

Lists all of the commands available.

Help for a command may be viewed as follows:

```powershell
    Get-Help <CommandName>
```

Example:

```powershell
    Get-Help Get-Variable
```

You can also view the Help online.

```powershell
    Get-Help Get-Variable -Online
```

This throws you to Powershell's online help.

### Syntax

The syntax section lists each of the possible combinations of parameters a command will accept; each of these is known as a parameter set.

A command that has more than one parameter set is displayed as follows:

>SYNTAX
>    Get-Process [[-Name] <String[]>] [-ComputerName <String[]>]        
>    [-FileVersionInfo] [-Module] [<CommonParameters>]      
>       
>    Get-Process [-ComputerName [<String[]>]] [-FileVersionInfo]        
>    [-Module] -InputObject <Process[]> [<CommonParameters>]

The syntax elements written in **square brackets** are optional;

Examples of commands:

```powershell
    Get-Process
```

Shows all processes.

```powershell
    Get-Process wsl
```

Returns:

> NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName     
> ------    -----      -----     ------      --  -- -----------     
>     10     1.89       8.38       0.00   20416   1 wsl

You can also use the optional name to get the same result.

```powershell
    Get-Process -Name wsl
```

### Examples

When using the Help you can just list the examples with:

```powershell
    Get-Help Get-Process -Examples
```

This will only show the list of examples for ``Get-Process``.

#### Parameter

Help for specific parameters may be requested as follows:

```powershell
    Get-Help Get-Command -Parameter <ParameterName>
```

Example.

```powershell
    Get-Help Import-Csv -Parameter Path
```

> -Path <System.String[]>       
>     Specifies the path to the CSV file to import. You can also pipe a path to `Import-Csv`.       
>       
>     Required?                    true     
>     Position?                    0        
>     Default value                None     
>     Accept pipeline input?       True (ByPropertyName, ByValue)       
>     Accept wildcard characters?  false

You can search for all parameters.

```powershell
    Get-Help Import-Csv -Parameter *
```

Returns a list of all parameters.

#### Detailed and full switches

The **Detailed** switch parameter asks Get-Help to return the most help content. This adds information about each parameter and the set of examples to name, synopsis, syntax, and description. Related links are excluded when using this parameter.

The Detailed parameter is used as follows:

```powershell
    Get-Help Get-Process -Detailed
```

Using a **Full** switch adds more technical details (compared to using the Detailed parameter). Inputs, outputs, notes, and related links are added to those that are seen using Detailed. For example, the sections detailing input and output types from ``Get-Process`` may be extracted from the full help document:

```powershell
    Get-Help Get-Process –Full
```

### Save-Help

The **Save-Help** command can be used with modules that support updatable help. It saves help content for modules to a folder; for example, the help content for the ``DnsClient`` module can be saved to C:\PSHelp (the directory must already exist):

```powershell
    Save-Help -DestinationPath C:\Temp\PSHelp -Module DnsClient
```

This will save all of the help for ``DnsClient`` in a **.cab** file.

Alternatively, the help content for all modules may be saved as follows:

```powershell
    Save-Help -DestinationPath C:\Temp\PSHelp
```

The process creates an XML formatted HelpInfo file that holds the source of the help content and a CAB (cabinet) file that's named after the module and culture.

Opening the CAB file shows that it contains a number of XML formatted help files.

**Note:** performing this task will take some time.

### Update-Help

The Update-Help command can perform two tasks:

*Update help files from the internet
*Import previously saved help files

**Note:** you have to have Administrator rights to perform this task.

Example:

```powershell
    Update-Help -Module DnsClient -Verbose
```

You can't download the Help file if it has been downloaded less than 24 hours before or if it is up to date. To get around this you can **-Force** the download.

```powershell
    Update-Help -Module DnsClient -Verbose -Force
```

You can also update the Help from a local directory. This is helpful for machines that don't have access to the Internet.

```powershell
    Update-Help -SourcePath C:\temp\PSHelp
```
