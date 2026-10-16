# Contributing

Help agents choose the right Douchanchan capability and interpret its results accurately. Do not reproduce the interface manual.

## Writing

- Keep only guidance that improves source selection, execution or interpretation; document supported behavior rather than guessed capabilities.
- Keep routing and compatibility in `SKILL.md`; load `references/browser.md` only for setup or recovery. Group task references by workflow: posts/data, media, analysis and MCP account reads.
- Keep `README.md` in Simplified Chinese and `README.en.md` equivalent. Skill instructions use English; responses follow the user's language.
- Keep references focused on product decisions and actions; avoid internal implementation details and separate files for short shared notes.

## Versions

Keep the skill's `metadata.version` separate from the supported browser extension version range. Set the skill version when preparing a release; unreleased edits do not need individual version bumps. Publish from `main` and tag releases as `v<version>`.

## Validation

Validate the skill against the [Agent Skills specification](https://agentskills.io/specification), check local references and bilingual installation commands, and run `git diff --check`. Format and link checks do not prove automatic discovery or successful execution in every agent client.
