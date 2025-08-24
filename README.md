<div align="right">
  <details>
    <summary >🌐 Language</summary>
    <div>
      <div align="center">
        <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=en">English</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=zh-CN">简体中文</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=zh-TW">繁體中文</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=ja">日本語</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=ko">한국어</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=hi">हिन्दी</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=th">ไทย</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=fr">Français</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=de">Deutsch</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=es">Español</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=it">Italiano</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=ru">Русский</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=pt">Português</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=nl">Nederlands</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=pl">Polski</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=ar">العربية</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=fa">فارسی</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=tr">Türkçe</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=vi">Tiếng Việt</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=id">Bahasa Indonesia</a>
        | <a href="https://openaitx.github.io/view.html?user=wshobson&project=agents&lang=as">অসমীয়া</
      </div>
    </div>
  </details>
</div>

# Claude Code Subagents Collection

A comprehensive collection of specialized AI subagents for [Claude Code](https://docs.anthropic.com/en/docs/claude-code), designed to enhance development workflows with domain-specific expertise.

## Overview

This repository contains 75 specialized subagents that extend Claude Code's capabilities. Each subagent is an expert in a specific domain, automatically invoked based on context or explicitly called when needed. All agents are configured with specific Claude models based on task complexity for optimal performance and cost-effectiveness.

## Available Subagents

### Development & Architecture
- **[architect-reviewer](architect-review.md)** - Reviews code changes for architectural consistency and patterns

### Language Specialists
- **[python-pro](python-pro.md)** - Write idiomatic Python code with advanced features and optimizations


### Quality & Security
- **[code-reviewer](code-reviewer.md)** - Expert code review with deep configuration security focus and production reliability
- **[security-auditor](security-auditor.md)** - Review code for vulnerabilities and ensure OWASP compliance
- **[test-automator](test-automator.md)** - Create comprehensive test suites with unit, integration, and e2e tests
- **[performance-engineer](performance-engineer.md)** - Profile applications, optimize bottlenecks, and implement caching strategies
- **[debugger](debugger.md)** - Debugging specialist for errors, test failures, and unexpected behavior
- **[error-detective](error-detective.md)** - Search logs and codebases for error patterns, stack traces, and anomalies
- **[search-specialist](search-specialist.md)** - Expert web researcher using advanced search techniques and synthesis



### Documentation
- **[docs-architect](docs-architect.md)** - Creates comprehensive technical documentation from existing codebases
- **[mermaid-expert](mermaid-expert.md)** - Create Mermaid diagrams for flowcharts, sequences, ERDs, and architectures
- **[reference-builder](reference-builder.md)** - Creates exhaustive technical references and API documentation
- **[tutorial-engineer](tutorial-engineer.md)** - Creates step-by-step tutorials and educational content from code

## Installation

These subagents are automatically available when placed in `~/.claude/agents/` directory.

```bash
cd ~/.claude
git clone https://github.com/wshobson/agents.git
```

## Usage

### Automatic Invocation
Claude Code will automatically delegate to the appropriate subagent based on the task context and the subagent's description.

### Explicit Invocation
Mention the subagent by name in your request:
```
"Use the code-reviewer to check my recent changes"
"Have the security-auditor scan for vulnerabilities"
"Get the performance-engineer to optimize this bottleneck"
```

## Usage Examples

### Single Agent Tasks
```bash
# Code quality and review
"Use code-reviewer to analyze this component for best practices"
"Have code-reviewer scrutinize these configuration changes"
"Have security-auditor check for OWASP compliance issues"
```

### Multi-Agent Workflows

These subagents work together seamlessly, and for more complex orchestrations, you can use the **[Claude Code Commands](https://github.com/wshobson/commands)** collection which provides 52 pre-built slash commands that leverage these subagents in sophisticated workflows.

```bash
# Feature development workflow
"Implement user authentication feature"
# Automatically uses: backend-architect → frontend-developer → test-automator → security-auditor
```

## Subagent Format

Each subagent follows this structure:
```markdown
---
name: subagent-name
description: When this subagent should be invoked
model: haiku  # Optional - specify which model to use (haiku/sonnet/opus)
tools: tool1, tool2  # Optional - defaults to all tools
---

System prompt defining the subagent's role and capabilities
```

### Model Configuration

As of Claude Code v1.0.64, subagents can specify which Claude model they should use. This allows for cost-effective task delegation based on complexity:

- **Low Complexity (Haiku)**: Simple tasks like basic data analysis, documentation generation, and standard responses
- **Medium Complexity (Sonnet)**: Development tasks, code review, testing, and standard engineering work  
- **High Complexity (Opus)**: Critical tasks like security auditing, architecture review, incident response, and AI/ML engineering

Available models (using simplified naming as of Claude Code v1.0.64):
- `haiku` - Fast and cost-effective for simple tasks
- `sonnet` - Balanced performance for most development work
- `opus` - Most capable for complex analysis and critical tasks

If no model is specified, the subagent will use the system's default model.

## Agent Orchestration Patterns

Claude Code automatically coordinates agents using these common patterns:

### Sequential Workflows
```
User Request → Agent A → Agent B → Agent C → Result

Example: "Build a new API feature"
backend-architect → frontend-developer → test-automator → security-auditor
```

### Parallel Execution
```
User Request → Agent A + Agent B (simultaneously) → Merge Results

Example: "Optimize application performance" 
performance-engineer + database-optimizer → Combined recommendations
```

### Conditional Branching
```
User Request → Analysis → Route to appropriate specialist

Example: "Fix this bug"
debugger (analyzes) → Routes to: backend-architect OR frontend-developer OR devops-troubleshooter
```

### Review & Validation
```
Primary Agent → Review Agent → Final Result

Example: "Implement payment processing"
payment-integration → security-auditor → Validated implementation
```

## When to Use Which Agent


### 🧪 Quality Assurance
- **code-reviewer**: Code quality, configuration security, production reliability
- **test-automator**: Test strategy, test suite creation
- **debugger**: Bug investigation, error resolution
- **error-detective**: Log analysis, error pattern recognition, root cause analysis
- **search-specialist**: Deep web research, competitive analysis, fact-checking

### 📚 Documentation
- **api-documenter**: OpenAPI/Swagger specs, API documentation
- **docs-architect**: Comprehensive technical documentation, architecture guides, system manuals
- **reference-builder**: Exhaustive API references, configuration guides, parameter documentation
- **tutorial-engineer**: Step-by-step tutorials, learning paths, educational content



## Best Practices

### 🎯 Task Delegation
1. **Let Claude Code delegate automatically** - The main agent analyzes context and selects optimal agents
2. **Be specific about requirements** - Include constraints, tech stack, and quality requirements
3. **Trust agent expertise** - Each agent is optimized for their domain

### 🔄 Multi-Agent Workflows
4. **Start with high-level requests** - Let agents coordinate complex multi-step tasks
5. **Provide context between agents** - Ensure agents have necessary background information
6. **Review integration points** - Check how different agents' outputs work together

### 🎛️ Explicit Control
7. **Use explicit invocation for specific needs** - When you want a particular expert's perspective
8. **Combine multiple agents strategically** - Different specialists can validate each other's work
9. **Request specific review patterns** - "Have security-auditor review backend-architect's API design"

### 📈 Optimization
10. **Monitor agent effectiveness** - Learn which agents work best for your use cases
11. **Iterate on complex tasks** - Use agent feedback to refine requirements
12. **Leverage agent strengths** - Match task complexity to agent capabilities

## Contributing

To add a new subagent:
1. Create a new `.md` file following the format above
2. Use lowercase, hyphen-separated names
3. Write clear descriptions for when the subagent should be used
4. Include specific instructions in the system prompt

## Troubleshooting

### Common Issues

**Agent not being invoked automatically:**
- Ensure your request clearly indicates the domain (e.g., "performance issue" → performance-engineer)
- Be specific about the task type (e.g., "review code" → code-reviewer)

**Unexpected agent selection:**
- Provide more context about your tech stack and requirements
- Use explicit invocation if you need a specific agent

**Multiple agents producing conflicting advice:**
- This is normal - different specialists may have different priorities
- Ask for clarification: "Reconcile the recommendations from security-auditor and performance-engineer"

**Agent seems to lack context:**
- Provide background information in your request
- Reference previous conversations or established patterns

### Getting Help

If agents aren't working as expected:
1. Check agent descriptions in their individual files
2. Try more specific language in your requests
3. Use explicit invocation to test specific agents
4. Provide more context about your project and goals

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Learn More

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Subagents Documentation](https://docs.anthropic.com/en/docs/claude-code/sub-agents)
- [Claude Code GitHub](https://github.com/anthropics/claude-code)
