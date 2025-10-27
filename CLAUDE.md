# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a **Zenn Connect** repository for managing technical articles and books published on [Zenn.dev](https://zenn.dev/). The repository contains Japanese technical content focused on AI development tools (particularly TRAE), React Native, mobile development, and AI-assisted coding.

### Project Type
Documentation platform using Zenn CLI for content creation and preview.

## Content Structure

### Articles (`articles/`)
Individual technical articles with frontmatter metadata:
- **File naming**: Uses kebab-case slugs (e.g., `trae-cue-ai-development-partner.md`) or random IDs (e.g., `fd97352ed30e5a.md`)
- **Frontmatter fields**:
  ```yaml
  ---
  title: "Article title"
  emoji: "🤖"
  type: "tech" # or "idea"
  topics: ["ai", "react", "typescript"]
  published: false # or true
  ---
  ```

### Books (`books/`)
Long-form technical guides organized by chapters:
- Each book has a directory (e.g., `books/trae-ai-guide/`)
- **`config.yaml`**: Book metadata and chapter ordering
  ```yaml
  title: "Book title"
  summary: "Book description"
  topics: ["topic1", "topic2"]
  published: false
  chapters:
    - introduction
    - chapter-name
  ```
- **Chapter files**: Named to match chapter IDs in config.yaml (e.g., `introduction.md`)

### Supporting Files
- **`TECHNICAL_ARTICLE_MCP.md`**: Writing guidelines based on "伝えたい人に届ける技術記事の書き方" principles
- **`images/`**: Image assets for articles and books
- **Reference documents**: Claude Code UI reference, Zenn command documentation

## Development Commands

### Essential Zenn CLI Commands
```bash
# Create new article
npx zenn new:article

# Create new book
npx zenn new:book

# Preview content locally (starts dev server)
npx zenn preview
```

### Git Workflow
- Main branch: `main`
- Typical workflow for new content:
  1. Create article/book using Zenn CLI
  2. Edit content in Markdown
  3. Preview locally with `npx zenn preview`
  4. Commit and push when ready

## Content Guidelines

When creating or editing technical articles, follow the principles in `TECHNICAL_ARTICLE_MCP.md`:

### Writing Philosophy
- **Target reader**: "Past self who faced this problem"
- **Core principle**: Technology is a means to solve problems, not the end goal
- **Article focus**: "This solution solves this problem" > "This technology is amazing"

### Required Article Structure
1. **Title**: Include the problem solved and main technology used
2. **Introduction** (はじめに):
   - Target audience
   - Article scope (what's covered and what's not)
   - Reader benefits
3. **Main content**:
   - Problem statement
   - Solution overview
   - Detailed steps (What/Why/How)
   - Working code snippets
   - Diagrams/screenshots when helpful
4. **Conclusion** (おわりに):
   - Summary
   - Future outlook
   - Acknowledgments

### Style Guidelines
- Use active voice over passive voice
- One idea per sentence (一文一義)
- Define technical terms on first use
- All code snippets must be tested and working

## Content Topics

This repository focuses on:
1. **TRAE AI Editor** - AI-powered development partner (major focus)
   - Cue (Context Understanding Engine)
   - IDE mode vs Solo mode
   - Technical features and use cases
2. **React Native** - Mobile development
3. **iOS Development** - Release processes and best practices
4. **AI-Assisted Coding** - Claude Code, Vibe Coding, Spec-driven development
5. **Developer Tools** - General productivity and development workflows

## Architecture Patterns

### Article Writing Pattern
When asked to create/edit articles:
1. Check if similar content exists in `articles/` using grep
2. Verify frontmatter follows Zenn format
3. Apply TECHNICAL_ARTICLE_MCP.md principles
4. Ensure code examples are complete and runnable
5. Use appropriate emoji and topics for discoverability

### Book Chapter Pattern
When working with books:
1. Check `config.yaml` for chapter ordering
2. Ensure chapter filename matches chapter ID in config
3. Maintain consistent structure across chapters
4. Update config.yaml when adding/removing chapters

## Language and Localization

- **Primary language**: Japanese (日本語)
- **Code comments**: Can be English or Japanese
- **Technical terms**: Often keep English terms with Japanese explanation
- **Target audience**: Japanese-speaking developers

## Dependencies

```json
{
  "zenn-cli": "^0.2.3"
}
```

No build process, testing framework, or bundler - pure content repository.

## Common Tasks

### Adding New Article
```bash
npx zenn new:article
# Edit the generated file in articles/
# Add frontmatter: title, emoji, type, topics, published
# Preview with: npx zenn preview
```

### Adding New Book Chapter
1. Edit `books/{book-name}/config.yaml` to add chapter ID
2. Create `books/{book-name}/{chapter-id}.md`
3. Write content following book structure
4. Preview with `npx zenn preview`

### Publishing Content
Set `published: true` in frontmatter, then commit and push to trigger Zenn sync.

## Special Considerations

### Image References
- Store images in `images/` directory
- Reference using relative paths from article/chapter
- Organize by subdirectories for different books/topics (e.g., `images/trae-guide/`)

### Unpublished Content
Many articles and the TRAE AI Guide book have `published: false` - these are drafts in progress.

### Code Examples
When adding code to articles:
- Prefer complete, runnable examples over fragments
- Include necessary imports and setup
- Test code before committing
- Use appropriate syntax highlighting (```typescript, ```javascript, etc.)
