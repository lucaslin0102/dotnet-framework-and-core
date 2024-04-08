# dotnet-framework-and-core

[SonarScanner for .NET](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner-for-dotnet/)

> This is to demonstrate that you can analysis both .NET Framework and .NET Core targeted projects with all scanner versions for .NET Framework, .NET Core and .NET Core global tool

- NET Standard Project (Targeting .NET Standard 2.1)
- NET Core Project (Targeting .NET Core 3.1)
- NET Framework Project (Targeting .NET Framework 4.7.2)

**"Classic" .NET framework invocation**
```
[PATH]\sonar-scanner-6.2.0.85879-net-framework\SonarScanner.MSBuild.exe begin /k:"s4net-framework-analysis" /d:sonar.token="<token>"
```
```
"C:\Program Files\Microsoft Visual Studio\2022\Community\MSBuild\Current\Bin\MSBuild.exe" [path]\dotnet-framework-and-core\dotnet-framework-and-core.sln /t:Rebuild
```
```
[PATH]\sonar-scanner-6.2.0.85879-net-framework\SonarScanner.MSBuild.exe end /d:sonar.token="<token>"
```

**.NET Core DLL invocation**
```
dotnet "[path]\sonar-scanner-6.2.0.85879-net\SonarScanner.MSBuild.dll" begin /k:"s4net-dll-analysis" /d:sonar.token="<token>"
dotnet build [path]\dotnet-framework-and-core\dotnet-framework-and-core.sln --no-incremental
dotnet "[path]\sonar-scanner-6.2.0.85879-net\SonarScanner.MSBuild.dll" end /d:sonar.token="<token>" 
```

**.NET Core global tool invocation**
```
dotnet sonarscanner begin /k:"s4net-globaltool-analysis" /d:sonar.token="<token>"
```

```
dotnet build [path]\dotnet-framework-and-core\dotnet-framework-and-core.sln --no-incremental
```

```
dotnet sonarscanner end /d:sonar.token="<token>"
```