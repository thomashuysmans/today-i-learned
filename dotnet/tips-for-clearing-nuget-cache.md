## Tips for clearing Nuget cache

Lately I had some problems with Nuget caching so following TIL is about how to clear your Nuget cache.

### Tip 1: Using the command line 

If you want to know all the local cache folders, then execute following:

```
dotnet nuget locals all --list
```

When you want to clear the cache:

```powershell
dotnet nuget locals all --clear
```

### Tip 2  In Visual Studio:



### Tip 3 Deleteing folders in Windows Explorer 

You find the cache folders on following locations:

%LocalAppData%\Nuget\Cache
%UserProfile% \ .nuget\packages

When you delete the above folders, you are clearing the cache

