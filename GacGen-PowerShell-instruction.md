## GacGen and PowerShell Instructions

This is a configuration that just works for me.

<br/>

Because of the default security policy, users cannot run \*.ps1 scripts directly. You should execute some commands to modify the configuration.

### On PS terminal

```PowerShell
Set-ExecutionPolicy Bypass -Scope Process
```

<br/>

### For shortcut of PS

The `Target` of .lnk file is:

```CMD
powershell.exe -NoExit -Command & {Set-ExecutionPolicy Bypass -Scope Process ; cd X:\GacLib_Tools ; explorer X:\GacLib_Tools}
```

```X:\GacLib_Tools```: The folder where GacGen's files exist.

* Double click the shortcut
* Drag and drop ```GacGen.ps1``` to PS Terminal
* Type a space
* Drag and drop your .xml file to PS Terminal
* Go!

<br/>

### Ref

* [about_Execution_Policies | Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies)
* [15 Ways to Bypass the PowerShell Execution Policy](https://blog.netspi.com/15-ways-to-bypass-the-powershell-execution-policy/)
* [Simple way to temporarily bypass PowerShell execution policy &#8211; Ken Brumfield&#039;s Blog](https://blogs.technet.microsoft.com/ken_brumfield/2014/01/19/simple-way-to-temporarily-bypass-powershell-execution-policy/)
