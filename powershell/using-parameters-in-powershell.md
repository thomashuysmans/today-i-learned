## Using Parameters in PowerShell

Today, I needed to use PowerShell and I am not familiar with PowerShell so a quick write up about how to use parameters in PowerShell



*Creating a variable can be done the following way*:

```powershell
$keyVaultName = "some-name"
```

*When you want to use a parameter as an input value*:

```powershell
$paramKeyVaultName=$args[0]
write-host $paramKeyVaultName
```

$args is an array where you can access multiple values from the command line.

*When you want to use Named Parameters*:

```powershell
param ($paramKeyVaultName)
write-host $paramKeyVaultName
```

You can run it by 

```
.\name-of-your-script.ps -paramKeyVaultName
```

When you want to use multiple Named Parameters:

```powershell
param ($param1, $param2)
```

