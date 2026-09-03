# Czech locale for Hermes Desktop

Community-maintained Czech (`cs`) translation catalog for the native Hermes Desktop application.

This repository contains a complete, manually reviewed Czech translation of the Desktop `Translations` tree. It is intended both as a reference implementation for [NousResearch/hermes-agent#102178](https://github.com/NousResearch/hermes-agent/issues/102178) and as improved Czech translation material for [NousResearch/hermes-agent#56521](https://github.com/NousResearch/hermes-agent/pull/56521).

## Status

- Source file: `apps/desktop/src/i18n/cs.ts`
- Based on Hermes Agent commit: `e629c900a`
- Translation entries: 3,221
- Missing entries against that source revision: 0
- Extra entries against that source revision: 0
- Verified on Windows 10 with the native Hermes Desktop build
- SHA-256 of `cs.ts`: `0652d25702d4c1e12471fe223ae34f0e34a55a5f959b222b031e13343dae87f0`

The translation uses `defineLocale()`, so future keys that are not yet present can fall back to English when used inside a compatible Hermes source tree.

## Important

This is currently a **translation catalog, not an installable Desktop plugin**. Hermes Desktop does not yet expose an API that allows a plugin to register a locale for the core application UI.

Do not replace a stock Hermes Desktop build with a locally rebuilt application solely to install this file unless you understand how that interacts with `hermes update`.

The proposed `registerAppLocale()` capability in issue #102178 would allow this catalog to become an update-safe language-pack plugin stored outside the application build.

## Intended future installation

If the proposed locale extension point is accepted, the target shape would be a normal disk plugin under:

```text
$HERMES_HOME/desktop-plugins/locale-cs/plugin.js
```

The language pack would register `cs`, appear as **Čeština** in the normal language picker, and fall back to the built-in English catalog for any missing future keys.

## Maintenance

Hermes Desktop evolves quickly. Updates to the English catalog should be compared against this file before claiming compatibility with a newer Hermes revision.

When updating the translation:

1. Compare the current upstream `en.ts` and `types.ts` with the recorded base revision.
2. Add or update Czech entries while preserving function parameters and interpolation behavior.
3. Run the Desktop typecheck and i18n tests.
4. Update the base commit, entry counts, and SHA-256 recorded above.

## License

Released under the MIT License, matching the upstream Hermes Agent project.

