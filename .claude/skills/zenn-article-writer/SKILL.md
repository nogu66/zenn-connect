---
name: zenn-article-writer
description: "Write high-quality Zenn technical articles following Japanese article writing best practices, focusing on problem-solving narratives rather than technology showcases"
---

# Zenn Technical Article Writer

This skill enables Claude to write high-quality technical articles for Zenn.dev following established Japanese technical writing best practices.

## Core Philosophy

**Technology is a means to solve problems, not the end goal.**

The primary approach is: **"This solution solves this problem" > "This technology is amazing"**

### Target Reader

The most important target reader is **"your past self who faced this problem"**. Write as if explaining to yourself from the past:
- What problem were you facing?
- What did you struggle with?
- How did you solve it?

Secondary targets are colleagues and community members who might face similar challenges.

## When to Use This Skill

Use this skill when:
- Creating a new Zenn article
- The user asks to write about a technical topic
- Documenting a solution to a problem
- Sharing technical knowledge or experience

## Article Structure

Follow this structure for all Zenn articles:

### 1. Title (タイトル)

**Format**: Include both the problem solved and the main technology used.

**Good examples**:
- "ClaudeのSkills機能で「毎回同じこと説明する問題」を解決する"
- "【TypeScript】zodを使って環境変数の静的型付けとバリデーションを実現する"

**Bad examples**:
- "Claudeがすごい" (Technology showcase, no problem stated)
- "環境変数について" (No solution, no specific technology)

Include keywords that readers would use when searching.

### 2. Introduction (はじめに)

Must clearly state three elements:

#### 2.1. Target Readers (この記事の対象読者)
```markdown
**この記事の対象読者**
- [Specific reader profile 1]
- [Specific reader profile 2]
- [Specific reader profile 3]
```

Example:
```markdown
**この記事の対象読者**
- Claude Code、Claude.ai、Claude APIを業務で活用している開発者
- AIに同じ指示を何度も繰り返している人
- 組織固有のワークフローやブランドガイドラインをAIに適用したい人
```

#### 2.2. Article Scope (この記事でわかること)
Clearly state what WILL and will NOT be covered:

```markdown
**この記事でわかること**
- [Key learning point 1]
- [Key learning point 2]
- [Key learning point 3]

**この記事で扱わないこと**
- [Out of scope topic 1]
- [Out of scope topic 2]
```

#### 2.3. Reader Benefits (読者が得られるもの)
What will readers gain by reading this article to the end?

### 3. Main Content (本文)

#### 3.1. Problem Statement
Start by describing the problem readers can relate to:

```markdown
## 「[Relatable problem description]」

[Describe the pain points readers experience]

- Concrete example 1
- Concrete example 2
- Concrete example 3

[Explain why this is frustrating or time-consuming]

**[Technology Name]は、この問題を解決します。**
```

#### 3.2. Solution Overview
Briefly introduce the solution before diving into details.

#### 3.3. Detailed Explanation (What/Why/How)

For each aspect, explain:
- **What**: What are you doing?
- **Why**: Why is this necessary? Why this approach?
- **How**: Concrete implementation with code examples

#### 3.4. Code Examples

**Requirements**:
- All code must be tested and actually work
- Include necessary imports and setup
- Make it copy-paste-able when possible
- Use appropriate syntax highlighting

```markdown
```typescript
// Working, complete example
import { something } from 'library';

function example() {
  // Implementation
}
\`\`\`
```

For long code, provide GitHub repository links.

#### 3.5. Visual Aids

- Use diagrams for complex concepts or architecture
- Use screenshots for step-by-step instructions or results
- Ensure all images enhance understanding

### 4. Results/Outcomes (やってみた結果)

Show what happened when you applied the solution:
- Success stories
- Performance improvements
- Challenges encountered
- Lessons learned

Be honest about both successes and limitations.

### 5. Conclusion (おわりに)

Must include:

#### 5.1. Summary
Briefly recap the main points:
```markdown
[Technology]は、**「[Problem]」を解決する**[adjective]仕組みです。

[Summary of how it solves the problem]
```

#### 5.2. Next Steps
Give readers actionable next steps:
```markdown
### 今すぐ始めるには

1. [Step 1]
2. [Step 2]
3. [Step 3]
```

#### 5.3. Future Outlook (Optional)
Mention advanced topics or future possibilities.

#### 5.4. Acknowledgments (Optional)
Thank people who helped or references that were crucial.

### 6. References (参考リンク)

List key references:
- Official documentation
- GitHub repositories
- Related articles
- Tools or platforms mentioned

## Writing Style Guidelines

### Language Rules

1. **One Idea Per Sentence (一文一義)**
   - Keep each sentence focused on a single idea
   - Break complex sentences into multiple simple ones

2. **Active Voice Over Passive**
   - Good: "この関数は値を返します"
   - Bad: "値が返されます"

3. **Define Technical Terms**
   - On first use, provide a brief explanation
   - Use parentheses for clarification: "MCP (Model Context Protocol)"

4. **Be Concrete**
   - Use specific examples over abstract descriptions
   - Show, don't just tell

### Tone

- Professional but approachable
- Empathetic to reader's challenges
- Confident but humble
- Encouraging and supportive

### Common Phrases

**Problem introduction**:
- "こんな経験はありませんか?"
- "〜で困っていませんか?"

**Solution introduction**:
- "[Technology]は、この問題を解決します。"
- "[Technology]を使えば、[problem]を[solution]できます。"

**Explanation transitions**:
- "具体的には..."
- "つまり..."
- "要するに..."

**Encouragement**:
- "実際にやってみましょう"
- "早速試してみます"

## Zenn-Specific Format

### Frontmatter

Always include proper frontmatter:

```yaml
---
title: "Article title (max 50 chars recommended)"
emoji: "🛠️"  # Choose relevant emoji
type: "tech"  # or "idea"
topics: ["topic1", "topic2", "topic3"]  # 1-5 topics, lowercase
published: false  # Set true when ready to publish
---
```

### Topics Selection

Choose 1-5 relevant topics (lowercase):
- Technology names: "typescript", "react", "claude"
- Categories: "ai", "開発効率化", "自動化"
- Platforms: "zenn", "github"

### Emoji Selection

Choose an emoji that represents:
- The main technology (🤖 for AI, ⚛️ for React)
- The action (🛠️ for tools, 📝 for writing)
- The feeling (✨ for excitement, 🎉 for celebration)

## Quality Checklist

Before completing an article, verify:

- [ ] Title includes both problem and solution technology
- [ ] Introduction clearly states target readers, scope, and benefits
- [ ] Problem statement is relatable and concrete
- [ ] All code examples have been tested and work
- [ ] What/Why/How is explained for each major point
- [ ] Conclusion summarizes key takeaways
- [ ] Next steps are actionable and clear
- [ ] All technical terms are defined on first use
- [ ] One idea per sentence throughout
- [ ] References include all important sources
- [ ] Frontmatter is complete and accurate

## Anti-Patterns to Avoid

**Don't**:
- Write technology showcases without problem context
- Use passive voice excessively
- Include untested code examples
- Write overly long sentences with multiple ideas
- Skip the "why" and only explain "what" and "how"
- Forget to define the target reader
- Write conclusions that are just summaries without next steps

**Do**:
- Focus on problem-solving narratives
- Use active voice and concrete examples
- Test all code before including it
- Keep sentences simple and focused
- Always explain the reasoning behind choices
- Clearly define who will benefit from reading
- Give readers actionable next steps

## Example Application

When asked to write an article about a new technology:

1. **First, identify the problem**: What pain point does this technology solve?
2. **Define the reader**: Who struggles with this problem?
3. **Structure the narrative**: Past problem → Solution → Implementation → Results
4. **Write with empathy**: Remember what it was like before you knew the solution
5. **Provide value**: Ensure readers can immediately apply what they learn

## Integration with Zenn CLI

When creating articles, use:

```bash
# Create new article
npx zenn new:article

# Preview locally
npx zenn preview
```

The article will be created in `articles/` directory with a random ID filename.

## Remember

The goal is not to show off technology or your knowledge. The goal is to **help your past self and others solve real problems**. Write the article you wish you had found when you were struggling with this issue.
