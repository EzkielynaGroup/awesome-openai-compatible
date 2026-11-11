# Contribution Guidelines

Thank you for helping keep this list accurate. Corrections are as welcome as new entries.

## What belongs here

- Pages from an API provider or server project that document how its OpenAI-compatible API differs from the OpenAI API: ignored, rejected or renamed parameters, response fields, streaming, usage reporting, errors, or headers.
- Translation layers and SDKs that document how they map parameters between providers.
- Conformance tests, probes and canary prompt sets that anyone can run.
- Trackers that publish latency, uptime, throughput or price data together with a description of how it is measured.

## What does not belong here

- Marketing pages, comparison pages that rank vendors, and articles without a reproducible example.
- Services that resell shared or pooled consumer accounts, convert web chat products into APIs, or advertise use with no usage limits.
- Uncensored, abliterated or NSFW model listings.

## Requirements for an entry

- The link points to the page that documents the claim. Use a heading anchor or a `#:~:text=` fragment when the claim sits deep in a long page.
- The description states what the page documents, in one sentence that starts with a capital letter and ends with a period. No superlatives, no prices that change weekly, no comparisons with other entries.
- Open source projects must be public, not archived, and have a commit within the last six months.
- Trackers must describe their method (what is measured, over what window).
- Vendors may add their own pages. Say so in the pull request.

## Format

```markdown
- [Name](https://example.com/docs/openai-compatibility) - What the page documents.
```

- Keep each section in alphabetical order, ignoring case.
- Use the product name as the provider writes it.
- One entry per pull request, with a title such as `Add Name`, `Update Name` or `Remove Name`.

## Before you open a pull request

- Run `npx awesome-lint` in the repository and fix what it reports.
- Open the link in a private browser window to confirm it works without logging in.

## Removing entries

Open a pull request or an issue with the reason (broken link, page removed, project archived, claim no longer on the page) and a link to the evidence. A weekly link check also opens a report when links break.

By contributing, you agree to release your contribution under [CC0 1.0](LICENSE).
