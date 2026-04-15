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

## 00:05-00:15 Short Intro (What We Will Do)

Say:

"Today we modernize a .NET 6 Claims API to .NET 9 using GitHub Copilot."

"I will do each exercise first, then you repeat it. If you are behind, finish your step and then join us in the next exercise."

"I will paste the prompts in the meeting chat so you can copy them."

"Please stay muted. Ask questions in the chat. I will pause after each exercise."

"We take a short break in the middle: 10 minutes if we are on time, otherwise 5 minutes."

Two quick tips:

"Tip 1: Context. Copilot needs context."

"- Select code and ask questions."

"- Use `@workspace` for whole project answers."

"- Attach files or drag files into the chat."

"Tip 2: Model."

"- Use Auto for normal work."

"- Use a stronger model for Agent Mode or complex steps."

While people open the lab (optional filler):

"Please keep the lab script open on the side. It has the exact prompts."

"I will show each prompt on screen and paste it into chat."

"If you are unsure, wait for my screen before you run the prompt."

If Copilot is slow (optional filler):

"If Copilot is slow, please wait. It is reading the project."

"If the answer is too long, ask: 'Give me a short summary in 5 bullets.'"

## Quick Glossary (Say it once, optional)

"CVE: a known security issue in a package."

"Record: a short class for data objects."

"Primary constructor: a shorter way to write constructor and fields."

"System.Text.Json: the built-in JSON serializer in .NET."

## 00:15-00:25 Environment Check

Say:

"Before Exercise 1, please check Copilot Chat works. If not, restart VS Code and check your GitHub login."

"Also, open the whole project folder, not only one file."

If Dev Container is used, say:

"Please make sure you are inside the Dev Container. The terminal should show the container path."

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

Say:

"Exercise 1 is about assessment: we look at the legacy code, CVE warnings, and modernization opportunities."

"We will follow the steps in the lab script. I will paste prompt 1.1, 1.2, 1.3, and 1.4 into the chat."

"And now we'll start Exercise 1."

While Copilot is working (optional filler):

"Use Ask mode to understand the code before changing anything."

"We are looking for warnings and risky packages. This is a safety step."

"Step 1 is the build. We want to see warnings in the output."

"Step 2 is analysis with `@workspace`. It gives us a list of packages and versions."

"Step 3 is legacy patterns. We want to find old C# styles to modernize."

"Step 4 is the assessment file. This is our plan for the upgrade."

"If you get a long answer, scroll and check the summary at the end."

"If Copilot misses a package, ask again with `@workspace` and be specific."

"If the response is too long, ask: 'Give me a short table with package, current version, safe version.'"

"If you are not sure what a warning means, ask Copilot: 'Explain NU1902 and NU1903 in one sentence.'"

Mid-step status check (optional):

"If you are still building, type `B` in the chat. If build finished, type `D`."

After finishing Exercise 1 (quick check):

"Quick check: did you see NU1902/NU1903 warnings and create the assessment file?"

Mini recap (optional):

"We now know the current framework and the risky packages. This is our baseline."

If you get stuck here, say:

"If you did not see warnings, check the `nuget.config` and run `dotnet build` again."

"If the build fails, do not fix it yet. First read the error and share it in chat."

Q&A micro-pause (30-60 seconds):

"Please type `OK` if you're done, `1` if you're stuck, or `2` if Copilot isn't responding."

## Exercise 2 (Intro)

Say:

"Exercise 2 upgrades the framework to .NET 9 and fixes CVEs with Agent Mode."

"Check the lab script for prompts 2.1, 2.2, 2.3, and 2.4. I will paste them into the chat."

"And now we'll start Exercise 2."

Safety mantra:

"Review the diff before accepting. Verify TargetFramework is net9.0 and packages are updated."

While Copilot proposes changes (optional filler):

"Agent should show a plan. It should include TargetFramework update, package updates, restore, and build."

"If the plan misses tests, ask the agent to run tests after the build."

"If you see many package updates, that is normal. We want latest stable versions."

"Please do not accept changes you do not understand. Ask for a smaller step."

"Now the agent updates the .csproj to net9.0."

"Then it updates packages to the latest stable versions."

"After that, it runs restore and build to confirm the upgrade."

"If errors appear, the agent should fix them before we continue."

"If Agent is fast, pause and read the plan out loud. It helps everyone follow."

"If Agent is slow, say: 'It is reading many files. That is normal.'"

Mid-step status check (optional):

"If the plan is ready, type `P` in the chat. If you are still waiting, type `W`."

After finishing Exercise 2:

"Quick check: build should not show NU190 warnings and tests should pass."

Mini recap (optional):

"Now the project targets .NET 9 and CVE warnings should be gone."

If you get stuck here, say:

"If the build fails, copy the error into Copilot and ask it to fix."

"If tests fail, ask Copilot to focus on test fixes only."

"If NU190 warnings remain, ask Copilot to list which package is still vulnerable."

Q&A micro-pause (30-60 seconds):

"Type `OK` if you're done, `1` if you're stuck, `2` if Copilot isn't responding."

## Exercise 3 (Intro)

Say:

"Exercise 3 converts DTO classes to records."

"Follow prompts 3.1, 3.2, 3.3 from the lab script. I will paste them into the chat."

"And now we'll start Exercise 3."

While Copilot is working (optional filler):

"Records reduce boilerplate and are good for data objects."

"After conversion, check the constructors are gone. Records create them for us."

"If a record needs default values, add them carefully in the signature."

"We start with one DTO to see the pattern."

"Then we convert all DTOs in the folder."

"We also update mapping code so it matches the new record syntax."

"If you see warnings about nullable values, ask Copilot to add safe defaults."

Mid-step status check (optional):

"If your DTOs are converted, type `R` in the chat. If not, type `N`."

After finishing Exercise 3:

"Quick check: all DTO files are records and the project builds."

Mini recap (optional):

"DTOs are now cleaner and easier to read."

If you get stuck here, say:

"If a DTO fails, ask Copilot to fix mapping in `ClaimService.cs`."

"If you see errors about property setters, check if the code expects mutation."

Q&A micro-pause (30-60 seconds):

"Type `OK` if you're done, `1` if you're stuck, `2` if Copilot isn't responding."

## Break (5-10 min)

Say:

"We take a short break now. We are about 1 hour into the lab."

"I will post the return time in the chat."

"After the break we finish modernization: primary constructors, JSON migration, and validation."

If you need to shorten the break:

"We will take 5 minutes so we can finish on time."

## Exercise 4 (Intro)

Say:

"Exercise 4 uses C# primary constructors in services and controllers."

"Follow prompts 4.1, 4.2, 4.3, 4.4 from the lab script."

"And now we'll start Exercise 4."

While Copilot is working (optional filler):

"Primary constructors remove field and constructor boilerplate."

"After the change, use the new parameter names directly in the class."

"Be careful: `_logger` becomes `logger`, `_context` becomes `context`."

"We update services first, then controllers."

"This change should not affect behavior, only the syntax."

"If you see a null check, we simplify it with `ArgumentNullException.ThrowIfNull()`."

"If you see compile errors, they are often simple renames." 

Mid-step status check (optional):

"If the file builds, type `B` in the chat. If not, type `E`."

After finishing Exercise 4:

"Quick check: services/controllers use primary constructors and build is clean."

Mini recap (optional):

"We reduced boilerplate and kept the same logic."

If you get stuck here, say:

"If something is broken, check that `_context` and `_logger` were replaced with `context` and `logger`."

"If a controller fails, check constructor signatures and DI registrations."

Q&A micro-pause (30-60 seconds):

"Type `OK` if you're done, `1` if you're stuck, `2` if Copilot isn't responding."

## Exercise 5 (Intro)

Say:

"Exercise 5 replaces Newtonsoft.Json with System.Text.Json."

"Follow prompts 5.1, 5.2, 5.3 from the lab script."

"And now we'll start Exercise 5."

While Copilot is working (optional filler):

"This removes an extra dependency and uses the built-in serializer."

"Check that JsonConvert calls are replaced by JsonSerializer."

"After removing the package, rebuild to confirm no missing references."

"We first find all Newtonsoft usages."

"Then we replace the API calls with System.Text.Json."

"Finally we remove the package reference from the project file."

"If you see options changes, ask Copilot to align JSON options with old behavior."

Mid-step status check (optional):

"If Newtonsoft is removed, type `N` in the chat. If not, type `S` (still)."

After finishing Exercise 5:

"Quick check: no `Newtonsoft` usages remain."

Mini recap (optional):

"We now use System.Text.Json everywhere."

If you get stuck here, say:

"Search for `Newtonsoft` in the project and remove any leftover using statements."

"If you see JSON options differences, check if naming policy changed."

Q&A micro-pause (30-60 seconds):

"Type `OK` if you're done, `1` if you're stuck, `2` if Copilot isn't responding."

## Exercise 6 (Intro)

Say:

"Exercise 6 finishes modernization: strings, logging, and full validation."

"Follow prompts 6.1, 6.2, 6.3, 6.4, 6.5 from the lab script."

"And now we'll start Exercise 6."

Safety mantra:

"Validation is critical: build Release, run tests, and check the health endpoint."

While Copilot is running (optional filler):

"We want modern syntax without changing behavior."

"Focus on string interpolation and structured logging."

"If the agent changes logic, reject and ask for syntax-only changes."

"We modernize strings and logs first."

"Then we validate behavior with Release build and tests."

"Finally we generate the modernization summary file."

"If you are unsure, run the tests before accepting more changes."

Mid-step status check (optional):

"If tests finished, type `T` in the chat. If still running, type `R`."

After finishing Exercise 6:

"Quick check: Release build passes, tests pass, health endpoint responds, and summary file is created."

Mini recap (optional):

"We completed the modernization and validated behavior."

If you get stuck here, say:

"If tests fail, copy the failure into Copilot and ask it to fix."

"If health check fails, confirm the API is running and correct port is used."

Q&A micro-pause (30-60 seconds):

"Type `OK` if you're done, `1` if you're stuck, `2` if Copilot isn't responding."

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

"Before we close, a quick reminder about future labs and support."

"If you want to practice more or attend other modules, please check the requirements before registering."

"Support Calls are available every Monday and Friday if you need help with setup."

"I will post the information in the chat now."

Copy/paste in chat (optional):

```text
Support calls are available every Monday and Friday. If you need help with lab setup or have questions, please write to TechnicalExcellenceSchools@generali.com
```

"Now I will paste the survey link. Please fill it in." 

If there is extra time (optional):

"If we have time, I can show a quick recap of the files changed and the key commands used."

### Copy/Paste (Official Text)

LAB feedback survey:

```text
Please fill our LABS feedback survey, it takes a few minutes for you and it is super important for us to improve our School !
Link:
https://welearngenerali.qualtrics.com/jfe/form/SV_6eSxmtUuuvITaMC
```

Environment issues message:

```text
If you experience issues with requirements and setup of lab environment, please consider to register again in another date and join our Support Calls available every Monday and Friday. Please write an email to
TechnicalExcellenceSchools@generali.com and inform us about this.
```

## Goodbye

Say:

"Thanks everyone for joining. Have a great day, and see you in the next module."

**IMPORTANT: Stop recording and end the meeting (do not just leave).**
