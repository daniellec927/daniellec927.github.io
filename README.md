# daniellec927.github.io

My personal portfolio site — built with [Jekyll](https://jekyllrb.com/) and the
[al-folio](https://github.com/alshedivat/al-folio) theme (v0.16.3), deployed on GitHub Pages.

## Run it locally

```bash
docker compose up          # then open http://localhost:8080
```

Edits to content reload automatically. Changes to `_config.yml` need a restart.

## Where things live

| I want to change… | Edit |
|---|---|
| My name, site title, URL, feature toggles | `_config.yml` |
| Homepage bio and photo | `_pages/about.md`, `assets/img/prof_pic.jpg` |
| Portfolio items | `_projects/*.md` |
| Blog posts | `_posts/YYYY-MM-DD-title.md` |
| CV contents | `_data/cv.yml` |
| Social links | `_data/socials.yml` |
| Featured GitHub repos | `_data/repositories.yml` |
| Homepage "news" blurbs | `_news/*.md` |
| Accent colour | `_sass/_variables.scss` (`$blue-color`, `$blue-color-light`) |

Anything still marked `TODO` is a placeholder waiting to be filled in.
