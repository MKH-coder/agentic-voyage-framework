# Execution Scripts (Layer 3: Doing the work)

This directory holds deterministic, automated scripts.

## Rules for Execution Scripts
1. **Deterministic**: Must perform reproducible actions with defined exit codes (`0` on success).
2. **Safe**: Read secrets only from `.env`. Never commit credentials.
3. **Idempotent**: Where possible, rerunning scripts should not corrupt state.
