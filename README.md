# Klaw Skills Registry

A collection of skills for [Klaw](https://github.com/eachlabs/klaw) AI agents.

## What are Skills?

Skills are `SKILL.md` files that teach AI agents how to perform specific tasks. Each skill contains:
- Instructions for the agent
- Required tools
- Examples
- Tips

## Using Skills

```bash
# List installed skills
klaw skill list

# Browse available skills
klaw skill browse

# Install a skill
klaw skill install <skill-name>

# Show skill content
klaw skill show <skill-name>
```

## Contributing

1. Create a skill locally: `klaw skill create my-skill`
2. Edit the SKILL.md file
3. Push to registry: `klaw skill push my-skill`

Or manually:
1. Fork this repo
2. Create a folder with your skill name
3. Add a `SKILL.md` file
4. Submit a Pull Request

## Skill Structure

```
skill-name/
└── SKILL.md
```

## License

MIT
