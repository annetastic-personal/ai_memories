# Quick Reference (Commands & File Updates)
- Place comments on a separate line above the code they describe, not inline at the end of the line.

- Only provide commit messages for files that have been modified, added, or deleted—never for unmodified files.
- When adding or updating a global preference, always ask whether to update the ai_memories/memory-backup/preferences.md file to keep the backup in sync.

- Always specify the target terminal and cwd in plain text before any terminal command code block.
- For any command or commit response, include Terminal + Cwd + a terminal-ready code block; if any part is missing, reject the command response and ask for the missing detail.
- When giving terminal commands in a multi-repo workspace, specify which terminal/cwd to use.
- When providing a commit message, use: type(scope): summary, and include a body with bullet points in imperative mood.
- Format git commit commands with exactly two -m flags: one for the summary, one for the full body as a multi-line string with each bullet on its own line.
- Always tag command code blocks with a shell language (powershell) so the VS Code "Insert into Terminal" button appears.
- Do not include comments in console command/code blocks for the user.
- When saving or updating memories, always ask which repo the memory should go into and confirm before duplicating to ai_memories.
- If a memory is repo-specific, do not copy it to ai_memories unless explicitly requested.

# Preferences

This file stores persistent instruction preferences for reuse across workspaces.

- When adding or updating a global preference, always ask whether to update the ai_memories/memory-backup/preferences.md file to keep the backup in sync.
- Trigger phrase: "session end check".
- When user says "session end check":
  - Review the session and recommend any global or repo-level memory updates, including a summary of in-progress work for easy resumption.
  - Remind user to sync updated memories with the appropriate repo backups if changes were made.
  - Point out any uncommitted or unpushed work in connected repositories.
  - Verify uncommitted and unpushed work using actual Git status/upstream state per repo instead of inference.
  - Remind user to close any open VPN connections.
  - Remind user to close any open terminals connected to external servers.
  - Deliver all reminders as a clear, human-friendly bullet list—no code, just actionable instructions.
  - Keep the output concise by default with only actionable items.
- Do not include comments in console command/code blocks for the user.

- Confirm with user before changing any files.
- Confirm with user before running terminal commands.
- Confirm with user before running builds.
- Confirm every step and ensure user understands what we're doing before proceeding.
- Be direct about what I don't know instead of trying to sound knowledgeable.
- Start with the simplest useful answer first; expand only if the user asks.
- Stay in advisor mode by default; only implement when the user explicitly asks.
- Treat "let's do..." as a request for next steps, not authorization to make changes.
- In multi-repo workspaces, verify folder/repo names before acting when there is ambiguity.
- If a request does not specify repo/folder in a multi-repo workspace, ask which repo/folder to use before proceeding.
- When giving terminal commands in a multi-repo workspace, specify which terminal/cwd to use.
- For any command or commit response, include Terminal + Cwd + a terminal-ready code block; if any part is missing, reject the command response and ask for the missing detail.
- When saving memories, ask which repo the memory should go into.
- If a memory is repo-specific, do not copy it to ai_memories unless explicitly requested.
- Commit messages must use: type(scope): summary.
- Commit messages must include a body with bullet points.
- Commit message body must explain both what changed and why.
- Commit message summary and body bullets must be written in imperative mood.
- Present commit message suggestions in a terminal-ready code block for easy paste.
- Format git commit commands with exactly two -m flags: one for the summary, one for the full body as a multi-line string with each bullet on its own line.
- Always tag command code blocks with a shell language (powershell) so the VS Code "Insert into Terminal" button appears.
- When working with wiki docs, use canonical GitHub Wiki page URLs (for example, https://github.com/odomaf/references/wiki/step-00-upfront-decisions) so pages open in rendered wiki view; avoid .md file-path links and avoid %2F-encoded wiki path links unless explicitly verified.
- When asked for a commit message only, provide only the commit command — do not include git add or any other commands.
- Trigger phrase: "Prefs Check".
- When user says "Prefs Check", apply saved preferences first, list applied preferences in one line before answering, and for commands/commits include target terminal/cwd first plus required commit format.
- When publishing new documentation for the GitHub Wiki, ensure the files are placed in docs/wiki or a subfolder that is included by the publishing script. Files outside this path will not appear in the wiki.
- When linking to sample or step pages in the wiki, use the dash-joined path as rendered by GitHub (e.g., ops-steps-sample-step-1-server-layout-sample) for all canonical URLs.
- After moving or renaming documentation files, always update all internal links to match the new canonical wiki page names.
- When publishing to GitHub Wiki, all .md files (including those from subfolders) appear at the wiki root as pages named only by their filename (e.g., step-1-server-layout-sample), not by their full path.
- All canonical wiki links must use only the filename portion (e.g., https://github.com/odomaf/references/wiki/step-1-server-layout-sample), regardless of source folder structure.
- After moving or reorganizing wiki source files, always verify the actual wiki page URLs and update all links to match the rendered wiki.
- I already have an ai_memories repo for persistent instructions.
- For afodom-spa-assessment, store repo-specific memory backups in docs/ai_repo_memories.md.
- Keep repo-specific memories in the repo they belong to as a backup copy.
- When documenting decisions, assumptions, or chosen approaches, use imperative voice.
- When reviewing code for an interview/assessment context, evaluate comments and structure from both a junior reader's clarity perspective and a senior reviewer's signal perspective before adding or removing comments.
- Trigger phrase: "Interview Lens". When user says "Interview Lens", review the current code from both a junior reader's clarity perspective and a senior reviewer's signal perspective, then report findings and recommendations.
- For modern .NET CLI workflows, `dotnet new sln` may create `.slnx`; always use the actual generated solution filename in commands.
- On Windows, verify .NET SDK architecture (x64 vs x86); x86 installs may not appear in normal x64 `dotnet` usage.
- After SDK installs, open a new terminal (or restart VS Code) before rechecking `dotnet --list-sdks`.
- In planning docs, use completion timestamps in this format: `YYYY-MM-DD HH:MM (UTC±HH:MM)`.
- Prefer separate files for implementation plan and implementation timeline when both are maintained.
- Bash is the default for helper scripts and tools (e.g., coverage reports, automation). Use bash unless there's a specific reason to use PowerShell (Windows-only requirement, repo convention, etc.).
- When running dotnet test in a multi-project solution, always specify the test project path explicitly to avoid MSB1008 "Only one project can be specified" error.
- Top-level statement programs generate a synthetic Main$ method that shows up in coverage with 0% and a high CRAP score. Exclude it via runsettings Exclude tag with [AssemblyName]Program under XPlat Code Coverage configuration.
- When writing to memory files, never include backtick-wrapped code containing angle brackets or special characters (e.g., angle-bracket identifiers). Describe them in plain prose instead to avoid memory file corruption.
- After every memory write (str_replace or create), immediately verify with memory view to catch corruption before the session ends.
- Prefer assigning return values to a named variable before returning rather than inlining the expression in the return statement. Aids readability and debuggability.
- Comment code clearly for maintainability without over-commenting.
- Place comments on a separate line above the code they describe, not inline at the end of the line.

## Memory Log

### 2026-05-05

Reason: Add audit-friendly structure for easier preference checks and updates.

Changes:

- Add `Active Rules` section as the current source of truth.
- Add `Memory Log` section for dated change history.
- Preserve all existing preference entries without modification.

### 2026-05-05 (in progress)

Reason: Session updates to memory management and commit message formatting preferences.

Changes:

- Replace "ask whether to update ai_memories" rule with "ask which repo memory should go into."
- Add rule: repo-specific memories stay local unless explicitly requested to go to ai_memories.
- Add rule: keep a backup copy of repo-specific memories inside the repo they belong to.
- Add rule: for afodom-spa-assessment, store repo-specific memory backups in docs/ai_repo_memories.md.
- Add rule: format git commit commands with exactly two -m flags, with the full body kept as a multi-line string.
- Add rule: write decision and assumption documents in first-person "I" rather than "we".

### 2026-05-05 (end of session)

Reason: Capture lessons learned from .NET 10 SDK setup and planning document conventions.

Changes:

- Add rule: `dotnet new sln` may generate `.slnx`; always use the actual generated solution filename.
- Add rule: on Windows, verify .NET SDK is x64, not x86, before troubleshooting dotnet issues.
- Add rule: after SDK installs, open a new terminal before rechecking `dotnet --list-sdks`.
- Add rule: use `YYYY-MM-DD HH:MM (UTC±HH:MM)` format for completion timestamps in planning docs.
- Add rule: prefer separate files for implementation plan and implementation timeline.

### 2026-05-06

Reason: Capture lessons learned from coverage tooling and dotnet test usage in multi-project solutions.

Changes:

- Add rule: bash is the default for helper scripts; only use PowerShell when there is a specific reason.
- Add rule: always specify test project path in dotnet test to avoid MSB1008 in multi-project solutions.
- Add rule: exclude top-level statement Program from coverage via runsettings to suppress synthetic Main$ CRAP score.

### 2026-05-06 (session 3)

Reason: Prevent recurrence of memory file corruption caused by special characters in str_replace content.

Changes:

- Add rule: never use backtick-wrapped code containing angle brackets or special characters in memory files; use plain prose instead.
- Add rule: after every memory write, immediately verify with memory view to catch corruption before the session ends.

### 2026-05-27

Reason: Anne gets caught up in work and is forgetful, needs reminders to improve less than desirable habits

Changes:

- Add key phrase: "session end check".
- Add instructions for end-of-session reminders covering memory updates, repo sync, uncommitted work, VPNs, and external terminals.

