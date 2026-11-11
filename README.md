# ROCm Repo Repair — Multi-Agent AST Fault Localization & Test-Verified Code Repair

Built for **AMD AI League Match 5: AI-Powered Code Repository Repair (`+2,100 XP`)** by **Tusiime Eriya** (`ERIX-12`) on `rocm/pytorch`.

## Architecture on AMD Instinct MI300X (`192 GB HBM3`)
1. **Agent 1 — AST & Traceback Fault Localizer:** Parses failing pytest/unittest tracebacks and builds an Abstract Syntax Tree (AST) call-graph to isolate the exact defective function and line range.
2. **Agent 2 — BF16 Patch Synthesizer (`Qwen/Qwen2.5-Coder-7B-Instruct` on ROCm):** Generates minimal unified diff patches (`git diff`) targeting the root defect without breaking adjacent interfaces.
3. **Agent 3 — Sandbox Test Gatekeeper:** Applies each candidate diff in an isolated working tree and runs the repository test suite, emitting only 100% test-verified fixes to `/app/output/<query-id>_output.json`.
