# Check-SqlInstance
Check-SqlInstance uses Powershell to return selected information about a SQL Server instance.  The Comment-based help is excepted below.  You can also access it using Get-Help.

This is the code for the post [Returning Basic Instance Information with Powershell](https://shoestringdba.com/?p=662).

```
<#
    .SYNOPSIS
    This script extracts some basic properties of a SQL Server instance and
    it's databases then exports them to a text file.

    .DESCRIPTION
    The script creates a text file containing a number of properties that are
    important to know about a SQL Server instance.  The file is divided into
    sections.

    [Instance Information]
    Lists the Version, Edition, Version Level, Update level and Login Mode for
    the instance.  Details can be found at
    https://docs.microsoft.com/en-us/sql/t-sql/functions/serverproperty-transact-sql?view=sql-server-2017


    [Memory and Parallelism]
    Lists the Minimum Memory, Maximum Memory, Max Degree of Parallelism and
    Cost Threshold for Parallelism values.

    [Databases]
    Lists all databases on the instance, along with Compatibility Level,
    status, owner plus AutoClose and AutoShrink settings.

    [Backups]
    Lists the Recovery Model, plus the dates/times for the last Full,
    Differential and Log backups.

    .PARAMETER instancename
    Required.  The name of the instance to be checked.

    .PARAMETER outfile
    Optional.  Path and filename for the output of the command.  Defaults to
    .\Check-SqlInstanceResults.txt

    .PARAMETER errorfile
    Optional.  Path and filename for the output errors, if any.  Defaults to
    .\Check-SqlInstanceErrors.txt

    .INPUTS
    None.

    .OUTPUTS
    None.

    .NOTES
    The script requires the SqlServer Powershell module.  You can get this by
    executing Install-Module -Name SqlServer.

    If the script encounters an exception, the exception will be written to the
    ErrorLog.txt file in the current directory.

    .EXAMPLE
    PS> Check-SqlInstance.ps1 -instancename "MyInstance"

    Check the "MyInstance" instance and output results or errors to default (current) directory.

    .EXAMPLE
    PS> Check-SqlInstance.ps1 -instancename "MyInstance" -outfile "C:\Users\username\Documents\Check-SqlInstanceResults.txt"

    Check the "MyInstance" instance and output results to custom path or errors to default (current) directory.

    .EXAMPLE
    PS> Check-SqlInstance.ps1 -instancename "MyInstance" -outfile "C:\Users\username\Documents\Check-SqlInstanceResults.txt"
        -errorfile "C:\Users\username\Documents\Check-SqlInstanceErrors.txt"

    Check the "MyInstance" instance and output results or errors to custom path.
#>
```
