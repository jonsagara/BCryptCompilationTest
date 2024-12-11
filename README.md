# C# Compilation Broken in Visual Studio 2022 17.13.0 Preview 2.0

After upgrading to the latest Visual Studio 2022 Preview, I could no longer compile my solution.

This project is a bare bones reproduction of the issue.


## Steps to Reproduce

First and foremost, clone this repository.

### Working compilation in Visual Studio 2022

1. Open `BCryptCompilationTest.sln` in Visual Studio 2022
2. `Build` -> `Rebuild Solution`

#### Expected results

The solution compiles successfully.

#### Actual results

Solution compiles successfully:

```
Rebuild started at 3:04 PM...
1>------ Rebuild All started: Project: BCryptCompilationTest, Configuration: Debug Any CPU ------
Restored C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\BCryptCompilationTest.csproj (in 29 ms).
1>BCryptCompilationTest -> C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\bin\Debug\net9.0\BCryptCompilationTest.dll
========== Rebuild All: 1 succeeded, 0 failed, 0 skipped ==========
========== Rebuild completed at 3:04 PM and took 07.553 seconds ==========
```



### Broken compilation in Visual Studio 2022 Preview

1. Open `BCryptCompilationTest.sln` in Visual Studio 2022 Preview
2. `Build` -> `Rebuild Solution`

#### Expected results

The solution compiles successfully.

#### Actual results

Solution fails to compile:

```
Rebuild started at 2:54 PM...
1>------ Rebuild All started: Project: BCryptCompilationTest, Configuration: Debug Any CPU ------
Restored C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\BCryptCompilationTest.csproj (in 2 ms).
1>C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\BCrypt.cs(391,28,391,29): error CS1002: ; expected
1>C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\BCrypt.cs(391,32,391,33): error CS1002: ; expected
1>C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\BCrypt.cs(391,36,391,37): error CS1003: Syntax error, ',' expected
1>C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\BCrypt.cs(391,53,391,54): error CS1003: Syntax error, ',' expected
1>C:\Dev\SANDBOX\BCryptCompilationTest\src\BCryptCompilationTest\BCrypt.cs(391,54,391,55): error CS1525: Invalid expression term ')'
1>Done building project "BCryptCompilationTest.csproj" -- FAILED.
========== Rebuild All: 0 succeeded, 1 failed, 0 skipped ==========
========== Rebuild completed at 2:55 PM and took 03.064 seconds ==========
```

## Environment

- Visual Studio 2022 17.12.3
- Visual Studio 2022 17.13.0 Preview 2.0
- .NET SDK 9.0.101
- Windows 11 Version 24H2 (OS Build 26100.2605)

## JetBrains Rider

The solution also compiles successfully in JetBrains Rider 2024.3.