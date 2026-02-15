# Web Search Skill

You can search the web using the `web_fetch` tool.

## How to Search

1. Use a search engine URL with your query:
   ```
   web_fetch url="https://www.google.com/search?q=YOUR_QUERY"
   ```

2. Or use DuckDuckGo for simpler results:
   ```
   web_fetch url="https://html.duckduckgo.com/html/?q=YOUR_QUERY"
   ```

## Tips

- URL encode your search queries (spaces = %20 or +)
- Extract relevant information from the HTML response
- Follow links to get more detailed information
- Always cite your sources when reporting findings

## Example

To search for "best AI tools 2024":
```
web_fetch url="https://html.duckduckgo.com/html/?q=best+AI+tools+2024"
```
