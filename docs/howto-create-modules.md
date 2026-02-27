# How to Create Lola Modules

A guide for creating portable AI skills and commands that work
across Claude Code, Cursor, Gemini CLI, and OpenCode.

## Two Ways to Create Modules

### The Easy Way: lola-manager (Recommended)

Use **lola-manager** for intelligent, guided module creation with
workflow assistance and automatic boilerplate generation.

```bash
# Install lola-manager
lola mod add https://github.com/mrbrandao/lola-manager
lola install lola-manager -a claude-code

# Then ask your AI assistant
create a new module
```

lola-manager will interactively guide you through:
- Module structure creation
- Pattern recognition (Simple, Reference, Workflow, Automation)
- Template generation with best practices
- Validation and linting
- README generation

Perfect for creating well-structured, production-ready modules!

### The Manual Way: lola mod init

For those who prefer manual control or want to learn the
structure:

```bash
lola mod init my-awesome-module
cd my-awesome-module
```

This creates a basic structure you can customize manually.

---

## Module Structure

```
my-module/
  skills/            # AI skills
    skill-name/
      SKILL.md       # Required: skill definition
      scripts/       # Optional: helper scripts
      templates/     # Optional: templates
  commands/          # Slash commands (optional)
    command.md
  agents/            # Subagents (optional)
    agent.md
```

**Note:** Lola uses auto-discovery. Skills are discovered from
`skills/<name>/SKILL.md`, commands from `commands/*.md`, and
agents from `agents/*.md`. No manifest file required!

## Creating Skills

Skills are the core of Lola modules. They provide instructions,
workflows, and guidance for AI assistants.

### SKILL.md Format

```markdown
---
name: skill-name
description: Brief description for discovery
allowed-tools: [Read, Write, Bash]  # Optional
---

# Skill Title

Your instructions for the AI assistant.

## When to Use This

Explain when the AI should use this skill.

## Instructions

Step-by-step guidance...
```

### Frontmatter Fields

- **name** (required): Skill identifier
- **description** (required): When to use this skill
- **allowed-tools** (optional): Restrict which tools AI can use

### Supporting Files

Add scripts, templates, or examples to your skill directory:

```
skills/
  my-skill/
    SKILL.md
    scripts/
      helper.sh
    templates/
      example.md
```

Reference them using relative paths in SKILL.md:

```markdown
Use the helper script: `./scripts/helper.sh`
Load the template: `./templates/example.md`
```

**Path handling:** Use relative paths like `./file` or
`./scripts/helper.sh` to reference files in the same skill
directory. Each assistant handles these differently:

| Assistant   | Skill Location           | Path Behavior    |
|-------------|--------------------------|------------------|
| Claude Code | `.claude/skills/<skill>` | Copied with skill|
| Cursor      | `.cursor/rules/<skill>`  | Paths rewritten  |
| Gemini      | `GEMINI.md` (reference)  | Paths work       |
| OpenCode    | `AGENTS.md` (reference)  | Paths work       |

Lola automatically rewrites paths for each assistant type.

## Creating Commands

Commands are slash commands that users can trigger explicitly.

### Command Format

Create `commands/my-command.md`:

```markdown
---
description: What this command does
argument-hint: <required> [optional]
---

Your prompt template here. Use $ARGUMENTS for all arguments
or $1, $2 for positional arguments.
```

### Argument Variables

- **$ARGUMENTS** - All arguments as a single string
- **$1, $2, $3...** - Positional arguments

### Example Command

```markdown
---
description: Review a pull request
argument-hint: <pr-number>
---

Review PR #$1 and provide detailed feedback on:
- Code quality
- Best practices
- Potential issues
```

## Creating Agents

Agents are specialized subagents for specific tasks.

Create `agents/my-agent.md`:

```markdown
---
description: What this agent does
---

Agent instructions and behavior...
```

## Best Practices

### 1. Clear Descriptions

Good: "Generate conventional commit messages from staged changes"
Bad: "Helps with commits"

### 2. Progressive Disclosure

Keep SKILL.md under 5000 tokens. Move detailed documentation to
separate files and reference them.

### 3. Tool Restrictions

Use `allowed-tools` to prevent security issues:

```yaml
---
allowed-tools: [Read]  # Read-only skill
---
```

### 4. Cross-Assistant Compatibility

Test your module with multiple assistants:
- Claude Code
- Cursor
- Gemini CLI

### 5. Version Your Module

Follow semantic versioning (MAJOR.MINOR.PATCH):
- MAJOR: Breaking changes
- MINOR: New features
- PATCH: Bug fixes

## Testing Your Module

### 1. Add to Local Registry

```bash
lola mod add ./my-module
```

### 2. Install to AI Assistant

```bash
# Install to all assistants
lola install my-module

# Or install to specific assistant
lola install my-module -a claude-code
```

### 3. Test Functionality

Try using your skills and commands with your AI assistant to
ensure everything works as expected.

### 4. Regenerate After Changes

```bash
lola update
```

## Publishing Your Module

### 1. Create a GitHub Repository

```bash
git init
git add .
git commit -m "feat: initial module"
git remote add origin https://github.com/you/your-module
git push -u origin main
```

### 2. Add a README

Explain what your module does, how to install it, and how to
use it. See existing modules for examples.

### 3. Submit to Marketplace

Follow the [contribution guide](../CONTRIBUTING.md) to add your
module to the Lola Marketplace so others can discover and use it.

## Examples

See the marketplace catalog for examples:
- **lola-manager**: Complex module with workflows, templates,
  and scripts
- **chef-buddy**: Lazy context loading demonstration with
  persona and step-by-step workflows

## Resources

- **[Lola Documentation](https://github.com/RedHatProductSecurity/lola)**:
  Official Lola docs
- **[Lola Marketplace](./modules-catalog.md)**: Browse existing
  modules for inspiration
- **[Module Structure Reference](https://github.com/RedHatProductSecurity/lola#module-structure)**:
  Detailed structure guide
- **[lola-manager](https://github.com/mrbrandao/lola-manager)**:
  Interactive module builder

## Getting Help

Questions? Open an issue on the
[Lola repository](https://github.com/RedHatProductSecurity/lola/issues)
or check existing modules for examples.

---

*Happy module building!* 🚀
