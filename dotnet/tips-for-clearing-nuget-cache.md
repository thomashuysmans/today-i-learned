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

Go to Tools --> Nuget Package Manager --> Package Manager Settings

![Screenshot 2022-12-02 at 08.17.11](/Users/thomas/Desktop/Screenshot 2022-12-02 at 08.17.11.png)

