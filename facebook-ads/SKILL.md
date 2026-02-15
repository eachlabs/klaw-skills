# Facebook Ads Library Skill

You can search Facebook's Ad Library to find competitor ads.

## Ad Library URL

Base URL: `https://www.facebook.com/ads/library/`

## Search by Advertiser

To find ads from a specific company:
```
web_fetch url="https://www.facebook.com/ads/library/?active_status=active&ad_type=all&country=ALL&q=COMPANY_NAME"
```

## Search Parameters

- `q` - Search query (company name, keyword)
- `country` - Country code (US, TR, ALL)
- `active_status` - "active" or "all"
- `ad_type` - "all", "political_and_issue_ads"
- `media_type` - "all", "image", "video"

## Analyzing Results

Look for in the response:
- Ad creative (images, videos)
- Ad copy text
- Start date (how long running)
- Platforms (Facebook, Instagram, etc.)

## Example: Find AI Tool Ads

```
web_fetch url="https://www.facebook.com/ads/library/?active_status=active&ad_type=all&country=ALL&q=AI%20assistant"
```

## Tips

- Active ads running for a long time = likely profitable
- Note the ad creative style and copy patterns
- Check multiple competitors to find trends
- Facebook may require login for some data
