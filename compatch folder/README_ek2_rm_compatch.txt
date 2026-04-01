EK2 + RM Height/Aging Compatch Notes

Reference inputs used:
1) EK2 reference files:
   - culture/pillars/00_heritage.txt (species + heritage_lifespan parameters)
   - ethnicity files with gene_height distributions/comments for lore race height baselines
2) RM reference files:
   - common/scripted_effects/gene_default_distributions.txt
   - common/scripted_effects/aging effect.txt
   - common/script_values/aging values.txt

What this compatch changes:
- Replaces RM default random height gene generation for spawned/generated characters with EK2 lore buckets and RM-style weighted variance.
- Keeps children natural: parented inheritance path remains RM-driven (no forced equalized child genes).
- Adds hard guardrails against extreme hybrid/outlier values to avoid portrait spill/glitch cases.
- Extends growth/puberty/visual-aging pacing for long-lived races using EK2 heritage_lifespan parameters.
- Overrides RM visual-age on_actions so yearly visual aging gain is also scaled by EK2 lifespan parameters.

Load order (top -> bottom):
1. Elder Kings 2 (EK2)
2. Realistic Attraction Mod (RM)
3. This compatch (MUST be last)

Implementation note:
- Files are prefixed with zz_ so this compatch overwrites RM script blocks.
