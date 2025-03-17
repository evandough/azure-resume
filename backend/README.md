# Your backend lives here

## Building The BackEnd - Set Up CosmosDB, Set Up Azure Function, & Test
- `api/` (Contains the .NET API deployed on Azure Functions)
    - `GetVisitorCounter.cs` (Conatains the visitor counter code)
1. Create Azure Cosmos DB in the Azure portal
    - For the naming convention of resources, I referenced [Microsoft's documentation](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-best-practices/resource-naming) 
2. Create the database & container inside of Azure Cosmos DB
3. Create the Azure Function inside of VSCode  
    - I ran into 2 issues that needed to be resolved: 
        - 1. Needed to install the Azure Function extension in VSCode
        - 2. To create an Azure Function, I had to install .NET Core SDK 3.0.1
        - 3. Needed to install [Nuget package for Cosmos DB Extension v3.0.10](https://www.nuget.org/packages/Microsoft.Azure.WebJobs.Extensions.CosmosDB) in VSCode
    - Created Azure Function using .NET 6.0 LTS
        - Ran into an issue running ```func host start ```, so I had to install Chocolately and run ```choco install azure-functions-core-tools``` in PowerShell as Administrator
        - Ran into another error whilst running ```func host start ```, from Shell I had to run `dotnet nuget add source --name nuget.org https://api.nuget.org/v3/index.json` - WHAT THIS DOES: adds a NuGet package source to ensur .NET projects can download packages from NuGet.org it it's not already configured
         - Ran ```func host start ``` in VSCode and BOOM - we can access the http get,post