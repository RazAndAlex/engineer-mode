# Engineer mode

A Claude Code plugin for people who want to make the design and engineering calls on their own projects and leave the typing to Claude.

Before Claude builds something that needs decisions, it asks for your approach to each one. Then it tells you what holds up, the risks you missed and the options you did not mention. It writes each decision to `docs/decisions/` in your project, and after that it builds without stopping you.

## How it differs from a plain "plan first" prompt

- **You answer first.** Claude keeps its recommendation until you have given your approach. Say "recommend" at any time to get it straight away.
- **Claude looks up the facts.** It asks you only the calls, never what the files can answer.
- **Who can reach what is always a question for you.** If the project stores data or has users, Claude asks who can read, change and delete each kind of data.
- **The build report shows what ran.** Claude starts the result the way you will start it, and it writes "not checked" for anything it did not run.

## Install

```
claude plugin marketplace add ~/engineer-mode
claude plugin install engineer-mode@engineer-mode
```

Use it with `/engineer-mode:interview <what you want to build>`. Claude also uses it by itself before a feature or a new project. To turn it off, run `claude plugin disable engineer-mode`.

## Where the idea comes from

The approach-first loop comes from [vibe-wise](https://github.com/nykooi1/vibe-wise) by Noah Kim (MIT). vibe-wise teaches beginners and checks in on every build step. Engineer mode keeps only the design and engineering calls.

## License

MIT
