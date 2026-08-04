# CampusTrading Documentation

Source repository for the CampusTrading Supply & Demand documentation.

The documentation is written in Markdown, built with Material for MkDocs, and published through GitHub Pages.

## Local preview

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install -r requirements.txt
mkdocs serve
```

Open `http://127.0.0.1:8000` in a browser.

## Production build

```bash
mkdocs build --strict
```

