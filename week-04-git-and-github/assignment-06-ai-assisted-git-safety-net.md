# Assignment 6 — Building an AI-Assisted Git Safety Net (PR Ready Check)

Part of the DevOps Micro Internship (DMI) Cohort 3 with Agentic AI

---

## Purpose

In Week 2 you built Claude Code hooks that block a dangerous action *before* it happens (`PreToolUse`), and a restricted skill that could look but not touch (`allowed-tools` without `Write`). In this assignment you will discover that Git has the exact same idea, decades older: a **pre-commit hook** that blocks a commit before it's created.

You will build both halves of a real "PR Ready" workflow:

1. A **Git hook that follows fixed rules** — scans staged changes for hardcoded secrets and oversized files and refuses the commit. No AI involved, no guessing, just a rule that gives the same answer every time.
2. A **restricted Claude Code skill** (`/pr-ready`) that reads your staged diff and drafts a Pull Request title, description, and a short list of things worth a second look — the kind of judgment a fixed rule can't make (mixed changes, missing context, unclear intent). The skill never commits, pushes, or opens the PR. You do that yourself, using its draft as a starting point.

This mirrors the Agentic Loop from Week 3's Linux triage assignment: **Gather → Analyze → Human Act → Verify**. The hook and the skill both gather and analyze; only you act.

---

# Task 0 — Confirm Your Fork and Create a Feature Branch

## Goal

Confirm you are working in your own fork, then create a dedicated branch for this assignment.

### Evidence

#### Screenshot 1 — Output of git remote -v and git branch showing the new branch

![init2](screenshots/branch1.jpg)

---

### Notes

**1. Why create a dedicated branch instead of doing this work on main?**

Its easy for tracking the changes if we commit the changes in a branch rather than main.It provides isolation to the main content.

---

# Task 1 — Stage a Change With Realistic Risk

## Goal

On your own fork of this repository (the one you've been submitting your DMI work in since onboarding), create a new branch and stage a change that a real reviewer should catch: a hardcoded-looking secret and a leftover debug statement.

### Evidence

#### Screenshot 1 — Output of  `git status` showing the staged file on feature/ai-pr-ready

![init2](screenshots/status6.jpg)

---

### Notes

**1. Why does this assignment use an obviously fake key instead of a real one?**

The assignment uses an obviously fake key to safely demonstrate how secret detection works without exposing any real credentials.

---

# Task 2 — Write a Real Git Pre-Commit Hook

## Goal

Create a tracked, shareable pre-commit hook that blocks a commit containing secret-like patterns or files over 1MB.

### Evidence

#### Screenshot 2 — `hooks/pre-commit` open in VS Code showing the full script

![init2](screenshots/hooks.jpg)

---

#### Screenshot 3 — Output of `git config core.hooksPath` confirming it points to `hooks`

![init2](screenshots/hook.jpg)

---

### Notes

**1. Why is `hooks/pre-commit` tracked in the repo instead of living only in `.git/hooks/`?**

hooks/pre-commit is tracked in the repository so it can be shared with everyone working on the project. Files inside .git/hooks/ are local to each developer and are not version-controlled, so other team members would not receive them.

---

**2. Compare this to `PreToolUse` from Week 2 Assignment 6. What does each one intercept, and what do they have in common?**

Both act as preventive checkpoints that stop problems early, enforce consistent rules, and improve safety before an action is completed.

---

# Task 3 — Prove the Hook Blocks the Risky Commit

## Goal

Attempt to commit the staged file from Task 1 and show the hook rejecting it.

### Evidence

#### Screenshot 4 — Terminal showing `git commit` rejected with the hook's "BLOCKED" message naming the exact file

![init2](screenshots/blocked.jpg)

---

### Notes

**1. Which line in `hooks/pre-commit` matched your fake key, and why did it match?**

The line containing the regular expression that checks for AWS Access Key IDs matched my fake key. 

---

**2. Could this hook have caught a poorly-named variable that stores a secret without the `AKIA` prefix? What does that tell you about the limits of a fixed rule like this?**

No. This hook would not catch it because it only looks for specific patterns, like keys that start with AKIA. If a secret is stored in a variable with a different format, the hook may miss it.

---

# Task 4 — Build the `/pr-ready` Skill

## Goal

Create a manually invoked Claude Code skill that reads your staged changes and produces a PR-readiness report and a draft PR description — without writing, committing, or pushing anything itself.

### Evidence

#### Screenshot 5 — `SKILL.md` frontmatter showing `allowed-tools: Bash, Read, Grep` (no `Write`) and `disable-model-invocation: true`

![init2](screenshots/skill.jpg)

---

#### Screenshot 6 — `/pr-ready` output while the risky file is still staged, showing it flagged the secret and/or debug statement

![init2](screenshots/pre-ready2.jpg)
![init2](screenshots/pre-ready1.jpg)
![init2](screenshots/pre-ready.jpg)

---

### Notes

**1. Why does `/pr-ready` have `Bash` and `Read` but not `Write`?**
/pr-ready has Bash and Read permissions because it needs to read the project files and run Git commands to review the changes. It does not have Write permission because it should not change or edit the code automatically.

---

**2. The pre-commit hook and `/pr-ready` both looked at the same staged diff. Did they flag the same things? What did one catch that the other didn't?**

No, they did not flag the same things. The pre-commit hook checked for fixed rules, such as detecting a fake secret key, and blocked the commit when the rule was violated. /pr-ready reviewed the staged changes, summarized what was changed, and suggested improvements for the Pull Request. The pre-commit hook enforced rules, while /pr-ready provided helpful review and guidance

---

# Task 5 — Fix the Issues and Re-Verify

## Goal

Remove the secret and debug statement, then prove both gates now pass clean.

### Evidence

#### Screenshot 7 — `git commit` succeeding after the fix (no BLOCKED message)

![init2](screenshots/commit6.jpg)

---

#### Screenshot 8 — Second `/pr-ready` run showing a clean risk report and a drafted PR title + description

![init2](screenshots/pr3.jpg)

---

### Notes

**1. What exactly did you change to satisfy the pre-commit hook?**

I removed the fake AWS access key from the file so it no longer matched the secret detection rule.

---

# Task 6 — Push and Open a Pull Request Using the AI Draft

## Goal

Push your branch and open a real Pull Request, using `/pr-ready`'s drafted title and description as your starting point — read it critically and edit before you use it.

**Important:** Open this Pull Request with base repository set to **your own fork** — not the shared upstream `pravinmishraaws/devops-micro-internship-pravinmishra` repository. This assignment's hook and skill files are your own practice work, not a change meant for the shared class repo.

### Evidence

#### Screenshot 9 — Your Pull Request showing the base repository is your own fork, plus the title and description, with the `/pr-ready` draft visible for comparison (paste it in the PR conversation or your notes below)

![init2](screenshots/pr4.jpg)

---

#### PR Link

`https://github.com/pravinmishraaws/devops-micro-internship-interviews/pull/396`

---

### Notes

**1. What, if anything, did you edit in the AI's drafted PR description before using it? Why?**

This is part of human action. AI based draft needs to be carefully checked with human intervention.

---

**2. If you had blindly copy-pasted the AI's draft without reading it, what could go wrong?**

Blindly copy the AI based draft could lead to reject the PR request.

---

**3. Why does this PR need to target your own fork instead of the shared upstream repository?**

The pull request should be created from my fork because I don't have direct write access to the shared upstream repository. Using a fork allows me to work safely in my own repository and submit my changes for review without affecting the original project.

---

# Task 7 — Map the Workflow to the Agentic Loop

## Goal

Explain this assignment's workflow using the same Gather → Analyze → Human Act → Verify structure from Week 3.

### Notes

**1. Which step(s) represent Gather?**

Gather includes reviewing the repository, checking the modified files, reading the Git status, examining the commit history, and collecting the information needed to prepare the pull request.
---

**2. Which step(s) represent Analyze?**

Analyze includes using AI to review the changes, generate a draft pull request description, identify possible improvements, and verify that the summary accurately reflects the code changes.

---

**3. Which step is Human Act, and why must a human — not Claude — run `git commit`, `git push`, and open the PR?**

Human Act is when I execute git commit, git push, and create the Pull Request.It modify the repository and publish changes to GitHub, so they require human approval.

---

**4. Which step is Verify?**

Verify includes checking that the pre-commit hook passed successfully, confirming the commit was created, ensuring the branch was pushed correctly, reviewing the generated pull request, and verifying that the final PR accurately represents the intended changes.

---

**5. In one or two sentences: why do you need *both* the fixed-rule pre-commit hook and the AI skill? Isn't one enough?**
```
The pre-commit hook automatically enforces fixed rules, such as checking for secrets or formatting issues, before code is committed.
AI skills needed in feedback and improving the pull request description.
```
---

# Task 8 — LinkedIn Post

## Goal

Publish a LinkedIn post summarizing what you built and what you learned about combining fixed-rule safety checks with AI-assisted review.

### Evidence

#### LinkedIn Post URL

`https://www.linkedin.com/posts/blessy-s-06b379269_dmibypravinmishra-devops-agenticai-share-7486435308142673921-WdLz/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAEG6aBMB0zfBR9hQTWrl7i6zZCygzNyvY74`

---

## Key Learnings

Add 3-5 bullet points on what you learned this week.

-Implemented a fixed-rule pre-commit safety check
-Used AI to generate and improve a Pull Request description
-Reviewed and refined the AI-generated content before using it
-Committed, pushed my changes, and created a Pull Request using the standard GitHub workflow
-Learned how AI supports developers without replacing human responsibility

---

# Submission Instructions

- Ensure `hooks/pre-commit` and `.claude/skills/pr-ready/SKILL.md` are committed to your GitHub repository
- Add all required screenshots to your submission
- All written answers must be in your own words
- Do not use a real secret or credential anywhere in your submission — the fake key in Task 1 is intentional and must stay clearly fake
- Open your Pull Request against your own fork, not the shared upstream repository
- Push your final changes to your forked repository
- Include your PR link and LinkedIn post URL

---

## GitHub Repository URL

Paste your forked repository URL here:

`https://github.com/blessy2/devops-micro-internship-interviews.git`

---

# Completion Checklist

- [ ] Branch `feature/ai-pr-ready` created with a staged file containing a fake secret and a debug statement
- [ ] `hooks/pre-commit` created and tracked in the repo (not only in `.git/hooks/`)
- [ ] `core.hooksPath` configured to point at `hooks/`
- [ ] Pre-commit hook shown blocking the risky commit
- [ ] `.claude/skills/pr-ready/SKILL.md` created with correct `allowed-tools` (no `Write`) and `disable-model-invocation: true`
- [ ] `/pr-ready` run against the risky diff and shown flagging issues
- [ ] Risky file fixed; `git commit` succeeds cleanly
- [ ] `/pr-ready` re-run showing a clean report and drafted PR title/description
- [ ] Pull Request opened using the AI draft as a starting point, with your own fork as the base repository (not upstream), PR link included
- [ ] Agentic Loop mapping (Task 7) completed in your own words
- [ ] LinkedIn post published and URL submitted
- [ ] All required screenshots added
- [ ] GitHub repository URL provided

---

## 📌 About DMI & CloudAdvisory

DevOps Micro Internship (DMI) is a project-based DevOps program run by Pravin Mishra (The CloudAdvisory) focused on real-world execution, systems thinking, and career readiness.

It helps learners build strong DevOps foundations with hands-on experience.

---

## 📌 Resources

- 🌐 DMI Official Website: https://pravinmishra.com/dmi  
- 🎓 DevOps for Beginners (Udemy): https://www.udemy.com/course/devops-for-beginners-docker-k8s-cloud-cicd-4-projects/  
- 🎓 Agentic AI DevOps with Claude Code: https://www.udemy.com/course/ultimate-agentic-ai-devops-with-claude-code/  
- 🎓 DevOps with Claude Code: Terraform, EKS, ArgoCD & Helm: https://www.udemy.com/course/devops-with-claude-code-terraform-eks-argocd-helm/  
- ▶️ YouTube Playlist: https://www.youtube.com/playlist?list=PLFeSNDtI4Cho  
- 🔗 Pravin Mishra (LinkedIn): https://www.linkedin.com/in/pravin-mishra-aws-trainer/  
- 🏢 CloudAdvisory (LinkedIn): https://www.linkedin.com/company/thecloudadvisory/

---

*This submission is part of DevOps Micro Internship (DMI) Cohort 3 — Agentic AI Track.*
