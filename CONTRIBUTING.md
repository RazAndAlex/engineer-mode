# Contributing

Thank you for helping. Engineer mode is one skill file, so most changes are small.

## Report a problem

Open an issue with the **Bug report** form. Include:

- what you typed,
- what Claude did,
- what you expected it to do,
- your Claude Code version (`claude --version`).

## Suggest a change

Open an issue with the **Idea** form before you write a large change. Say which step of the interview it changes and why.

## Send a pull request

1. Fork the repository and make a branch.
2. Edit `skills/interview/SKILL.md`. Keep the skill short: every line costs context in each session that loads it.
3. Run `claude plugin validate .` from the repository root. It must pass.
4. Install your copy and try it on one real task:
   ```
   claude plugin marketplace add ./
   claude plugin install engineer-mode@engineer-mode
   ```
5. In the pull request, say what you typed and what Claude did with your change.
6. Add a line to `CHANGELOG.md` under a new version.

By contributing, you agree that your work is published under the [MIT License](LICENSE) and that you follow the [Code of Conduct](CODE_OF_CONDUCT.md).
