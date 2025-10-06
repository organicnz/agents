# Agent Guidelines

This document defines the standards and best practices for creating and maintaining agent definition files in this repository.

## File Naming Conventions

### Platform Naming
- **iOS agents:** Use uppercase "iOS" (e.g., `elevenlabs-speech-specialist-iOS.md`)
- **Flutter/cross-platform:** Use lowercase (e.g., `flutter-expert.md`)
- **Other platforms:** Use lowercase (e.g., `nextjs-developer.md`)

### Role Naming
Use consistent role titles based on the agent's primary function:
- **`-developer`:** Implementation-focused roles (e.g., `iOS-developer`, `nextjs-developer`)
- **`-engineer`:** System/infrastructure roles (e.g., `documentation-engineer`, `security-engineer`)
- **`-specialist`:** Domain-specific expertise (e.g., `upstash-specialist`, `openai-realtime-specialist`)
- **`-analyst`:** Research/analysis roles (e.g., `research-analyst`, `trend-analyst`)
- **`-expert`:** Advanced technical expertise (e.g., `flutter-expert`, `qa-expert`)

### Examples
✅ Correct:
- `iOS-developer.md`
- `elevenlabs-speech-specialist-iOS.md`
- `flutter-expert-debugger.md`
- `documentation-engineer.md`

❌ Incorrect:
- `ios-developer.md` (should be uppercase iOS)
- `ios-speech-specialist.md` (iOS should be at end: `speech-specialist-iOS.md`)

## File Structure

All agent files must follow this structure:

```yaml
---
name: agent-name
description: Use this agent when [concise 2-3 sentence description]. Examples: <example>Context: [scenario] user: "[user request]" assistant: "[assistant response with agent invocation]"</example> [2 more examples]
model: sonnet
---

[Agent role statement - 1-2 paragraphs describing who they are and their core mission]

## Core Expertise Areas

[List of expertise areas with bullet points or subsections]

## [Additional sections as needed for the specific agent]

## Quality Standards

[Quality expectations and standards the agent maintains]
```

### Required Sections
1. **YAML Front Matter:**
   - `name`: Kebab-case agent name matching filename
   - `description`: 2-3 sentences with exactly 3 examples
   - `model`: Usually "sonnet"

2. **Agent Role Statement:**
   - 1-2 paragraphs introducing the agent
   - Clear statement of their core mission and expertise

3. **Core Expertise Areas:**
   - Bulleted or structured list of capabilities
   - Specific, actionable items

4. **Quality Standards:**
   - Standards the agent maintains
   - Expected outputs and behaviors

### Optional Sections (as appropriate)
- Implementation Guidelines
- Methodology/Approach
- Tools & Technologies
- Troubleshooting Expertise
- Communication Style
- Architecture & Best Practices

## Description Format

### Structure
The description must include:
1. **Opening statement:** "Use this agent when [primary use case]"
2. **Scope expansion:** "This includes [related capabilities]"
3. **Examples:** Exactly 3 examples using the format below

### Example Format
```xml
<example>
Context: [Brief scenario description]
user: "[User's request or question]"
assistant: "[How to invoke this agent]"
<commentary>
[Optional: Reasoning for using this agent]
</commentary>
</example>
```

### Example Guidelines
- **3 examples required** - no more, no less
- Cover different use cases or scenarios
- Show when to invoke the agent
- Keep examples concise and practical
- Include `<commentary>` only when clarification is needed

## Platform Parity

When creating platform-specific agents, ensure complementary agents exist:

### Current Platform Coverage
- **iOS:** iOS-developer, iOS-expert-debugger, refactoring-specialist-iOS
- **Flutter:** flutter-expert, flutter-expert-debugger, refactoring-specialist-flutter
- **Voice APIs:**
  - ElevenLabs: `-iOS` and base versions
  - Hume EVI: `-iOS` and base versions
  - OpenAI Realtime: `-iOS` and base versions

### Guidelines
- If creating an iOS-specific agent, consider if a Flutter equivalent is needed
- Maintain consistent capabilities across platform variants
- Document platform-specific features clearly

## Avoiding Duplication

### Before Creating a New Agent
1. **Check existing agents** for overlapping functionality
2. **Consider merging** if >60% overlap with existing agent
3. **Specialize clearly** - ensure distinct value proposition

### Consolidation Rules
- Merge agents with >80% overlapping functionality
- Keep specialized agents (e.g., platform-specific) separate
- Prefer one general agent over multiple similar agents

### Examples
✅ Keep separate:
- `iOS-expert-debugger` (iOS-specific) vs `flutter-expert-debugger` (Flutter-specific)
- `api-documenter` (API-focused) vs `documentation-engineer` (systems-focused)

❌ Consolidate:
- `debugger` + `expert-debugger` → Keep only `expert-debugger`
- `technical-writer` + `documentation-engineer` → Merged into `documentation-engineer`

## Quality Checklist

Before committing an agent file, verify:

- [ ] Filename follows naming conventions (iOS capitalized if applicable)
- [ ] YAML front matter is complete and correctly formatted
- [ ] Description is 2-3 sentences with exactly 3 examples
- [ ] Examples follow the required XML format
- [ ] Agent role statement is clear and concise (1-2 paragraphs)
- [ ] Core Expertise section is well-structured
- [ ] Quality Standards section is included
- [ ] No >60% duplication with existing agents
- [ ] Platform parity considered if platform-specific
- [ ] Markdown formatting is clean and consistent
- [ ] No project-specific details (unless in designated project-specific agents)

## Model Selection

### Standard Models
- **`sonnet`:** Default for most agents (balance of capability and speed)
- **`opus`:** Use configuration/deployment settings, not separate files

### Custom Configuration
- Model variants should be handled through configuration, not duplicate agent files
- Special model requirements should be documented in the agent's Quality Standards section

## Metadata Fields

### Standard Fields
- `name`: Required - kebab-case matching filename
- `description`: Required - formatted as specified above
- `model`: Required - usually "sonnet"

### Optional Fields
- `color`: Only use if part of established color-coding system
- Other fields: Discuss before adding

## Maintenance

### Regular Reviews
- Quarterly review for outdated information
- Update examples if API/framework changes
- Consolidate if duplication emerges
- Archive deprecated agents

### Version Control
- Commit with clear, descriptive messages
- Reference related issues/PRs when applicable
- Use conventional commits format

### Documentation Updates
- Update this guidelines document when patterns change
- Document decisions in commit messages
- Maintain CHANGELOG for significant changes

## Project-Specific Agents

If creating project-specific agents (e.g., with references to specific codebases):
- Clearly mark in description
- Consider separate directory or clear naming convention
- Ensure general value before including in main repository

## Getting Help

If unsure about:
- Agent duplication → Check existing agents and this guide
- Naming conventions → Follow the patterns in "File Naming Conventions"
- Structure questions → Reference "File Structure" section
- Platform parity → Review "Platform Parity" section

For questions not covered here, open an issue for discussion.
