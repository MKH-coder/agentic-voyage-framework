# Directive: Example Workflow

## Objective
Demonstrate how an AI agent or contributor should execute a task following the 3-layer architecture.

## Inputs
- `.env` file populated according to `.env.example`.

## Execution Procedure

1. **Verify Environment**:
   Run the environment validation script:
   ```bash
   python3 execution/verify_env.py
   ```

2. **Run Execution Script**:
   Execute the target deterministic script from `execution/`:
   ```bash
   # Add your script invocation here
   ```

3. **Verify Result**:
   Confirm that outputs match expected test cases or database states.

## Edge Cases & Notes
- Document any API rate limits or timing constraints discovered here.
