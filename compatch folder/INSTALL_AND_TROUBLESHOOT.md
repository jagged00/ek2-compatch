EK2 + Realistic Attraction Compatch — Install & Troubleshooting

Symptom this doc addresses
- In-game only Elder Kings 2 content appears.
- Realistic Attraction traits/modifiers do not appear.
- Compatch appears to do nothing.

Most likely root cause
- The compatch files are not being loaded by CK3 at all.
- If CK3 is loading this compatch, you should usually see script parse references from files prefixed with `zz_ek2_rm_` in `error.log`.
- If there are zero references to those files, CK3 never mounted this mod folder.

What this repository currently contains
- Script overrides only (under `common/...`) inside `compatch folder/`.
- No launcher metadata files (`descriptor.mod` and a matching `.mod` file) are included by default.

Required local mod structure (manual install)
1) Put this mod folder in your CK3 mod directory, e.g.:
   `Documents/Paradox Interactive/Crusader Kings III/mod/ek2_rm_compatch/`
2) Ensure this descriptor file exists inside that folder:
   `Documents/.../mod/ek2_rm_compatch/descriptor.mod`
3) Ensure a launcher file exists alongside mod folders:
   `Documents/.../mod/ek2_rm_compatch.mod`
4) Both files must point to the same path and use the same replace_path list.

Load order (top to bottom)
1. Elder Kings 2
2. Realistic Attraction
3. EK2 + RM Compatch (last)

Version/dependency gotchas
- If Realistic Attraction is disabled, missing, or wrong version, its traits will not appear.
- If the compatch is loaded before RM, RM will overwrite compatch script blocks.
- If EK2 or RM major versions changed, script keys can drift and require compatch updates.

Quick checks
- In launcher, verify all 3 mods are enabled in the same playset.
- Start a NEW save for testing (old saves can hide changed scripted behavior).
- Search `error.log` for `zz_ek2_rm_`:
  - if found: compatch is loading (then diagnose script logic/version mismatch).
  - if not found: install/descriptor/playset issue.

Known non-blocking log noise
- EK2 itself can emit unrelated errors/warnings in large logs.
- Those do not prove this compatch loaded; only direct references to compatch files do.
