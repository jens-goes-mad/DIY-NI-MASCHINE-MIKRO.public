# documentation-github-page

Public build-log site for the DIY-NI-MASCHINE-MIKRO project -- turning a Native
Instruments Maschine Mikro MK3 into a plain, class-compliant MIDI controller. Built with
[Hugo](https://gohugo.io/) and the [Stack theme](https://github.com/CaiJimmy/hugo-theme-stack),
deployed to GitHub Pages via `../.github/workflows/hugo.yml` on every push to `main` that
touches this directory.

Baseline copied from `DIY-MIDI-METRONOME.public` (2026-10-03). Shared `layouts/` and
`assets/icons/` come from
[DIY-HUGO-SCAFFOLD.public](https://github.com/jens-goes-mad/DIY-HUGO-SCAFFOLD.public) as a
Hugo Module -- see `config/_default/module.toml` for the (counterintuitive) import order,
and that repo's README for what's shared vs. per-site.

## Local development

Hugo (extended) and Go are pinned into the bundled Docker image, so no local install is
needed:

```bash
docker compose up
```

Then open http://localhost:1313/DIY-NI-MASCHINE-MIKRO.public/ (note the subpath --
`docker-compose.yml` overrides `--baseURL` so local links resolve like in production).

## Structure

- `content/overview` -- project intro
- `content/protocol` -- the device protocol at a glance (details stay in the private source repo)
- `content/bridge` -- planned bridge hardware and software
- `content/timeline` -- build log
- `content/me` -- author bio + legal notice (Impressum/Datenschutzerklärung)
