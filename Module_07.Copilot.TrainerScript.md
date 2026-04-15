# Module 07 - Application Modernization with GitHub Copilot (2h) - Trainer Script (Light, Simple English)

This is a read-aloud script for the transitions and the first/last minutes.

You will jump to `Module_07/Module_07.DotNet.md` for the actual step-by-step instructions and prompts.

## Timing (Suggested - ~2 hours)

- 00:00-00:05 Courtesy wait
- 00:05-00:15 Intro + how we will work
- 00:15-00:25 Environment check
- 00:25-00:40 Exercise 1 (15 min)
- 00:40-00:55 Exercise 2 (15 min)
- 00:55-01:05 Exercise 3 (10 min)
- 01:05-01:15 Break (10 min if on time, otherwise 5 min)
- 01:15-01:25 Exercise 4 (10 min)
- 01:25-01:35 Exercise 5 (10 min)
- 01:35-01:50 Exercise 6 (15 min)
- 01:50-02:00 Wrap-up + survey + goodbye (10 min)

## 00:00-00:05 Courtesy Wait

Say:

"Hi everyone, we will start in about five minutes. Please open VS Code and check that GitHub Copilot Chat works."

**IMPORTANT: Start recording now.**

Say:

"Quick reminder: this session is being recorded."

### After 5 minutes, say:

"Good afternoon everyone. Thank you for joining today's lab."

"Let's get started."

## 00:05-00:15 Short Intro (What We Will Do)

Say:

"Today we modernize a .NET 6 Claims API to .NET 9 using GitHub Copilot."

"By the end of this lab, you will have: upgraded the framework, fixed security vulnerabilities, and modernized the code with new C# features."

"I will do each exercise first, then you repeat it. If you are behind, finish your step and then join us in the next exercise."

"I will paste the prompts in the meeting chat so you can copy them."

"Please stay muted. Ask questions in the chat. "

"We take a short break in the middle."

Two quick tips:

"Tip 1: Context. Copilot needs context."

"- Select code and ask questions."

"- Use `@workspace` for whole project answers."

"- Attach files or drag files into the chat."

"Tip 2: Model."

"- Use Auto for normal work."

"- Use a stronger model for Agent Mode or complex steps."

Quick glossary of terms we will use:

"CVE: a known security issue in a package. Example: a vulnerable version of System.Text.Json."

"Record: a short class for data objects. Instead of writing many lines, you write one line."

"Primary constructor: a shorter way to write constructor and fields. Removes boilerplate code."

While people open the lab (optional filler):

"Please keep the lab script open on the side. It has the exact prompts."

"I will show each prompt on screen and paste it into chat."

"If you are unsure, wait for my screen before you run the prompt."

"If Copilot is slow, please wait. It is reading the project."

"If the answer is too long, ask: 'Give me a short summary in 5 bullets.'"

## 00:15-00:25 Environment Check

Say:

"Before Exercise 1, we need to check your environment is ready."

"Step 1: Check Copilot Chat works."

"- Open the Copilot Chat panel. You should see an icon on the left sidebar."

"- Type a simple question like: 'What is this project about?'"

"- If you see an answer, Copilot works correctly."

"Step 2: Open the whole project folder, not only one file."

"Step 3: If using Dev Container, make sure you are inside it. The terminal should show the container path."

Common issues and quick fixes:

"- If you see 'Sign in required', click and authenticate with your GitHub account."

"- If you see 'No subscription' or 'Not authorized', contact your admin or check your license."

"- If Copilot Chat does not appear, restart VS Code."

If someone is blocked and you are spending too long troubleshooting, say:

"If troubleshooting takes too long (more than 15-20 minutes), please disconnect and register for another session later."

You can copy/paste this text in the chat:

```text
If you experience issues with requirements and setup of lab environment, please consider to register again in another date and join our Support Calls available every Monday and Friday. Please write an email to TechnicalExcellenceSchools@generali.com and inform us about this.
```

## Exercise Transitions

Use this pattern for every exercise:

- Say what the exercise is about (1-2 sentences)
- Say: "And now we'll start Exercise X."
- Jump to `Module_07/Module_07.DotNet.md` and run the exercise as written
- While Copilot runs, use the suggested filler lines (optional)

## Exercise 1 (Intro)

## Exercise 1: Assess the Legacy Codebase

Say:

"Exercise 1 is about assessment: we look at the legacy code, CVE warnings, and modernization opportunities."

"The objective is: Use Copilot to analyze the legacy .NET 6.0 codebase and identify all modernization opportunities including outdated patterns, deprecated APIs, and security vulnerabilities."

"The Claims API was built with .NET 6.0 and contains several legacy patterns that can benefit from modernization. We will use Copilot's Ask mode and @workspace participant to perform a comprehensive assessment before planning the upgrade."

"Why do we assess first? To understand the risks before making changes."

"We will follow the steps in the lab script. I will paste prompt 1.1, 1.2, 1.3, and 1.4 into the chat."

"And now we'll start Exercise 1."

**STEP 1: Build the Project and Observe Warnings**

"Now we build the project with: dotnet build"

"The build will compile the code and check for package vulnerabilities."

"You should see warnings like: 'NU1902: Package X version Y has a known moderate severity vulnerability.'"

**STEP 2: Assess Framework Version and Dependencies**

"Now we use @workspace to analyze packages."

"Copilot will read all project files, analyze dependencies, and identify vulnerable packages."

"The response will show: package name, current version, and recommended safe version."

**STEP 3: Identify Legacy Code Patterns**

"Now we find old C# styles to modernize."

"Copilot will scan the codebase looking for: verbose classes, old constructors, string concatenation, and Newtonsoft.Json usage."

**STEP 4: Generate Assessment Report**

"Finally, we create the assessment file with Agent Mode."

"Agent Mode will create a comprehensive report with: current version, target version, CVEs found, and legacy patterns."

After finishing Exercise 1 (quick check):

"Quick check: did you see NU1902/NU1903 warnings and create the assessment file?"

If you get stuck here, say:

"If you did not see warnings, check the `nuget.config` and run `dotnet build` again."

## Exercise 2: Upgrade Framework with Agent Mode

Say:

"Exercise 2 upgrades the framework to .NET 9 and fixes CVEs with Agent Mode."

"The objective is: Use GitHub Copilot Agent Mode to upgrade the project from .NET 6.0 to .NET 9.0 and update all packages to their latest secure versions."

"Agent Mode can autonomously plan and execute multi-file framework upgrades. We will guide the agent to upgrade the target framework, update all NuGet packages, and resolve any compatibility issues that arise."

"Why upgrade? Security fixes and access to new C# features."

"Check the lab script for prompts 2.1, 2.2, 2.3, and 2.4. I will paste them into the chat."

"And now we'll start Exercise 2."

Safety mantra:

"Review the diff before accepting. Verify TargetFramework is net9.0 and packages are updated."

"When Agent Mode shows you a plan or proposes changes, you will see a diff view. Take your time to review it. Accept if it looks correct, or ask the agent to revise if something is wrong."

"If you see 'Keep' or 'Undo' buttons, remember: Keep = accept the change, Undo = reject it and ask Copilot to revise."

**STEP 1: Plan the Framework Upgrade**

"Copilot will analyze the project and create a step-by-step plan."

"The plan shows what files will be changed and what commands will run."

"Review the plan carefully. Check that it updates to net9.0 and updates all packages."

**STEP 2: Execute the Upgrade**

"Now the agent executes the plan."

"Copilot will update the .csproj to net9.0, update all PackageReferences, run restore and build."

"If errors appear, Copilot will read the error messages and propose fixes automatically."

**STEP 3: Verify CVE Remediation**

"Now we verify that CVE warnings are gone."

"Run dotnet build again and check the output."

"Build should complete without any NU1902/NU1903 warnings."

**STEP 4: Run Tests to Validate Upgrade**

"Now we run tests with: dotnet test"

"The tests verify that the upgrade did not break any functionality."

"If tests fail, ask Agent Mode to fix the compatibility issues."

After finishing Exercise 2:

"Quick check: build should not show NU190 warnings and tests should pass."

If you get stuck here, say:

"If the build fails, copy the error into Copilot and ask it to fix."

"If tests fail, ask Copilot to focus on test fixes only."

## Exercise 3: Refactor DTOs to Records

Say:

"Exercise 3 converts DTO classes to records."

"The objective is: Modernize the DTO classes to use C# records, which provide immutability, value equality, and concise syntax."

"The current DTOs are implemented as verbose classes with explicit constructors and mutable properties. We will use Copilot to convert them to records, reducing boilerplate and improving code quality."

"Why records? Less code for the same result. We remove constructors and boilerplate."

"Follow prompts 3.1, 3.2, 3.3 from the lab script. I will paste them into the chat."

"And now we'll start Exercise 3."

**STEP 1: Analyze Current DTO Structure**

"First, we analyze one DTO with Smart Action 'Explain' on ClaimReadDto.cs."

"Copilot will explain what the class does and how it is structured."

**STEP 2: Convert ClaimReadDto to Record**

"Now we convert one DTO to see the pattern using Agent mode."

"Copilot will rewrite the class as a record with positional parameters."

**STEP 3: Convert All DTOs**

"Now we convert all DTOs with Agent Mode."

"Copilot will convert all DTO files and update the service mapping methods."

"Review each file change before accepting."

**STEP 4: Verify and Test**

"Finally, we build and test with: dotnet build and dotnet test"

After finishing Exercise 3:

"Quick check: all DTO files are records and the project builds."

If you get stuck here, say:

"If a DTO fails, ask Copilot to fix mapping in `ClaimService.cs`."

## Break (5-10 min)

Say:

"We take a short break now. We are about 1 hour into the lab."

"Let me do a quick recap of what we accomplished so far:"

"- Exercise 1: We assessed the legacy code and found CVE warnings."

"- Exercise 2: We upgraded to .NET 9 and fixed all security vulnerabilities."

"- Exercise 3: We converted DTOs to modern records."

"After the break we finish modernization: primary constructors, JSON migration, and final validation."

"I will post the return time in the chat."

If you need to shorten the break:

"We will take 5 minutes so we can finish on time."

### Message to post in chat BEFORE the break:

```text
Break time! We'll return at [TIME]. 
Example: "Break time! We'll return at 14:15" (or "2:15 PM")
Please be back on time so we can finish the lab together.
```

### When the break time is over, post in chat:

```text
We are starting again now. Please join us for Exercise 4.
```

### When you return from break, say:

"Welcome back everyone."

"We will now continue with Exercise 4: Primary Constructors."

"If you are still on a break, please come back now so we can finish on time."

## Exercise 4: Modernize Services with Primary Constructors

Say:

"Exercise 4 uses C# primary constructors in services and controllers."

"The objective is: Refactor service classes to use C# 12 primary constructors, eliminating boilerplate field assignments."

"The current services use traditional constructor injection with explicit field declarations and assignments. C# 12 primary constructors reduce this boilerplate significantly."

"Follow prompts 4.1, 4.2, 4.3, 4.4 from the lab script."

"And now we'll start Exercise 4."

**STEP 1: Convert ClaimService**

"First, we convert ClaimService with Agent mode."

"Copilot will move the constructor parameters to the class declaration and remove the private fields."

**STEP 2: Convert UserService**

"Now we do the same with UserService."

"Copilot will apply the same pattern and update null validation to ArgumentNullException.ThrowIfNull()."

**STEP 3: Convert AuthController**

"Now we convert AuthController."

"Copilot will update the constructor and refactor logging statements."

**STEP 4: Batch Convert Remaining Files**

"Finally, we use Agent Mode to convert all remaining services and controllers."

"Copilot will find all classes with traditional constructors and convert them."

"Review each file change. Check that _context becomes context and _logger becomes logger."

After finishing Exercise 4:

"Quick check: services and controllers use primary constructors and build is clean."

If you get stuck here, say:

"If something is broken, check that field names changed from _context to context."

## Exercise 5: Replace Newtonsoft.Json with System.Text.Json

Say:

"Exercise 5 replaces Newtonsoft.Json with System.Text.Json."

"The objective is: Remove the Newtonsoft.Json dependency and replace all usages with the built-in System.Text.Json, which is faster and more secure."

"The legacy code uses Newtonsoft.Json for serialization. Modern .NET applications should use System.Text.Json for better performance, reduced dependencies, and native integration with ASP.NET Core."

"Why remove Newtonsoft? Better performance, less dependencies, and it is built into .NET."

"Follow prompts 5.1, 5.2, 5.3 from the lab script."

"And now we'll start Exercise 5."

**STEP 1: Find Newtonsoft.Json Usages**

"First, we find all usages with @workspace."

"Copilot will search the entire project and list all files using Newtonsoft."

**STEP 2: Replace JsonConvert Calls**

"Now we replace JsonConvert with JsonSerializer using Agent mode."

"Copilot will update the using statements and method calls: JsonConvert.SerializeObject becomes JsonSerializer.Serialize."

**STEP 3: Remove Package Reference**

"Finally we remove the package reference with Agent Mode."

"Copilot will edit the .csproj file and remove the PackageReference line."

**STEP 4: Verify and Test**

"Build and test with: dotnet build and dotnet test"

After finishing Exercise 5:

"Quick check: no `Newtonsoft` usages remain."

If you get stuck here, say:

"Search for `Newtonsoft` in the project and remove any leftover using statements."

## Exercise 6: Complete Modernization and Validation

Say:

"Exercise 6 finishes modernization: strings, logging, and full validation."

"The objective is: Complete the remaining modernization tasks, validate code behavior consistency, and ensure the modernized codebase is production-ready."

"This exercise covers the final modernization touches: string interpolation, collection expressions, pattern matching, and comprehensive validation of the changes."

"Follow prompts 6.1, 6.2, 6.3, 6.4, 6.5 from the lab script."

"And now we'll start Exercise 6."

Safety mantra:

"Validation is critical: build Release, run tests, and check the health endpoint."

**STEP 1: Modernize String Handling**

"First, we fix all string concatenation with Agent Mode."

"Copilot will find all string concatenations with + and replace them with $\"...\" syntax."

**STEP 2: Add Modern Logging**

"Now we modernize logging to use structured logging."

"Copilot will update logging to use {PropertyName} placeholders for better performance."

**STEP 3: Validate Code Behavior**

"Now we validate that behavior did not change with @workspace."

"Copilot will analyze the changes and identify any that could affect runtime behavior."

**STEP 4: Run Comprehensive Tests**

"Now we run full tests: Release build, unit tests, and health endpoint."

"Build in Release mode with: dotnet build -c Release"

"Run all tests with: dotnet test --verbosity normal"

"Test the health endpoint. You should see HTTP 200 and JSON with status 'Healthy'."

**STEP 5: Generate Modernization Summary**

"Finally we generate the summary file with Agent Mode."

"Copilot will create MODERNIZATION_COMPLETE.md with: framework upgrade, CVEs fixed, code patterns updated, and lines reduced."

After finishing Exercise 6:

"Quick check: Release build passes, tests pass, health endpoint responds, and summary file is created."

If you get stuck here, say:

"If tests fail, copy the failure into Copilot and ask it to fix."

## After The Last Exercise (Closing Script)

Say:

"We finished the lab. The main workflow was: assess -> upgrade -> refactor -> validate."

"Key points:"

"- Agent Mode is powerful but needs review."

"- CVE warnings must be fixed and verified."

"- Modern C# features reduce boilerplate."

"- Always validate with build and tests."

## Labs Reminder and Prerequisites (5 minutes before closing)

Say:

"Now I will paste the survey link. Please fill it in." 

### Copy/Paste (Official Text)

LAB feedback survey:

```text
Please fill our LABS feedback survey, it takes a few minutes for you and it is super important for us to improve our School !
Link:
https://welearngenerali.qualtrics.com/jfe/form/SV_6eSxmtUuuvITaMC
```

## Goodbye

Say:

"Thanks everyone for joining. Have a great day, and see you in the next module."

**IMPORTANT: Stop recording and end the meeting (do not just leave).**
