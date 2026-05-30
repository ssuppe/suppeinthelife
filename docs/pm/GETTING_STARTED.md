Here is the complete, end-to-end prompt document. It is written as a strict execution playbook for an AI coding agent. It instructs the agent to handle all the local architecture and code, and then explicitly tells the agent to pause and hand the manual infrastructure steps (DNS, GitHub UI) back to you at the exact right moment.

Copy everything below this line and paste it directly into your AI agent:

---

```markdown
# E2E Implementation Plan: Suppe In The Life (Portfolio & Blog)

**System Directive for AI Agent:**
You are acting as a senior DevOps and Frontend engineer assisting Steve, an L7 Product Manager. Your objective is to scaffold a minimalist Hugo static site using the `hugo-bearblog` theme, configure an automated GitOps pipeline for GitHub Pages, and hand off manual UI/infrastructure tasks back to the user when appropriate. 

Execute this plan sequentially. Do not hallucinate dependencies. Keep the configuration as minimal as possible.

## Phase 1: Variable Collection
**Agent Action:** Pause and ask the user to provide the following variables before proceeding:
1. GitHub Username
2. LinkedIn Username
3. The URL of the newly created empty GitHub repository (e.g., `https://github.com/USERNAME/suppeinthelife.git`)

## Phase 2: Local Architecture & Theming
**Agent Action:** Once variables are provided, execute the following CLI commands locally:
1. Initialize a new Hugo site: `hugo new site suppeinthelife`
2. Enter directory: `cd suppeinthelife`
3. Initialize git: `git init`
4. Add the submodule: `git submodule add https://github.com/janraasch/hugo-bearblog.git themes/hugo-bearblog`
5. Add the remote origin using the URL provided by the user.

## Phase 3: Configuration & Analytics
**Agent Action:** Overwrite `hugo.toml` with the following minimalist configuration. 

```toml
baseURL = "[https://suppeinthelife.com/](https://suppeinthelife.com/)"
title = "Steve Suppe"
theme = "hugo-bearblog"
languageCode = "en-us"

[params]
  author = "Steve Suppe"
  description = "L7 Product Manager specializing in AI evaluations and healthcare tech."

# Top Navigation
[[menus.main]]
  name = "Blog"
  url = "/posts/"
  weight = 1
[[menus.main]]
  name = "CV"
  url = "/resume.pdf"
  weight = 2
[[menus.main]]
  name = "GitHub"
  url = "[https://github.com/YOUR_GITHUB_USERNAME](https://github.com/YOUR_GITHUB_USERNAME)"
  weight = 3
[[menus.main]]
  name = "LinkedIn"
  url = "[https://linkedin.com/in/YOUR_LINKEDIN_USERNAME](https://linkedin.com/in/YOUR_LINKEDIN_USERNAME)"
  weight = 4

```

*(Agent: Ensure placeholders are swapped with Phase 1 variables).*

**Analytics Injection:**
Create the file `layouts/partials/head_custom.html` (or Bear's equivalent for injecting into the `<head>`) and add this exact script:
`<script data-goatcounter="https://suppeinthelife.goatcounter.com/count" async src="//gc.zgo.at/count.js"></script>`

## Phase 4: Content Modeling

**Agent Action:** Create the following files.

1. `content/_index.md` (The Homepage):

```markdown
---
title: "Home"
---
Hi, I'm Steve.

I'm an L7 Product Manager specializing in AI evaluations and healthcare tech. This site is a log of my architectures, prototypes, and side projects.

## Projects

* **Project Name 1** — A 1-sentence description of what this does and why it matters. 
  [View on GitHub](#) • [Read the Dev Log](/tags/project1/)
* **Project Name 2** — A 1-sentence description of what this does and why it matters. 
  [View on GitHub](#) • [Read the Dev Log](/tags/project2/)
* **Project Name 3** — A 1-sentence description of what this does and why it matters. 
  [View on GitHub](#) • [Read the Dev Log](/tags/project3/)

---
## Recent Posts

```

2. `content/posts/my-first-post.md`: Create a sample post with frontmatter containing `title`, `date`, and `tags: ["project1", "healthcare-ai"]`.
3. `static/resume.pdf`: Create a blank placeholder file so the CV link resolves.

## Phase 5: CI/CD Pipeline

**Agent Action:** Create `.github/workflows/hugo.yml` with the standard GitHub Actions configuration to build and deploy Hugo to GitHub Pages. It MUST include `submodules: true` in the checkout step to pull the Bear theme.

## Phase 6: Push & Handoff

**Agent Action:**

1. Commit all files: `git add . && git commit -m "Initial launch architecture"`
2. Push to the main branch: `git push -u origin main`
3. **STOP EXECUTION AND PRINT THE FOLLOWING HANDOFF INSTRUCTIONS FOR STEVE:**

### 🛑 Human Handoff Required

Steve, the code is successfully pushed. Complete these final 3 steps in your browser to bring the site live:

**1. Configure GitHub Pages**

* Go to your repository on GitHub -> **Settings** -> **Pages**.
* Under "Build and deployment", change "Source" to **GitHub Actions**.

**2. Configure Porkbun DNS**

* Log into Porkbun and open DNS Management for `suppeinthelife.com`.
* Delete any default/parked records.
* Add 4 **A Records** (Leave Host blank) pointing to:
* `185.199.108.153`
* `185.199.109.153`
* `185.199.110.153`
* `185.199.111.153`


* Add 1 **CNAME Record** (Host: `www`) pointing to `YOUR_GITHUB_USERNAME.github.io`.

**3. Link Domain in GitHub**

* Go back to GitHub -> **Settings** -> **Pages**.
* In the "Custom domain" field, enter `suppeinthelife.com` and hit Save.
* Wait a few minutes, then refresh and check **Enforce HTTPS**.

Your automated pipeline is now live. Any Markdown file you add to `content/posts/` from your phone or laptop will auto-publish in seconds.

```

```
