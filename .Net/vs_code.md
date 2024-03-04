### create a new solution
dotnet new sln -n MyApplication

### create a simple console application
dotnet new console -o HelloWorld

### run the application
dotnet run

### in the root solution folder create a unit test folder
dotnet new nunit -n MyConsoleApp.Tests

### Then, add it to the solution with 
dotnet sln add MyConsoleApp.Tests

### Add a Reference to Your Console App
dotnet add MyConsoleApp.Tests reference MyConsoleApp

### run tests
### In the terminal, ensure you are in the HelloWorld.Tests directory and run:
dotnet test

###  list all configured package sources
dotnet nuget list source

### To add NuGet.org as a source if it's missing, use:
dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org

## add reference for tests
dotnet add reference ../HelloWorld/HelloWorld.csproj




