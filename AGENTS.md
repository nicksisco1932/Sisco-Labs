# AGENTS.md — Sisco-Labs Static Site Governance

## Mission
Maintain a disciplined, minimal, high-credibility GitHub Pages site.
Optimize clarity, consistency, and capture reliability without introducing complexity.

## Core Principles
1. Minimal surface area change.
2. No premature optimization.
3. No new frameworks.
4. No paid services without explicit approval.
5. Preserve existing CSS and layout structure.
6. Scientific, restrained language only.
7. Every change must be reviewable and reversible.

## Structural Safeguards
- Do NOT introduce JS-based shared layout injection unless explicitly requested.
- Do NOT refactor global CSS.
- Do NOT modify more files than required.
- Do NOT alter directory structure.
- Do NOT introduce build tooling (npm, bundlers, preprocessors).
- Do NOT introduce analytics or trackers without approval.

## Header/Footer Contract
These pages must share IDENTICAL header + footer markup:
- index.html
- about.html
- programs.html
- blog.html
- blog-1.html
- blog-2.html
- blog-3.html
- contact.html

Nav labels (exact order):
- Home → index.html
- About → about.html
- Programs → programs.html
- Journal → blog.html
- Contact → contact.html
- Early Access → index.html#early-access

## Early Access Contract
index.html must:
- Validate email client-side.
- Show visible status messaging.
- Attempt Formspree JSON submission.
- Provide mailto fallback.
- Preserve id="early-access" anchor.
- Avoid marketing hype language.

## Git Discipline
Every change must:
1. Show `git status`.
2. Stage only relevant files.
3. Use concise imperative commit messages.
4. Output "ready to push after review".
Never push automatically.

## Output Discipline
- Prefer small commits.
- Prefer unified diffs.
- Avoid speculative enhancements.
- If uncertain, STOP and ask.
