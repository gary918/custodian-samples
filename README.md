# Introduction  
- Cloud Custodian Overview: https://cloudcustodian.io/
- Cloud Custodian Gtihub Repository: https://github.com/cloud-custodian/cloud-custodian
- Cloud Custodian Customer Example: https://github.com/logachev/custodian-samples

# Getting Started
## Authentication
### On Windows 10
1. Run set for checking the existing environment variables
```
set
```
2. Login to Azure to get the following environment variables
```
az login
az ad sp create-for-rbac --name gary -o table
```
Please note that AZURE_CLIENT_ID = AppId
3. Set the environment variables
```
set AZURE_TENANT_ID=abcdef89-3dea-4af8
set AZURE_SUBSCRIPTION_ID=abcd4ec8-93f4-9e9d
set AZURE_CLIENT_ID=abcd0df3ee0-0c0da
set AZURE_CLIENT_SECRET=abcd4041-9c8f-f40
```


# Build and Test
TODO: Describe and show how to build your code and run the tests. 

# Contribute
TODO: Explain how other users and developers can contribute to make your code better. 

If you want to learn more about creating good readme files then refer the following [guidelines](https://docs.microsoft.com/en-us/azure/devops/repos/git/create-a-readme?view=azure-devops). You can also seek inspiration from the below readme files:
- [ASP.NET Core](https://github.com/aspnet/Home)
- [Visual Studio Code](https://github.com/Microsoft/vscode)
- [Chakra Core](https://github.com/Microsoft/ChakraCore)