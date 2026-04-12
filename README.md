# Pokémon Static Site Generator

A lightweight static site generator written in vanilla Python that reads Pokémon data from a SQLite database and generates clean, ready-to-deploy HTML pages for each Pokémon — no frameworks, no dependencies.

## Features

- **Static HTML Generation:** Generates individual web pages for each Pokémon from a SQLite database
- **Zero Dependencies:** Built entirely with vanilla Python and the standard library
- **SQLite Powered:** Reads Pokémon details like name, type, stats, abilities and more from a local SQLite database
- **Fast & Lightweight:** No server required — just open the generated HTML files in any browser
- **Easy to Deploy:** Output is plain HTML/CSS, deployable to GitHub Pages, Netlify, or any static host

## Requirements

- Python 3.x
- SQLite3 *(comes bundled with Python)*

No third-party packages required.

## Project Structure

```
Static-Site-Generator/
├── index.py            # Entry point — runs the generator
├── style.css           # Stylesheet for all generated pages
├── PokemonDB.db        # SQLite database with Pokémon data
├── PokemonDB.sqbpro    # DB browser project file
├── assets/             # Icons and UI assets used in generated pages
├── .gitignore
└── pokedex_pages/      # Generated static pages (auto-created on run)
    ├── index.html      # Pokédex home page listing all Pokémon
    └── *.html          # Individual Pokémon detail pages (e.g. 1.html, 2.html)
```

## Installing

1. Clone the repository:
   ```bash
   git clone https://github.com/Sanskar-Adhikari-360/Static-Site-Generator.git
   cd Static-Site-Generator
   ```

2. Make sure Python 3 is installed:
   ```bash
   python --version
   ```

3. Run the generator:
   ```bash
   python index.py
   ```

4. Open the generated Pokédex in your browser:
   ```bash
   open pokedex_pages/index.html        # macOS
   xdg-open pokedex_pages/index.html    # Linux
   ```

## Usage

Once you run `index.py`, the generator will:

1. Connect to `PokemonDB.db`
2. Fetch all Pokémon records from the `Pokemon` table
3. Generate an `index.html` listing all Pokémon with their images
4. Generate an individual detail page for each Pokémon named by their ID

Each page will be named after the Pokémon's ID, for example:
```
pokedex_pages/index.html   # Home listing page
pokedex_pages/1.html       # Bulbasaur
pokedex_pages/2.html       # Ivysaur
pokedex_pages/3.html       # Venusaur
```

## Database Schema

```sql
CREATE TABLE Pokemon (
    Id          INTEGER NOT NULL UNIQUE,
    Name        TEXT NOT NULL,
    Type1       TEXT NOT NULL,
    Type2       TEXT,
    Hp          INTEGER NOT NULL,
    Attack      INTEGER NOT NULL,
    Defense     INTEGER NOT NULL,
    Speed       INTEGER NOT NULL,
    Sp_Attack   INTEGER,
    Sp_Defense  INTEGER,
    Weight      TEXT,
    Height      TEXT,
    Ability     TEXT,
    Image       TEXT,
    Dex_Entry   TEXT,
    PRIMARY KEY(Id AUTOINCREMENT)
);
```

## Deployment

Since the output is plain HTML, you can deploy it anywhere:

- **GitHub Pages** — push the `pokedex_pages/` folder to a `gh-pages` branch
- **Netlify** — drag and drop the `pokedex_pages/` folder
- **Vercel** — point it to the `pokedex_pages/` directory
