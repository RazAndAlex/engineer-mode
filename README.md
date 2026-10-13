# Engineer mode

A Claude Code plugin for people who want to make the design and engineering calls on their own projects and leave the typing to Claude.

Before Claude builds something that needs decisions, it asks for your approach to each one. Then it tells you what holds up, the risks you missed and the options you did not mention. It writes each decision to `docs/decisions/` in your project. After that it builds without stopping you.

![One call played out: Claude asks with no options, you answer, Claude names one risk, you revise your own answer, and the decision is filed as yours](docs/media/one-call.gif)

## Install

In a terminal:

```
claude plugin marketplace add RazAndAlex/engineer-mode
claude plugin install engineer-mode@engineer-mode
```

Or inside a Claude Code session:

```
/plugin marketplace add RazAndAlex/engineer-mode
/plugin install engineer-mode@engineer-mode
```

Start a new session after you install it.

## Use

```
/engineer-mode:interview <what you want to build>
```

Claude also starts the interview by itself before a feature or a new project. It skips lookups, one-file fixes and renames.

To turn it off, run `claude plugin disable engineer-mode`. To remove it, run `claude plugin uninstall engineer-mode`.

## An example, start to finish

You type: `/engineer-mode:interview a page where my running club can sign up for Saturday runs`.

1. **Claude maps the calls.** It reads the project first, then lists the calls it needs from you: scope, data model, who can reach what. It decides the obvious ones itself and says so ("decided by me: same stack as the rest of the repo").
2. **You answer first.** Claude asks: "Two people sign up for the last place at the same moment. What should happen?" It gives no options yet.
3. **Claude checks your answer, and you revise it.** You say "first one wins". Claude says that holds up, then names one risk: someone cancels at 7am and the place stays empty. You change your own answer: keep a waiting list and text the next person.
4. **The decision goes on file.** Claude writes `docs/decisions/0002-full-runs.md` with your choice, your reasoning in your own words, the alternatives and the open risks.
5. **Who can reach what is always your call.** Claude asks who can see the sign-up list and who can delete a sign-up. It never decides this one alone.
6. **Claude builds.** It shows one table of every call and who proposed it, writes `docs/spec.md`, and builds without asking you to approve each step.
7. **The report shows what ran.** Claude starts the page from a clean state, uses it once, and lists the commands it ran with their output. Anything it did not run is marked "not checked".

## How it differs from a plain "plan first" prompt

- **You answer first.** Claude keeps its recommendation until you have given your approach. Say "recommend" at any time to get it at once.
- **Claude looks up the facts.** It asks you only for the calls. It never asks what the files can answer.
- **Who can reach what is always a question for you.** If the project stores data, has users or talks to a network, Claude asks who can read, change and delete each kind of data.
- **The build report shows what ran.** Claude starts the result the way you will start it.

## What it writes in your project

| File | When |
|---|---|
| `docs/decisions/NNNN-<slug>.md` | After each call: the decision, your reasoning, the alternatives, the open risks |
| `docs/spec.md` | When every call is decided |

## Where the idea comes from

The approach-first loop comes from [vibe-wise](https://github.com/nykooi1/vibe-wise) by Noah Kim (MIT). vibe-wise teaches beginners and checks in on every build step. Engineer mode keeps only the design and engineering calls.

## License

MIT. See [LICENSE](LICENSE).
