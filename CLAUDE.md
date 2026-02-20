# ancc-site

Single-page static site for ancc.dev — Agent-Native CLI Convention.

## What this is

A spec page describing the ANCC methodology: how to build CLI tools that agents can discover, install, configure, and compose without plugins, SDKs, or registries.

## What this is NOT

- Not a framework or library
- Not a registry or marketplace
- Not documentation for a specific tool
- Not a blog or CMS

## Architecture

```
index.html    -- single-page site with inline CSS (same pattern as attentionfirst.dev)
CNAME         -- ancc.dev domain
docs/
  work-orders.md  -- build WOs
```

## Design

- Dark theme matching attentionfirst.dev (#0E1116 background)
- Centered column, max-width 640px
- No JavaScript except optional domain redirect
- No build tools, no bundler, no framework
- Deploy via GitHub Pages from root

## Style reference

Follow the exact CSS patterns from attentionfirst.dev:
- Font: system font stack
- Colors: #CDD6E0 text, #7C8590 secondary, #3B414A borders
- Links: subtle underline, hover effect
- Sections: h2 with section-intro paragraph

## Content structure

1. Title + tagline
2. What ANCC is (brief philosophy)
3. The 6 requirements (single binary, deterministic, structured output, bounded job, SKILL.md, init command)
4. SKILL.md format
5. Example tools (chainwatch, noisepan, entropia)
6. Observed pattern (agent self-install narrative)
7. Links (GitHub)
