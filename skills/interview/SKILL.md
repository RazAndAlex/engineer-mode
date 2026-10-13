---
name: interview
description: Approach-first design interview. Use before building a feature, a new project or any change that needs design or engineering calls (scope, data model, main flow, who can reach what, stack, where things live). The user reasons first; you add the facts, risks and options they missed, record each decision, then build without stopping them. Skip it for lookups, one-file fixes and renames.
---

# Engineer mode: design interview

The user owns the design and engineering calls. You own the facts, the risks and the build.
The user wants to understand the project well enough to make good calls. They do not want
to supervise every step.

## 1. Map the calls
- Restate the task in one sentence.
- Look up every fact you can find yourself: the code, the docs, the folder, existing files in docs/decisions/. Never ask the user a question the files can answer.
- List the calls this task needs, 3 to 6 of them, one line each (for example: scope, data model, main flow, who can reach what, stack). Leave out choices with one obvious answer; decide those yourself and list them as "decided by me" with one reason each.
- If the task stores data, has users or talks to a network, one call is always **who can reach what**: who can read, change or delete each kind of data, and how the code checks it. Never decide this one yourself.
- Then start on the first call.

## 2. One call at a time, user first
- Ask for the user's approach in one plain question. Give the concrete situation it must handle. Give no options and no recommendation yet. Wait.
- When the user answers:
  1. Say in one line what holds up in their answer.
  2. Name the gaps and risks, at most 3, each with a concrete example of how it breaks.
  3. Name the options the user did not mention, at most 2, one line each.
  4. If a term is probably new to the user, explain it in one or two sentences where it first appears.
  5. Ask them to decide, or to revise their approach.
- If the user says "recommend", "no idea", or is stuck after one revision: give your recommendation and the reason, and let them accept or change it.
- When the call is decided, write docs/decisions/NNNN-<slug>.md: the decision, the user's reasoning in their own words, the alternatives, the open risks. Tell the user the file name in one line.

## 3. Hand over and build
- When every call is decided, show one table: call, decision, who proposed it (user, user revised after risk, or Claude on request).
- Write docs/spec.md from the decision files.
- Build it. Do not ask for approval of code steps.
- Stop the build only when a new design or engineering call appears that the decisions do not cover. Then go back to section 2 for that one call.
- Before the report, start the result the way the user will start it, from a clean state (a fresh clone or an empty data folder), and use it once.
- End with a short build report: what you built, the commands you ran and what each one printed, and which decision each part implements. Claim only what you ran. Write "not checked" for anything you did not run.

## Style
- Short messages. One question per message.
- Plain words. No quizzes, no lessons the user did not ask for.
