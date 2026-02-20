# Work Orders — ancc-site

## Roadmap

- [ ] WO-A01: Build single-page site
- [ ] WO-A02: GitHub Pages deployment
- [ ] WO-A03: Domain setup (ancc.dev)

---

### WO-A01: Build single-page site

**Status:** `[ ]` planned
**Priority:** high — this is the only deliverable

### Summary

Create `index.html` for ancc.dev — a single-page spec describing the Agent-Native CLI Convention. Same visual pattern as attentionfirst.dev (dark theme, centered column, inline CSS, no JS framework).

### Content sections

1. **Header**: "ANCC" title, tagline: "Agent-Native CLI Convention. Build tools agents can use without plugins."

2. **Philosophy** (2-3 short paragraphs):
   - Agents don't need plugins. They need well-built Unix tools.
   - ML compensates for lack of structure. Deterministic tools don't need ML.
   - Build small. Ship small. Compose like pipes.

3. **The Convention** — 6 numbered requirements, each with a short heading and 2-3 sentence description:
   - Single binary, zero runtime deps
   - Deterministic behavior
   - Structured output (`--format json`)
   - One bounded job
   - SKILL.md at repo root
   - Init command

4. **SKILL.md** — what it is, YAML frontmatter format, key sections (install, commands, flags, JSON output, parsing examples, what it does NOT do, exit codes). Show a minimal example.

5. **Observed in the wild** — brief narrative: an autonomous agent discovered CLI tools from conversation, installed via Homebrew, configured via init + config files, composed into a pipeline, set up cron. No plugin framework. No SDK. No registry. Just CLI tools + SKILL.md.

6. **Example tools** — list with links:
   - [chainwatch](https://github.com/ppiankov/chainwatch) — AI agent execution control plane
   - [noisepan](https://github.com/ppiankov/noisepan) — signal extractor for noisy information streams
   - [entropia](https://github.com/ppiankov/entropia) — source credibility verifier

7. **Principle** — closing statement. Same tone as attentionfirst.dev's principle section. Tools present evidence and let you decide — mirrors, not oracles. The right substrate for agents is the same substrate that works for humans: the terminal.

8. **Footer**: GitHub link

### Design constraints

- Copy the exact CSS from attentionfirst.dev (see `/Users/pashah/dev/ppiankov-github/attentionfirst-site/index.html`)
- Same dark theme: `#0E1116` bg, `#CDD6E0` text, `#7C8590` secondary
- Same layout: max-width 640px, centered, system font stack
- No JavaScript (except optional domain redirect)
- No build tools, no framework
- Single `index.html` file with inline CSS

### Scope

| File | Change |
|------|--------|
| `index.html` | Create: full page with all sections |

### Acceptance criteria

- [ ] `index.html` renders correctly in browser
- [ ] All 6 ANCC requirements are clearly described
- [ ] SKILL.md format is explained with example
- [ ] Example tools link to correct GitHub repos
- [ ] Visual style matches attentionfirst.dev
- [ ] No JavaScript dependencies
- [ ] Page validates as valid HTML5

### Notes

- Do NOT add a build system or CSS framework
- Do NOT create multiple pages — single page only
- Do NOT add analytics, tracking, or third-party scripts
- Keep text concise — this is a spec, not a blog post
- The "observed in the wild" section should be brief (3-4 sentences), not a full case study

---

### WO-A02: GitHub Pages deployment

**Status:** `[ ]` planned — depends on WO-A01
**Priority:** medium — needed after site is built

### Summary

Initialize git repo, push to GitHub, enable GitHub Pages.

### Scope

| File | Change |
|------|--------|
| `.gitignore` | Create: standard static site ignores |

### Steps

1. `git init && git add -A && git commit -m "feat: initial ancc.dev site"`
2. `gh repo create ppiankov/ancc-site --public --description "ANCC — Agent-Native CLI Convention" --source . --push`
3. Enable GitHub Pages: `gh api repos/ppiankov/ancc-site/pages -X POST -f source.branch=main -f source.path=/`

### Acceptance criteria

- [ ] Repo exists at github.com/ppiankov/ancc-site
- [ ] GitHub Pages is enabled
- [ ] Site is accessible at ppiankov.github.io/ancc-site (before custom domain)

---

### WO-A03: Domain setup (ancc.dev)

**Status:** `[ ]` planned — depends on WO-A02
**Priority:** low — manual step, requires domain purchase

### Summary

Configure ancc.dev domain to point to GitHub Pages. This is a manual step — the operator must purchase the domain and configure DNS.

### DNS records

```
A     @    185.199.108.153
A     @    185.199.109.153
A     @    185.199.110.153
A     @    185.199.111.153
CNAME www  ppiankov.github.io
```

### Acceptance criteria

- [ ] ancc.dev resolves to the site
- [ ] HTTPS works via GitHub Pages
- [ ] CNAME file is in repo root
