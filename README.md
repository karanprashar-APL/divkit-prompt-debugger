# DivKit Prompt Debugger

A repository for debugging, testing, and refining DivKit generation prompts through iterative prompt engineering.

The objective is to improve prompt quality so that Large Language Models consistently generate valid, visually appealing, and production-ready DivKit JSON.

---

# Repository Structure

```text
divkit-prompt-debugger/
│
├── README.md
│
├── TC001/
│   ├── Prompt.md
│   ├── output.json
│   ├── __structure__.json
│   └── change_log.md
│
├── TC002/
│   ├── Prompt.md
│   ├── output.json
│   ├── __structure__.json
│   └── change_log.md
│
└── ...
```

---

# Purpose

Each **Test Case (TC)** represents one prompt debugging session.

A test case contains:

* **Prompt.md** — The current version of the prompt being tested.
* **output.json** — The latest DivKit JSON generated from the prompt.
* **__structure__.json** — The structure metadata emitted after the DivKit JSON (the `__STRUCTURE__` block).
* **change_log.md** — A record of issues found, prompt improvements, and iteration history.

Each test case is independent, making it easy to compare different prompts, revisit previous work, and track progress over time.

Test cases hold only these artifacts. Local tooling (renderers, preview servers, editor config, scratch drafts, image assets) is kept out of the repo — the value lives in the prompt and its documented iterations, not in the scaffolding used to test them.

---

# Workflow

1. Open the test case folder (e.g., `TC001`).
2. Review or update `Prompt.md`.
3. Generate DivKit JSON using the prompt.
4. Save the generated output in `output.json` and the structure metadata in `__structure__.json`.
5. Render the JSON in DivKit (at the target viewport, e.g. 1920×1080 for desktop web).
6. Review the rendered UI for:

   * JSON validation errors
   * Rendering issues
   * Layout problems
   * Visual inconsistencies
   * Component misuse
   * Overall design quality
7. Identify the root cause of each issue **in the prompt** (not just the output).
8. Improve the prompt to prevent the issue from recurring.
9. Record all findings and prompt updates in `change_log.md`.
10. Repeat until the generated layout meets the expected quality.

---

# Goal

The purpose of this repository is **not** to manually fix generated JSON.

Instead, each iteration should improve the prompt so that future generations naturally avoid previously discovered issues.

By continuously refining the prompt, the generation process becomes more reliable, consistent, and capable of producing high-quality DivKit layouts with minimal manual intervention.
