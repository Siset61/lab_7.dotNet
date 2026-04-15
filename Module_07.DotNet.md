# Module 07 – Application Modernization with GitHub Copilot - Hands-On Lab

## Overview

In this lab, you will use GitHub Copilot's application modernization capabilities to upgrade a legacy .NET 6.0 Claims API to modern .NET 9.0 standards. You'll leverage Agent Mode for automated upgrades, learn to identify and fix CVE vulnerabilities, refactor legacy code patterns, and validate modernization changes.

**What You'll Learn:**
- Assess legacy codebases for modernization opportunities using Copilot
- Use Agent Mode to plan and execute framework upgrades
- Identify and remediate CVE vulnerabilities in dependencies
- Refactor legacy code patterns to modern C# 12+ idioms
- Validate code behavior consistency after modernization
- Leverage GitHub Copilot App Modernization extension features

**What You'll Build:**
- Upgraded Claims API from .NET 6.0 to .NET 9.0
- Modernized code using records, primary constructors, and collection expressions
- Remediated security vulnerabilities (CVEs)
- Replaced Newtonsoft.Json with System.Text.Json
- Validated and tested modernized codebase

## Lab Learning Path

1. **Introductory (30 min)**: Assess the legacy codebase, identify modernization opportunities, and understand the current CVE status
2. **Intermediate (30 min)**: Use Agent Mode to upgrade the framework and remediate CVEs, refactor legacy patterns to modern C# idioms
3. **Advanced (30 min)**: Perform consistency validation, handle complex refactoring scenarios, and complete the modernization with automated testing

## Prerequisites

> **📋 See [Module_07.Requirements.DotNet.md](Module_07.Requirements.DotNet.md) for detailed setup instructions.**

## Repository Structure

The repository contains **exercise tags** that allow you to start from any exercise or catch up if you fall behind.

### Available Tags

| Tag | Description | Checkpoint |
|-----|-------------|------------|
| `Exercise_1` | After Exercise 1 | Legacy codebase assessed |
| `Exercise_2` | After Exercise 2 | Framework upgraded to .NET 9.0 |
| `Exercise_3` | After Exercise 3 | CVEs remediated |
| `Exercise_4` | After Exercise 4 | Records and primary constructors |
| `Exercise_5` | After Exercise 5 | Collection expressions applied |
| `Exercise_6` | After Exercise 6 | System.Text.Json migration |
| `Exercise_7` | After Exercise 7 | Complex refactoring complete |
| `Exercise_8` | After Exercise 8 | Modernization validated |

### Starting from a Specific Exercise

To start from a specific exercise, checkout the **previous** exercise tag:

```bash
# Example: To start Exercise 4, checkout Exercise_3 tag
git checkout Exercise_3

# To start Exercise 1, use the initial state
git checkout Initial
```

### Quick Reference

| To Start | Checkout Tag |
|----------|--------------|
| Exercise 1 | `Initial` |
| Exercise 2 | `Exercise_1` |
| Exercise 3 | `Exercise_2` |
| Exercise 4 | `Exercise_3` |
| Exercise 5 | `Exercise_4` |
| Exercise 6 | `Exercise_5` |
| Exercise 7 | `Exercise_6` |
| Exercise 8 | `Exercise_7` |

---

# Introductory Level

## Exercise 1: Assess the Legacy Codebase

### 📋 Prerequisites

- VS Code with GitHub Copilot extension enabled
- **Project opened in DevContainer**
- Claims API project loaded in VS Code

### 🎯 Objective

Use Copilot to analyze the legacy .NET 6.0 codebase and identify all modernization opportunities including outdated patterns, deprecated APIs, and security vulnerabilities.

### 🧠 Description

The Claims API was built with .NET 6.0 and contains several legacy patterns that can benefit from modernization. You'll use Copilot's Ask mode and `@workspace` participant to perform a comprehensive assessment before planning the upgrade.

**Key Copilot Features Used:**
- **Ask Mode**: Query the codebase for legacy patterns
- **@workspace**: Analyze project-wide modernization needs
- **Smart Actions**: Explain legacy code before refactoring

### 🪜 Steps

#### Step 1: Build the Project and Observe Warnings

Open the terminal and build the project:
```bash
cd src/ClaimsApi
dotnet build
```

*(See prompt 1.1 for reference)*

**Expected Copilot Behavior:**
> The build should succeed with several NU1902/NU1903 warnings about known vulnerabilities in packages like Microsoft.Extensions.Caching.Memory, System.Text.Json, and Swashbuckle.AspNetCore.SwaggerUI.

**If Copilot doesn't respond as expected:**
> Ensure the nuget.config file exists in the project root and contains only nuget.org as a package source.

#### Step 2: Assess Framework Version and Dependencies

Open Copilot Chat in **Ask** mode and query:
```text
@workspace Analyze the current .NET version and all NuGet packages in this project. List which packages have known CVEs and what the current vs recommended versions are.
```

*(See prompt 1.2 for reference)*

Review Copilot's analysis of:
- Current .NET target framework (net6.0)
- Package versions with known vulnerabilities
- Recommended upgrade paths

#### Step 3: Identify Legacy Code Patterns

Continue in Ask mode:
```text
@workspace Find all legacy C# patterns in this codebase that could be modernized for .NET 9.0. Look for: classes that should be records, verbose constructors that could use primary constructors, string concatenation instead of interpolation, verbose null checks, and use of Newtonsoft.Json.
```

*(See prompt 1.3 for reference)*

**Expected Response:**
> Copilot should identify patterns in ClaimService.cs, UserService.cs, AuthController.cs, and DTOs that use legacy patterns.

#### Step 4: Generate Assessment Report

Use Agent Mode to create an assessment document:
```text
Create a MODERNIZATION_ASSESSMENT.md file that summarizes:
1. Current .NET version and target upgrade version
2. All packages with CVEs and their recommended versions
3. Legacy code patterns found and their modern alternatives
4. Estimated complexity of the modernization
```

*(See prompt 1.4 for reference)*

### ✅ Success Criteria

- [ ] Build completes with CVE warnings visible
- [ ] Copilot identifies all 5 vulnerable packages
- [ ] Legacy patterns identified in at least 4 files
- [ ] MODERNIZATION_ASSESSMENT.md created with complete analysis

### 🔍 Verification Steps

```bash
# Verify assessment file was created
cat docs/MODERNIZATION_ASSESSMENT.md

# Confirm build warnings about CVEs
dotnet build 2>&1 | grep -E "NU190[23]"
```

### 🔗 Connection to Next Exercise

With the assessment complete, you'll use Agent Mode to automatically upgrade the .NET framework and remediate the CVE vulnerabilities identified.

### ⏱️ Estimated Time

15 minutes

---

## Exercise 2: Upgrade Framework with Agent Mode

### 📋 Prerequisites

- Completion of Exercise 1
- MODERNIZATION_ASSESSMENT.md created
- Understanding of current CVE status

### 🎯 Objective

Use GitHub Copilot Agent Mode to upgrade the project from .NET 6.0 to .NET 9.0 and update all packages to their latest secure versions.

### 🧠 Description

Agent Mode can autonomously plan and execute multi-file framework upgrades. You'll guide the agent to upgrade the target framework, update all NuGet packages, and resolve any compatibility issues that arise.

**Key Copilot Features Used:**
- **Agent Mode**: Autonomous multi-file operations
- **Plan Mode**: Review upgrade plan before execution
- **Build-Fix Loop**: Automatic error detection and resolution

### 🪜 Steps

#### Step 1: Plan the Framework Upgrade

Open Copilot Chat and switch to **Agent** mode. Enter:
```text
Upgrade this project from .NET 6.0 to .NET 9.0. Update all NuGet packages to their latest stable versions. Show me the plan before executing.
```

*(See prompt 2.1 for reference)*

**Expected Copilot Behavior:**
> Agent should present a plan including:
> 1. Update TargetFramework in .csproj to net9.0
> 2. Update all package versions
> 3. Run dotnet restore
> 4. Build and verify

Review the plan and approve execution.

#### Step 2: Execute the Upgrade

After approving the plan, Agent Mode will:
1. Modify `ClaimsApi.csproj` to target `net9.0`
2. Update all package references to latest versions
3. Run `dotnet restore` and `dotnet build`
4. Report any compilation errors

*(See prompt 2.2 for reference)*

**If build errors occur:**
> Agent Mode should automatically attempt to fix them. If it needs guidance, provide context about the error.

#### Step 3: Verify CVE Remediation

After the upgrade completes, rebuild and verify:
```bash
dotnet build 2>&1 | grep -E "NU190[23]" || echo "No CVE warnings - all vulnerabilities remediated!"
```

*(See prompt 2.3 for reference)*

**Expected Result:**
> Build should complete without any NU1902/NU1903 warnings.

#### Step 4: Run Tests to Validate Upgrade

```bash
cd ../../tests/ClaimsApi.Tests
dotnet test
```

*(See prompt 2.4 for reference)*

If tests fail, use Agent Mode to fix:
```text
The tests are failing after the .NET 9.0 upgrade. Analyze the test failures and fix any compatibility issues.
```

### ✅ Success Criteria

- [ ] Project targets .NET 9.0 (`<TargetFramework>net9.0</TargetFramework>`)
- [ ] All packages updated to latest versions
- [ ] Build completes without CVE warnings
- [ ] All existing tests pass

### 🔍 Verification Steps

```bash
# Verify framework version
grep TargetFramework src/ClaimsApi/ClaimsApi.csproj

# Verify no CVE warnings
dotnet build src/ClaimsApi/ClaimsApi.csproj 2>&1 | grep -c "NU190" || echo "0 CVE warnings"

# Run tests
dotnet test tests/ClaimsApi.Tests/ClaimsApi.Tests.csproj
```

### 🔗 Connection to Next Exercise

With the framework upgraded and CVEs remediated, you'll refactor the legacy code patterns to use modern C# 12 features.

### ⏱️ Estimated Time

15 minutes

---

# Intermediate Level

## Exercise 3: Refactor DTOs to Records

### 📋 Prerequisites

- Completion of Exercise 2
- Project building successfully on .NET 9.0
- Understanding of C# records

### 🎯 Objective

Modernize the DTO classes to use C# records, which provide immutability, value equality, and concise syntax.

### 🧠 Description

The current DTOs are implemented as verbose classes with explicit constructors and mutable properties. You'll use Copilot to convert them to records, reducing boilerplate and improving code quality.

**Modern Pattern - Records:**
```csharp
// Before: Legacy class
public class ClaimReadDto
{
    public int Id { get; set; }
    public string Status { get; set; } = string.Empty;
    public ClaimReadDto(int Id, string Status) { ... }
}

// After: Modern record
public record ClaimReadDto(int Id, string Status);
```

### 🪜 Steps

#### Step 1: Analyze Current DTO Structure

Open `src/ClaimsApi/DTOs/ClaimReadDto.cs` and use Smart Action "Explain" to understand the current structure.

*(See prompt 3.1 for reference)*

#### Step 2: Convert ClaimReadDto to Record

Select the entire file content and use Edit mode:
```text
Convert this class to a C# record. Maintain the same property names and types. Remove the manual constructors as records provide them automatically.
```

*(See prompt 3.2 for reference)*

**Expected Result:**
```csharp
namespace ClaimsApi.DTOs;

public record ClaimReadDto(
    int Id,
    string Status,
    string PolicyNumber,
    DateTime IncidentDate,
    string Description,
    decimal Amount
);
```

#### Step 3: Convert All DTOs

Use Agent Mode for batch conversion:
```text
Convert all DTO classes in the DTOs folder to records. Each should use positional parameters. Ensure the ClaimService.cs MapToReadDto method is updated to work with the new record syntax.
```

*(See prompt 3.3 for reference)*

#### Step 4: Verify and Test

```bash
dotnet build src/ClaimsApi/ClaimsApi.csproj
dotnet test tests/ClaimsApi.Tests/ClaimsApi.Tests.csproj
```

### ✅ Success Criteria

- [ ] All 6 DTOs converted to records
- [ ] No compilation errors
- [ ] All tests pass
- [ ] Code reduced by ~50 lines

### 🔍 Verification Steps

```bash
# Check all DTOs are records
grep -l "public record" src/ClaimsApi/DTOs/*.cs | wc -l  # Should be 6
```

### ⏱️ Estimated Time

10 minutes

---

## Exercise 4: Modernize Services with Primary Constructors

### 📋 Prerequisites

- Completion of Exercise 3
- DTOs converted to records
- Understanding of C# 12 primary constructors

### 🎯 Objective

Refactor service classes to use C# 12 primary constructors, eliminating boilerplate field assignments.

### 🧠 Description

The current services use traditional constructor injection with explicit field declarations and assignments. C# 12 primary constructors reduce this boilerplate significantly.

**Modern Pattern:**
```csharp
// Before: Legacy constructor
public class ClaimService : IClaimService
{
    private readonly ClaimsDbContext _context;
    private readonly ILogger<ClaimService> _logger;
    
    public ClaimService(ClaimsDbContext context, ILogger<ClaimService> logger)
    {
        _context = context;
        _logger = logger;
    }
}

// After: Primary constructor
public class ClaimService(ClaimsDbContext context, ILogger<ClaimService> logger) : IClaimService
{
    // context and logger are directly accessible
}
```

### 🪜 Steps

#### Step 1: Convert ClaimService

Open `src/ClaimsApi/Services/ClaimService.cs` and use Edit mode:
```text
Convert this class to use a C# 12 primary constructor. Remove the field declarations and constructor body. Replace _context with context and _logger with logger throughout the class.
```

*(See prompt 4.1 for reference)*

#### Step 2: Convert UserService

Apply the same transformation to `UserService.cs`:
```text
Convert UserService to use a primary constructor. Also modernize the null check to use ArgumentNullException.ThrowIfNull().
```

*(See prompt 4.2 for reference)*

#### Step 3: Convert AuthController

Modernize `AuthController.cs`:
```text
Convert AuthController to use a primary constructor. Also: remove the generic exception handling, use structured logging with interpolation, and simplify the null checks.
```

*(See prompt 4.3 for reference)*

#### Step 4: Batch Convert Remaining Files

Use Agent Mode:
```text
Find all remaining classes that use traditional constructor injection and convert them to primary constructors. This includes controllers and services.
```

*(See prompt 4.4 for reference)*

### ✅ Success Criteria

- [ ] ClaimService, UserService, AttachmentService use primary constructors
- [ ] All controllers use primary constructors
- [ ] Build succeeds without warnings
- [ ] Tests pass

### 🔍 Verification Steps

```bash
# Verify primary constructors are used (no explicit constructor bodies)
grep -r "public ClaimService(" src/ClaimsApi/Services/
# Should show: public class ClaimService(...) : IClaimService
```

### ⏱️ Estimated Time

10 minutes

---

## Exercise 5: Replace Newtonsoft.Json with System.Text.Json

### 📋 Prerequisites

- Completion of Exercise 4
- Services using primary constructors
- Understanding of JSON serialization

### 🎯 Objective

Remove the Newtonsoft.Json dependency and replace all usages with the built-in System.Text.Json, which is faster and more secure.

### 🧠 Description

The legacy code uses Newtonsoft.Json for serialization. Modern .NET applications should use System.Text.Json for better performance, reduced dependencies, and native integration with ASP.NET Core.

### 🪜 Steps

#### Step 1: Find Newtonsoft.Json Usages

```text
@workspace Find all usages of Newtonsoft.Json in this project including the package reference and any JsonConvert calls.
```

*(See prompt 5.1 for reference)*

#### Step 2: Replace JsonConvert Calls

Open `ClaimService.cs` and use Edit mode to replace:
```text
Replace the Newtonsoft.Json serialization with System.Text.Json. Use JsonSerializer.Serialize instead of JsonConvert.SerializeObject. Remove the using Newtonsoft.Json statement.
```

*(See prompt 5.2 for reference)*

**Modern Pattern:**
```csharp
// Before
using Newtonsoft.Json;
var json = JsonConvert.SerializeObject(obj);

// After
using System.Text.Json;
var json = JsonSerializer.Serialize(obj);
```

#### Step 3: Remove Package Reference

Use Agent Mode:
```text
Remove the Newtonsoft.Json package reference from the .csproj file and ensure there are no remaining usages in the codebase.
```

*(See prompt 5.3 for reference)*

#### Step 4: Verify and Test

```bash
dotnet build
dotnet test
```

### ✅ Success Criteria

- [ ] Newtonsoft.Json package removed from .csproj
- [ ] No `using Newtonsoft.Json` statements remain
- [ ] All JSON operations use System.Text.Json
- [ ] Tests pass

### 🔍 Verification Steps

```bash
# Verify Newtonsoft.Json is removed
grep -r "Newtonsoft" src/ClaimsApi/ && echo "FAIL: Still using Newtonsoft" || echo "PASS: Newtonsoft removed"
```

### ⏱️ Estimated Time

10 minutes

---

# Advanced Level

## Exercise 6: Complete Modernization and Validation

### 📋 Prerequisites

- Completion of all previous exercises
- Project building on .NET 9.0
- DTOs as records, services with primary constructors

### 🎯 Objective

Complete the remaining modernization tasks, validate code behavior consistency, and ensure the modernized codebase is production-ready.

### 🧠 Description

This exercise covers the final modernization touches: string interpolation, collection expressions, pattern matching, and comprehensive validation of the changes.

### 🪜 Steps

#### Step 1: Modernize String Handling

Use Agent Mode to fix all legacy string patterns:
```text
Find and fix all string concatenation in this project. Replace with string interpolation. Also update any verbose null/empty string checks to use string.IsNullOrEmpty() or pattern matching.
```

*(See prompt 6.1 for reference)*

#### Step 2: Add Modern Logging

Ensure all logging uses structured logging:
```text
Review all _logger calls and ensure they use structured logging with proper placeholders {PropertyName} instead of string concatenation.
```

*(See prompt 6.2 for reference)*

#### Step 3: Validate Code Behavior

Use Copilot to verify the modernization didn't change behavior:
```text
@workspace Compare the before and after of our modernization. List any changes that could affect runtime behavior (not just syntax changes).
```

*(See prompt 6.3 for reference)*

#### Step 4: Run Comprehensive Tests

```bash
# Build in Release mode
dotnet build -c Release

# Run all tests with verbose output
dotnet test --verbosity normal

# Start the API and test manually
dotnet run --project src/ClaimsApi/ClaimsApi.csproj &
curl -v http://localhost:5000/health
```

*(See prompt 6.4 for reference)*

#### Step 5: Generate Modernization Summary

Use Agent Mode to document the changes:
```text
Create a MODERNIZATION_COMPLETE.md file that summarizes all changes made during modernization:
1. Framework upgrade (.NET 6.0 → 9.0)
2. CVEs remediated (list each package)
3. Code patterns modernized (records, primary constructors, etc.)
4. Lines of code reduced
5. Performance improvements expected
```

*(See prompt 6.5 for reference)*

### ✅ Success Criteria

- [ ] No string concatenation remains in production code
- [ ] All logging uses structured format
- [ ] Build succeeds in Release mode
- [ ] All tests pass
- [ ] API responds correctly to health check
- [ ] MODERNIZATION_COMPLETE.md created

### 🔍 Verification Steps

```bash
# Final verification
dotnet build -c Release
dotnet test
grep -r "\" + " src/ClaimsApi/ | grep -v ".cs:" || echo "No string concatenation found"
```

### ⏱️ Estimated Time

15 minutes

---

## Lab Completion Summary

Congratulations! You've successfully modernized a legacy .NET 6.0 application to .NET 9.0 using GitHub Copilot.

### What You Accomplished

| Area | Before | After |
|------|--------|-------|
| Framework | .NET 6.0 | .NET 9.0 |
| CVEs | 5 vulnerabilities | 0 vulnerabilities |
| DTOs | Verbose classes | Concise records |
| Constructors | Traditional | Primary constructors |
| JSON | Newtonsoft.Json | System.Text.Json |
| Strings | Concatenation | Interpolation |
| Logging | Inconsistent | Structured |

### Key Takeaways

1. **Agent Mode** can autonomously plan and execute complex framework upgrades
2. **CVE scanning** is integrated into the build process
3. **Modern C# features** (records, primary constructors) reduce boilerplate significantly
4. **Copilot understands context** and can suggest appropriate modernization patterns
5. **Validation is critical** - always test after modernization

### Next Steps

- Explore Java modernization with OpenRewrite integration
- Apply these patterns to larger legacy codebases
- Set up automated CVE scanning in CI/CD pipelines
