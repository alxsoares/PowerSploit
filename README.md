### PowerSploit is a collection of Microsoft PowerShell modules and scripts that can be used to aid reverse engineers, forensic analysts, and penetration testers during all phases of an assessment. PowerSploit is comprised of the following scripts and modules:

## Root Directory

#### `Inject-Dll`

Inject-Dll injects a Dll into the process ID of your choosing.

#### `Inject-Shellcode`

Inject-Shellcode injects shellcode into the process ID of your choosing or within PowerShell locally.

#### `Find-AVSignature`

Locates single Byte AV signatures utilizing the same method as DSplit from "class101".

#### `Get-GPPPassword`

Get-GPPPassword retrieves the plaintext password for accounts pushed through Group Policy in groups.xml.

#### `Get-TimedScreenshot`

A function that takes screenshots at a regular interval and saves them to a folder.

## .\ScriptModification

**A PowerShell module used to modify and/or prepare scripts for execution on a compromised machine.**

#### `Out-EncodedCommand`

Compresses, Base-64 encodes, and generates command-line output for a PowerShell payload script.

#### `Out-CompressedDll`

Compresses, Base-64 encodes, and outputs generated code to load a managed dll in memory.

#### `Out-EncryptedScript`

Encrypts text files/scripts.

#### `Remove-Comments`

Strips comments and extra whitespace from a script. 

## .\PETools

**A PowerShell module used to parse/manipulate Windows portable executables**

#### `Get-PEHeader`

Get-PEHeader is an in-memory and on-disk PE parsing utility.

#### `Get-PEArchitecture`

Get-PEArchitecture returns the architecture for which an executable was compiled.

#### `Get-DllLoadPath`

Get-DllLoadPath returns the path from which Windows will load a Dll for the given executable.

## .\ReverseEngineering

**Tools to aid in reverse engineering**

#### `Get-PEB`

Returns the process environment block (PEB) of a process.

#### `Get-ILDisassembly`

Disassembles a raw MSIL byte array passed in from a MethodInfo object in a manner similar to that of Ildasm.

#### `Get-KernelModuleInfo`

Returns loaded kernel module information.

#### `Get-StructFromMemory`

Marshals data from an unmanaged block of memory in an arbitrary process to a newly allocated managed object of the specified type.

#### `Get-Member`

A proxy function used to extend the built-in Get-Member cmdlet. It adds the '-Private' parameter allowing you to display non-public .NET members

#### `Get-Strings`

Dumps strings from files in both Unicode and Ascii. This cmdlet replicates the functionality of strings.exe from Sysinternals.

#### `Get-MethodAddress`

Get the unmanaged function address of a .NET method.

## .\Recon

**Tools to aid in the reconnaissance phase of a penetration test**

#### `Get-HttpStatus`

Returns the HTTP Status Codes and full URL for specified paths when provided with a dictionary file.

#### `Invoke-ReverseDnsLookup`

Invoke-ReverseDnsLookup scans an IP address range for DNS PTR records. This script is useful for performing DNS reconnaissance prior to conducting an authorized penetration test.

## .\Recon\Dictionaries

**A collection of dictionaries used to aid in the reconnaissance phase of a penetration test. Dictionaries were taken from the following sources**

* admin.txt - <http://cirt.net/nikto2/>
* generic.txt - <http://sourceforge.net/projects/yokoso/files/yokoso-0.1/>
* sharepoint.txt - <http://www.stachliu.com/resources/tools/sharepoint-hacking-diggity-project/>

## License

The PowerSploit project and all individual scripts are under the [BSD 3-Clause license](https://raw.github.com/mattifestation/PowerSploit/master/LICENSE).

## Usage

Refer to the comment-based help in each individual script for detailed usage information.

## Script Style Guide

**For all contributors and future contributors to PowerSploit, I ask that you follow this style guide when writing your scripts/modules.**

* Avoid Write-Host **at all costs**. You should output custom objects instead. For more information on creating custom objects, read these articles:
   * <http://blogs.technet.com/b/heyscriptingguy/archive/2011/05/19/create-custom-objects-in-your-powershell-script.aspx>
   * <http://technet.microsoft.com/en-us/library/ff730946.aspx>

* If you want to display relevant debugging information to the screen, use Write-Verbose. The user can always just tack on '-Verbose'.

* Always provide descriptive, comment-based help for every script. Also, be sure to include your name and a BSD 3-Clause license.

* Make sure all functions follow the proper PowerShell verb-noun agreement. Use Get-Verb to list the default verbs used by PowerShell.

* I prefer that variable names be capitalized and be as descriptive as possible.

* Provide logical spacing in between your code. Indent your code to make it more readable.

* If you find yourself repeating code, write a function.

* Catch all anticipated errors and provide meaningful output. If you have an error that should stop execution of the script, use 'Throw'. If you have an error that doesn't need to stop execution, use Write-Error.

* If you are writing a script that interfaces with the Win32 API, do not compile C# code unless absolutely necessary. It is imperative that nothing aside from the script touches the disk.

* Do not use hardcoded paths. A script should be useable right out of the box. No one should have to modify the code unless they want to.

* I don't want any v3 dependencies right now. In fact, it would be ideal to use `Set-StrictMode -Version 2.0` to ensure you are conforming to PowerShell v2 best practices.

* Use positional parameters and make parameters mandatory when it makes sense to do so. For example, I'm looking for something like the following:
   * `[Parameter(Position = 0, Mandatory = $True)]`

* Don't use any aliases unless it makes sense for receiving pipeline input. They make code more difficult to read for people who are unfamiliar with a particular alias.

* Don't let commands run on for too long. For example, a pipeline is a natural place for a line break.

* Don't go overboard with inline comments. Only use them when certain aspects of the code might be confusing to a reader.

* Use Out-Null to suppress unwanted/irrelevant output.

* Only use .NET code when absolutely necessary.

* Use the Write-Output keyword when returning an object from a function. I know it's not necessary but it makes the code more readable.

* Use default values for your parameters when it makes sense. Ideally, you want a script that will work without requiring any parameters.

* Scripts that are intended to run on a remote machine should be self-contained and not rely upon any additional scripts. Scripts that are designed to run on your host machine can have dependencies on other scripts.

* If a script creates complex custom objects, include a ps1xml file that will properly format the object's output.