# Octocat
sample nuget package repository

[Github Nuget](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-nuget-registry)

## Configuration Step

### 1. Add Nuget cofiguration to NuGet.Config

 #### 1.1 > dotnet nuget add source --username USERNAME --password TOKEN --store-password-in-clear-text --name github "https://nuget.pkg.github.com/nuttapornk/index.json"

```xml
.n
<?xml version="1.0" encoding="utf-8"?>
<configuration>
	<packageSources>
		<clear />
		<add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
		<add key="github" value="https://nuget.pkg.github.com/nuttapornk/index.json" />
	</packageSources>
	<packageSourceCredentials>
		<github>
			<add key="Username" value="USERNAME" />
			<add key="ClearTextPassword" value="PAIN TEXT TOKEN" />
		</github>
	</packageSourceCredentials>
</configuration>
```

### 2. Generate [GITHUB-TOKEN](https://github.com/settings/tokens)
  #### 2.1 Gantt token permission
```permission
    write:packages Upload packages to GitHub Package Registry
    read:packages Download packages from GitHub Package Registry
    (optional)delete:packages Delete packages from GitHub Package Registry
```
### 3. Use GITHUB_TOKEN to authenticate to github


## TEST (Optional)

1. Pull Code from GITHUB REPOSITORY [Octocat](https://github.com/nuttapornk/Octocat.git)
2. Open OctocatApp.csproj identify parameter is exist
```xml
    <PackageId>OctocatApp</PackageId>
    <Authors>Nuttaporn Kunsin</Authors>
    <Company></Company>
    <PackageDescription>This package adds an Octocat!</PackageDescription>
    <RepositoryUrl>https://github.com/nuttapornk/Octocat</RepositoryUrl>
```
3. Change <Version> and pack release 
```cmd
dotnet pack --configuration Release
```
4. Test push to package repository
```cmd
dotnet nuget push "bin/Release/OctocatApp.1.0.0.nupkg" --source "github"
```