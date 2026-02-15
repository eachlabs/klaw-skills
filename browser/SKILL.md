# Browser Skill

You can browse websites and extract information using `web_fetch`.

## Basic Usage

Fetch any URL and read its content:
```
web_fetch url="https://example.com"
```

## Extracting Data

The response will be HTML. Look for:
- `<title>` for page title
- `<meta name="description">` for description
- `<h1>`, `<h2>` for headings
- `<p>` for paragraphs
- `<a href="...">` for links
- `<img src="...">` for images

## Following Links

1. Fetch the initial page
2. Find relevant links in the HTML
3. Fetch those links for more information

## Tips

- Some sites block automated requests - try different user agents
- For JavaScript-heavy sites, data may not be available (use API if available)
- Respect robots.txt and rate limits
- Look for API endpoints in the page source for structured data
