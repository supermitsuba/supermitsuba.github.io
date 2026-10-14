# portfolio-site

Source for **supermitsuba.github.io** — a modern-classic portfolio of diagram-forward
case studies.

## How it ships

Authored here in **Gitea** → push-mirrored to **GitHub**
(`supermitsuba/supermitsuba.github.io`) → served by **GitHub Pages**.

This flow is itself a specimen of the GitOps case study: cloud-style delivery driven from
self-hosted infrastructure.

## Structure

- `index.html` — the single-page shell: positioning header, Work (case studies), About,
  résumé link.
- `assets/style.css` — hand-tuned CSS. Classic/timeless, responsive, light + dark. No
  framework.

Static by design; no build step yet. An SSG is introduced only if content duplication
across case studies warrants it.
