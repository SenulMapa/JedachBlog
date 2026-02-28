# Dev.Notes

A fully static personal blog — no backend, no database, no build tools.

## Overview

- **Fully static**: HTML, CSS, vanilla JavaScript only
- **No backend**: Works on GitHub Pages, Netlify, Vercel, or any static host
- **No build step**: Edit files, push to deploy
- **Client-side rendering**: Homepage dynamically loads posts from `posts.json`

## Project Structure

```
/
├── index.html              # Homepage (dynamic, no edits needed for new posts)
├── posts.json              # Blog metadata (edit this to add posts)
├── post-template.html      # Template for new articles
├── posts/
│   ├── ai-not-replacing-engineers.html
│   ├── secret-keys-github.html
│   └── ...                 # Individual article HTML files
└── README.md
```

## Publishing Workflow

To add a new article:

1. **Create the article HTML file** in `/posts/`
   - Copy `post-template.html` as a starting point
   - Name it descriptively: `my-article-title.html`

2. **Add the entry** to `posts.json`:

```json
{
  "title": "Your Article Title",
  "slug": "my-article-title.html",
  "tag": "Category Name",
  "date": "2026-02-28",
  "readTime": "5 min read",
  "featured": false,
  "excerpt": "A brief summary of the article..."
}
```

3. **Push to GitHub** — done!

The homepage will automatically:
- Load the new post from `posts.json`
- Display it in the grid (sorted by date, newest first)
- Apply topic filters if the tag matches

## posts.json Format

| Field | Type | Description |
|-------|------|-------------|
| `title` | string | Article title |
| `slug` | string | Filename in `/posts/` directory |
| `tag` | string | Category (used for filtering) |
| `date` | string | ISO date `YYYY-MM-DD` |
| `readTime` | string | e.g., "5 min read" |
| `featured` | boolean | If true, shows in featured section |
| `excerpt` | string | Short summary for cards |

## Features

- **Dynamic featured post**: First post with `"featured": true` is featured
- **Topic filtering**: Click topic chips to filter by tag
- **Date sorting**: Posts sorted newest first automatically
- **Error handling**: Graceful fallback if `posts.json` fails to load
- **Responsive design**: Works on mobile and desktop
- **No JavaScript required for articles**: Individual posts are static HTML

## Article Template Components

The `post-template.html` includes:
- Header with logo and "Human Written" badge
- Hero section with title, tag, date, read time
- Article body with styled elements:
  - Paragraphs (`<p>`)
  - Strong emphasis (`<strong>`)
  - Headings (`<h2>`, `<h3>`)
  - Lists (`<ul>`, `<ol>`)
  - Inline code (`<code>`)
  - Code blocks (`<pre><code>`)
  - Pull quotes (`.callout`)
  - Security notes (`.security-box`)
  - TLDR section (`.tldr-section`)
- Footer with back link

## Deployment

### GitHub Pages
1. Push to a GitHub repository
2. Go to Settings → Pages
3. Select source: Deploy from branch → `main` → `/ (root)`
4. Site will be at `https://yourusername.github.io/repo-name/`

### Local Development
Simply open `index.html` in a browser, or use any static server:

```bash
# Python 3
python -m http.server 8000

# Node.js (npx serve)
npx serve .

# PHP
php -S localhost:8000
```

## Security

- No API keys or secrets in the codebase
- No admin panel or authentication
- No external CMS or database
- No server-side code
- Minimal attack surface — just static HTML files

## Customization

### Colors
Edit CSS variables in `:root`:

```css
:root {
  --bg: #0a0a08;        /* Background */
  --surface: #111110;   /* Card backgrounds */
  --accent: #e8ff47;    /* Primary accent (lime) */
  --accent2: #ff6b35;   /* Secondary accent (orange) */
  --text: #e8e4d9;      /* Main text */
  --muted: #6b6860;     /* Secondary text */
  --border: #2a2a26;    /* Borders */
}
```

### Fonts
Uses Google Fonts:
- **Playfair Display**: Headings (serif)
- **DM Mono**: UI elements, code (monospace)
- **DM Sans**: Body text (sans-serif)

### Ticker Messages
Edit the `.ticker` div in `index.html` to change scrolling messages.

## License

Your content. Your code. Do what you want.
