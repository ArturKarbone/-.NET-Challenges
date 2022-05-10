# IHostEnvironment Extensions

## Project statement

IHostEnvironment is an interface which looks like:

```csharp

public interface IHostEnvironment
{
    string ApplicationName { get; set; }
    IFileProvider ContentRootFileProvider { get; set; }
    string ContentRootPath { get; set; }
    string EnvironmentName { get; set; }
}
```

Extend it with the methods which:
- Compare the current host environment name against the specified value.
- Check if the current host environment name is Development/Staging/Production/UAT/etc.


So the client code could look something like:

```csharp
private bool AllowSwagger(IWebHostEnvironment env) =>
            env.IsDevelopment() || env.IsStaging();
```


Here is a non-working implementation for a quick start:

```csharp
    public static class HostEnvironmentEnvExtensions
    {
        public static bool IsEnvironment(this IHostEnvironment hostEnvironment, string environmentName) => throw new NotImplementedException();
        public static bool IsDevelopment(this IHostEnvironment hostEnvironment) => throw new NotImplementedException();
        public static bool IsProduction(this IHostEnvironment hostEnvironment) => throw new NotImplementedException();
        public static bool IsStaging(this IHostEnvironment hostEnvironment) => throw new NotImplementedException();
        public static bool IsUAT(this IHostEnvironment hostEnvironment) => throw new NotImplementedException();
    }
```

### Challenge #1
Implement **IsEnvironment** extension method
### Challenge #2
Implement **IsDevelopment/IsProduction/etc.** extension methods
### Challenge #3
Cover extension methods with unit tests
### Challenge# 4
Create a nuget package
### Challenge# 5
push the package to the nuget feed of your choice
### Challenge #6
Create a random .NET Core API project. Find a usage of **env.IsDevelopment()**. Imagine you need to obtain a source code of the implementation. How would you achieve that? Share your thought process.