# GitHub Classroom — Student Workflow Guide (CS L300)

> **Purpose:** This short guide shows you how to accept an assignment, pull the starter code, work in a branch, push your changes, open a Pull Request (PR), and respond to feedback. Keep this open while you work.

**Weekly rhythm**
- **Accept link** in LMS → Classroom creates **your private repo**.
- **Work in a branch** → commit small and often.
- **Push** → CI/autograding runs.
- **Open a PR** → fill checklist → request review.
- **Fix feedback** → merge when approved & checks pass.
- **Deadline:** Mondays **08:00 (Africa/Accra)** unless your assignment says otherwise.
- **Cutoff:** After the cutoff, the repo becomes read-only (ask for extension if needed).

---

## 0) Prerequisites

- A GitHub account (use your school email).
- Git installed: https://git-scm.com/downloads  
- VS Code (recommended): https://code.visualstudio.com/  
- Optional: **Codespaces** (one-click dev environment in your browser).

> Tip: If your laptop struggles with installs, use **Codespaces** (open the repo in GitHub → **Code** → **Codespaces** → **Create codespace on main**).

---

## 1) Accept the assignment

1. Click the **invite link** in the LMS.  
2. Classroom creates **a private repository for you** from the template.  
3. You’ll see a screen with your repo name, e.g. `w01-semantic-web-<username>`.

> If you get a “permission” error, make sure you’re signed into the **correct GitHub account** and that you clicked the link from the LMS (not a forwarded link).

---

## 2) Get the code on your machine

### Option A — Local (recommended if your machine is set up)
```bash
# Clone your repo (from the green "Code" button → HTTPS)
git clone https://github.com/<org>/<your-repo>.git
cd <your-repo>

# Set your identity (one-time per machine)
git config user.name "Your Name"
git config user.email "you@school.edu"
```

### Option B — Codespaces (no local setup)
- On GitHub, open **your repo** → **Code** → **Codespaces** → **Create codespace on main**.  
- VS Code opens in your browser. Terminal is built-in.

---

## 3) Create your work branch

Always work in a feature branch—**never** commit directly to `main`.

```bash
git checkout -b feat/<your-name>-w##-<short-task>
# example: feat/ama-w01-forms
```

> Branch naming for teams (group assignments):  
> `team-<teamname>/feat/<member>-<task>`  
> Example: `team-alpha/feat/ama-form-validation`

---

## 4) Build the assignment

- Read the **README** acceptance criteria.
- Keep commits **small** and **frequent**. Use meaningful messages:
```bash
git add .
git commit -m "feat: add semantic layout and primary nav"
git commit -m "fix: label association for email input"
git commit -m "docs: update README with reflection"
```

- Push your branch:
```bash
git push -u origin HEAD
```

> Every push triggers **autograding/CI**. Green checks ✅ mean tests passed; red ❌ means you need fixes. Click the “Checks” tab on your PR to see logs.

---

## 5) Open a Pull Request (PR)

1. On GitHub, you’ll see a **Compare & pull request** banner → click it.  
2. Title: `W##: <short description>` (e.g., `W01: Semantic HTML & form`)  
3. Description: paste the **PR Checklist** from the README and tick items.  
4. **Assign a reviewer** (your lecturer/TA or teammate for group work).  
5. Submit the PR.

> If “main is protected”, that’s expected—**everything merges via PR**.

---

## 6) Respond to feedback & fix tests

- Reviewer leaves inline comments on your PR.  
- Make changes locally (or in Codespaces), commit, and push again.  
- **Don’t close the PR**—pushes will update it automatically.  
- When all checks are green and the reviewer approves, **merge** the PR.

> If you can’t merge due to conflicts:  
> - Click **Resolve conflicts** (on GitHub) **or** pull latest and merge locally:
>   ```bash
>   git fetch origin
>   git checkout main
>   git pull
>   git checkout feat/<your-branch>
>   git merge main
>   # fix files, then:
>   git add .
>   git commit -m "chore: resolve merge conflicts"
>   git push
>   ```

---

## 7) Keep your local repo in sync (pull updates)

When your PR is merged, update your local `main`:
```bash
git checkout main
git pull
```

If the lecturer posts **starter fixes** after you cloned (rare), add an `upstream` remote pointing to the official template repo and pull from it:
```bash
git remote add upstream https://github.com/<org>/<assignment-template>.git
git fetch upstream
git checkout main
git merge upstream/main   # or: git rebase upstream/main
```

> Only do this if your lecturer announces template updates.

---

## 8) Group assignments (when enabled)

- Accept the **Group assignment** link and **join or create a team** (e.g., `team-alpha`).  
- The team gets **one shared repo**. Use branch prefixes to stay organized:
  - `team-alpha/feat/ama-form`
  - `team-alpha/fix/kweku-api-tests`
- Agree on roles each week (Frontend, Backend, QA, DevOps, Docs/PM).  
- Use the repo’s **Project board** (To do / In progress / In review / Done).  
- **One Issue → one PR.** Every change should reference an issue.

---

## 9) Deadlines, cutoff & extensions

- **Deadline:** Mondays 08:00 (Africa/Accra) unless stated otherwise.  
- **Cutoff:** After the cutoff time, your repo turns **read-only**.  
- Need more time? **Ask early**; extensions are at the lecturer’s discretion.

---

## 10) What not to do

- Don’t push to `main` directly.  
- Don’t work outside the specified folders (tests may rely on paths).  
- Don’t paste code from AI or the web without understanding/citation.  
- Don’t share your private repo publicly.

---

## 11) Quick troubleshooting

- **“Permission denied” when cloning** → Accept the assignment link first; verify you’re logged into the correct GitHub account.  
- **“Could not read from remote repository”** → Check repo URL, access rights, or network/VPN.  
- **Can’t push** → You’re on `main` (protected). Create a feature branch and push that.  
- **Checks failing** → Open the **Checks** tab to read autograder logs; fix tests or code style issues.  
- **Conflicts** → Pull latest `main` and merge into your branch (see step 6).  
- **CI didn’t run** → Make sure you pushed to **your** repo, not a local-only branch.

---

## 12) Example PR template (copy into your PR)

```md
### Summary
Short description of what you built/changed.

### Checklist
- [ ] All Acceptance Criteria met
- [ ] Lint/format pass (if applicable)
- [ ] Tests added/updated (if applicable)
- [ ] Screenshots or short GIF (UI work)
- [ ] README updated (reflection / setup notes)

### Notes
Any known issues, trade-offs, or follow-up tasks.
```

---

## 13) Example commit messages

```
feat: add semantic layout and primary nav
feat: implement contact form with labels and validation
fix: correct label-for association for email input
style: improve focus outline visibility
docs: add reflection to README
chore: update project structure and .gitignore
```

---

## 14) Code of conduct (short)

- Be respectful in issues, PRs, and reviews.  
- Reviews focus on code and learning, not the person.  
- Ask questions early; help your teammates succeed.

---

## 15) Need help?

- Post a question in the course forum/LMS thread.  
- Tag your lecturer/TA on the PR with a clear, minimal example.  
- If it’s private (grades/account), email the lecturer.


**You’ve got this. Build small, commit often, and keep the PR conversation active.**
