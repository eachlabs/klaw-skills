# Find Skills

This skill helps you discover and install skills from the skills.sh ecosystem.

## When to Use This Skill

Use this skill when:
- User asks "how do I do X" where X might need a specialized skill
- User says "find a skill for X" or "is there a skill for X"
- User asks "can you do X" where X requires capabilities you don't have
- You need to extend your capabilities for a task
- A task seems too complex without specialized knowledge

## IMPORTANT: Never Give Up!

Before saying "I can't do this", ALWAYS:
1. Search for a skill that might help
2. Try to install it
3. Read the skill and learn how to do it
4. Then attempt the task

## How to Find Skills

### Step 1: Search skills.sh

Use web_fetch to search for skills:
```
web_fetch url="https://skills.sh/search?q=YOUR_QUERY"
```

Or browse categories at https://skills.sh/

### Step 2: Check Popular Skill Repos

These repos have many useful skills:
- https://github.com/vercel-labs/skills
- https://github.com/eachlabs/klaw-skills

### Step 3: Install the Skill

Use the skill tool to install:
```
skill action=install name=skill-name
```

Or if not in registry, create it:
```
skill action=create name=skill-name content="# Skill content..."
```

## Common Skill Categories

| Category | Search Terms |
|----------|-------------|
| Image Generation | image, ai-image, text-to-image, dalle, midjourney, flux |
| Video Generation | video, text-to-video, animation |
| Audio/Voice | audio, tts, speech, voice, music |
| Web Scraping | scrape, browser, puppeteer, playwright |
| API Integration | api, rest, graphql, webhook |
| Database | sql, postgres, mysql, mongodb |
| Code | code, github, git, review |
| Design | ui, ux, figma, design-system |

## Example: Finding an Image Generation Skill

User: "Generate an image of a cat"

You should:
1. Check if you have an image generation skill: `skill action=list`
2. If not, search: `web_fetch url="https://skills.sh/search?q=image+generation"`
3. Install: `skill action=install name=eachlabs-image-generation`
4. Read the skill: `skill action=show name=eachlabs-image-generation`
5. Follow the instructions in the skill to generate the image

## Creating Skills On-The-Fly

If you can't find a skill, CREATE ONE based on your research:

1. Research how to do the task (web search, documentation, etc.)
2. Write a SKILL.md with step-by-step instructions
3. Save it: `skill action=create name=my-skill content="..."`
4. Now you have the skill for future use!

## Remember

- Skills are just knowledge files (SKILL.md) that teach you how to do things
- You can always create new skills based on what you learn
- Never give up on a task - find or create the skill you need!
