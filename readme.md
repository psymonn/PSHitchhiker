# PSHitchhiker

![HitchhikersGuide](HitchhikersGuide.png)

This module is designed for demonstration purposes.

The repo illustrates an automated release pipeline for a simplified PowerShell module.

For more information, please see the post: [Hitchhiker's Guide to the PowerShell Module Pipeline][HitchhikersGuide].

[HitchhikersGuide]: https://xainey.github.io/2017/powershell-module-pipeline/

Jenkins Console for HTML-Reporting:
To allow Jenkins to run inline CSS and JavaScript in the HTML Report we will need to configure the Content Security Policy.

System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "style-src 'self' 'unsafe-inline';")
System.setProperty("hudson.model.DirectoryBrowserSupport.CSP", "")

These settings do not persist when Jenkins is restarted. They can be added to the JAVA_ARGS for startup as seen in this StackOverflow Comment:
https://stackoverflow.com/questions/37618892/jenkins-content-security-policy/37623540#37623540


Create you own internal powershell repo:
https://www.nuget.org/downloads
https://kevinmarquette.github.io/2017-05-30-Powershell-your-first-PSScript-repository/

Register-PSRepository -Name "PsymonCorp" -SourceLocation "F:\Shared Folder\Repo" -InstallationPolicy Trusted

Get-PSRepository
Find-Module -Repository "PsymonCorp"
Install-Module -Name "PSHitchhiker" -Repository "PsymonCorp"
Install-Module -Name "PSHitchhiker" -Repository "PsymonCorp" -Scope CurrentUser

Import-Module PSHitchhiker
get-module

------
Get-PSRepository
Register-PSRepository -Name "Win10Automation" -SourceLocation "C:\Data\App\LocalNuGetFeed\Packages" -InstallationPolicy Trusted
Register-PSRepository -Name "LocalNuGetFeed" -SourceLocation "http://localhost:8087/nuget" -InstallationPolicy Trusted
Find-Module -name "PSHitchhiker" -Repository "Win10Automation" | Install-Module -Name "PSHitchhiker" -Scope "CurrentUser"

#(C:\Data\App\LocalNuGetFeed\Packages\PSHitchhiker.1.0.25.nupkg)
Install-Module -Name "PSHitchhiker" -Repository "Win10Automation" -Scope CurrentUser
Install-Module PSHitchhiker -Repository LocalNuGetFeed

Uninstall-Module -Name "PSHitchhiker"




Nuget Server:
PS C:\ProgramData\Microsoft\Windows\PowerShell\PowerShellGet> .\nuget.exe install PSHitchhiker -Source http://localhost:8082/nuget -OutputDirectory C:\data\Modules

find-package -name PSHitchhiker -allversion -Source http://localhost:8082/nuget

Install-Package -name PSHitchhiker -Source http://localhost:8082/nuget

Get-Package -name PSHitchhiker



