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
├── tc001/
│   ├── prompt.md
│   ├── test.json
│   └── changelog.md
│
├── tc002/
│   ├── prompt.md
│   ├── test.json
│   └── changelog.md
│
├── tc003/
│   ├── prompt.md
│   ├── test.json
│   └── changelog.md
│
└── ...
```

---

# Purpose

Each **Test Case (TC)** represents one prompt debugging session.

A test case contains:

* **prompt.md** — The current version of the prompt being tested.
* **test.json** — The latest DivKit JSON generated from the prompt.
* **changelog.md** — A record of issues found, prompt improvements, and iteration history.

Each test case is independent, making it easy to compare different prompts, revisit previous work, and track progress over time.

---

# Workflow

1. Open the test case folder (e.g., `tc001`).
2. Review or update `prompt.md`.
3. Generate DivKit JSON using the prompt.
4. Save the generated output in `test.json`.
5. Render the JSON in DivKit.
6. Review the rendered UI for:

   * JSON validation errors
   * Rendering issues
   * Layout problems
   * Visual inconsistencies
   * Component misuse
   * Overall design quality
7. Identify the root cause of each issue.
8. Improve the prompt to prevent the issue from recurring.
9. Record all findings and prompt updates in `changelog.md`.
10. Repeat until the generated layout meets the expected quality.

---

# Goal

The purpose of this repository is **not** to manually fix generated JSON.

Instead, each iteration should improve the prompt so that future generations naturally avoid previously discovered issues.

By continuously refining the prompt, the generation process becomes more reliable, consistent, and capable of producing high-quality DivKit layouts with minimal manual intervention.
