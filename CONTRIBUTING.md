# Contributing

Thanks for helping keep this list accurate. Corrections are as welcome as additions — a list like this decays fast.

## What belongs here

- **Open source or freely available** projects, models, datasets, papers, and guides that are useful for building AI companions.
- Closed/proprietary products only when they've published something genuinely educational (research, specs, engineering write-ups) — those go in **Adjacent Reading**, linked to the educational material, not the product.
- Active, working projects. Something unmaintained can stay if it's still widely used or historically important, but say so in its description (e.g. "not updated since 2024").

## How to suggest a change

- **Quick fix or addition:** open a pull request editing `README.md`.
- **Not sure if it fits, or want to discuss placement:** [open an issue](https://github.com/yuri-os/awesome-agentic-ai-waifus/issues/new/choose) using one of the templates.
- **You maintain a listed project** and think its description or placement is wrong: open an issue — this is explicitly welcome.

## Entry format

```markdown
- **[Project Name](https://link)** ★12k — One-sentence description of what it is. One sentence on why it matters for companions specifically, or when you'd pick it over the alternatives.
```

- **Link every entry.** Prefer the source repo; use the project site or Hugging Face page when there's no repo.
- **Stars (★)** for GitHub repos, using the current count:
  - under 1,000: exact (`★609`)
  - 1,000–9,999: one decimal (`★4.6k`)
  - 10,000 and up: whole thousands (`★51k`)
- **One entry per project.** If a project fits two sections, put it in the best one and refer to it from the other in prose rather than listing it twice.
- **Describe it honestly.** Note big caveats (license restrictions, maintenance status, hardware needs). No marketing copy.

## Ordering

Within a section, entries are ordered roughly by **importance/maturity**, not alphabetically: stars, ecosystem centrality, and how load-bearing the project is. Stars are the default tiebreaker. If you put something above a higher-starred entry, say why in the PR.

## Links

A [link checker](.github/workflows/links.yml) runs on every PR that touches Markdown and weekly on `master`; the weekly run opens an issue when it finds dead links. If your PR fails the check, fix or replace the link. If the site just blocks bots, add it to `exclude` in [`lychee.toml`](lychee.toml).

## License

By contributing, you agree to release your contribution under [CC0 1.0](LICENSE), the same as the rest of the list.
