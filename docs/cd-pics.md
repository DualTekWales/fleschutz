*cd-pics.ps1*
================

This PowerShell script changes the working directory to the user's pictures folder.

Parameters
----------
```powershell
PS> ./cd-pics.ps1 [<CommonParameters>]

[<CommonParameters>]
    This script supports the common parameters: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, 
    WarningVariable, OutBuffer, PipelineVariable, and OutVariable.
```

Example
-------
```powershell
PS> ./cd-pics
📂C:\Users\Markus\Pictures

```

Notes
-----
Author: Markus Fleschutz | License: CC0

Related Links
-------------
https://github.com/fleschutz/PowerShell

Script Content
--------------
```powershell
<#
.SYNOPSIS
	Sets the working directory to the user's pictures folder
.DESCRIPTION
	This PowerShell script changes the working directory to the user's pictures folder.
.EXAMPLE
	PS> ./cd-pics
	📂C:\Users\Markus\Pictures
.LINK
	https://github.com/fleschutz/PowerShell
.NOTES
	Author: Markus Fleschutz | License: CC0
#>

try {
	if ($IsLinux) {
		$Path = Resolve-Path "$HOME/Pictures"
	} else {
		$Path = [Environment]::GetFolderPath('MyPictures')
	}
	if (-not(Test-Path "$Path" -pathType container)) { throw "Pictures folder at 📂$Path doesn't exist (yet)" }
	Set-Location "$Path"
	"📂$Path"
	exit 0 # success
} catch {
	"⚠️ Error in line $($_.InvocationInfo.ScriptLineNumber): $($Error[0])"
	exit 1
}
```

*(generated by convert-ps2md.ps1 using the comment-based help of cd-pics.ps1 as of 10/19/2023 08:11:35)*