# DivKit Prompt Debugger

This repo (short for "repository" — basically a project folder that Git, a version-tracking tool, keeps a history of) is where we test and improve a prompt (the instructions we give an AI model to generate something).

The prompt's job is to make an AI generate DivKit JSON (DivKit is a UI framework — a toolkit for building app/website screens — and JSON is a text format for structured data, like a list of settings and content). Our goal is to make the prompt good enough that the AI always produces JSON that is valid (no syntax errors), looks good, and is ready to actually use — without us having to fix it by hand every time.

---

# Repository Structure

No subfolders. Everything lives flat in the main project folder:

```text
divkit-prompt-debugger/
│
├── README.md            (this file — explains the project)
├── Prompt.md            (the current version of the prompt we're testing)
├── output.json          (the latest DivKit JSON the prompt generated)
├── __structure__.json   (extra metadata/info the AI outputs alongside the JSON)
└── change_log.md        (a running log of every issue found and every prompt fix)
```

Since we're not using separate folders per test, **Git's history is what tracks our progress over time.** Every time you improve the prompt, you make a commit (a saved snapshot of your changes, with a message describing what changed). If you ever want to see an older version of the prompt or the JSON it produced, you look back through the commit history instead of digging through old folders.

---

# What Belongs in This Repo (and What Doesn't)

Keep this repo to exactly the 5 files above. Nothing else.

**Never commit (meaning: never save into Git) these kinds of things:**
- Local preview tools you use just to view/render the JSON on your own computer (e.g. a `preview.html` file, a test server)
- Editor or tool settings folders (e.g. `.claude/`, `.vscode/`) — these are personal to your machine, not part of the actual project
- Image files, logos, or anything downloaded just for testing
- Random extra files sitting loose in the folder (e.g. a second copy like `new.md`)
- JSON files with big embedded images (this means a picture converted into a giant block of text and pasted directly inside the JSON, called base64 encoding) — this bloats (makes unnecessarily large) the file size and makes it hard to review changes. Use real image links instead (like from `picsum.photos` or `placehold.co`, which are free services that give you placeholder/test images via a URL)

**If you're using a local tool to preview/render the JSON while debugging, keep it outside this repo entirely.** Or, add its name to a `.gitignore` file — a special file that tells Git "never track this, even if it shows up in the folder."

---

# Purpose

This repo tracks **one prompt at a time, as it evolves.**

* **Prompt.md** holds the current instructions we're giving the AI.
* **output.json** holds the most recent DivKit JSON the AI generated from that prompt.
* **__structure__.json** holds extra structured info the AI is supposed to output after the main JSON (this is called the `__STRUCTURE__` block in our setup).
* **change_log.md** holds a written history: what went wrong, why it went wrong (traced back to the exact part of the prompt causing it), and exactly what we changed in the prompt to fix it.

Instead of separate test folders, each round of testing just **overwrites** `output.json` and `__structure__.json` with the newest result, and adds a new entry to `change_log.md`. The old versions still exist — you can always find them in Git's commit history.

---

# Workflow (the step-by-step process to follow)

1. Open `Prompt.md` and review it.
2. Run the prompt through the AI to generate new DivKit JSON.
3. Save that output into `output.json`, and save the extra metadata block into `__structure__.json`.
4. Render (visually display) the JSON using a DivKit viewer — at a normal desktop screen size, like 1920×1080 pixels — using a tool that stays outside this repo.
5. Look at the rendered result and check for:
   * JSON errors (the file being broken or invalid)
   * Rendering issues (things not showing up correctly)
   * Layout problems (spacing, sizing, alignment being wrong)
   * Visual inconsistencies (things looking mismatched or off-brand)
   * Misused components (using the wrong building block for the job)
   * Overall design quality
6. For every issue you find, trace it back to the **exact part of the prompt** causing it — not just what looks wrong in the output, but why the instructions led the AI to produce that.
7. Edit the prompt to fix the root cause. Try to make the fix general (works across different screen sizes and setups) instead of hardcoded (locked to one specific number or one specific test case) — since hardcoded fixes tend to fix the current problem but break something else later.
8. Write down what happened in `change_log.md`: the issue, the root cause, and the exact before/after change you made to the prompt.
9. Commit your changes to Git with a clear message describing what you fixed.
10. Repeat until the output consistently looks the way you want.

---

# Goal

We are not trying to manually patch broken JSON output every time.

We're trying to make the **prompt itself** smart enough that future AI-generated JSON avoids problems we've already run into. Every fix should teach the prompt something general, so the same mistake doesn't come back next time.

Keeping the repo lean (containing only the 5 core files, no clutter) makes it much easier to see, at a glance, exactly how the prompt has evolved and why.