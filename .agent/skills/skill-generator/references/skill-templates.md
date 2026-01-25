# Skill Templates

Ready-to-use SKILL.md templates for common skill types. Copy, customize, and use.

---

## Template 1: Instruction-Only Skill

**Use for**: Workflow guidance, procedural knowledge, simple task instructions

```markdown
---
name: your-skill-name
description: [TODO: What does this skill do? When should it trigger? Include specific scenarios, keywords, and example phrases users might say. Be comprehensive - this determines when the skill loads.]
---

# Your Skill Title

## Overview

[1-2 sentences explaining what this skill enables]

## Quick Start

[Minimal example to get started immediately]

## Common Workflows

### Workflow 1: [Task Name]

[Step-by-step instructions using imperative form]

1. [First step with example]
2. [Second step with example]
3. [Third step with example]

### Workflow 2: [Task Name]

1. [First step]
2. [Second step]
3. [Third step]

## Advanced Usage

[Optional: More complex scenarios or edge cases]

## Troubleshooting

[Optional: Common issues and solutions]
```

**Customization checklist**:
- [ ] Update `name` to match directory name
- [ ] Write comprehensive `description` with triggers
- [ ] Replace all `[TODO]` and `[Task Name]` placeholders
- [ ] Add concrete examples for each workflow
- [ ] Use imperative form ("Do this" not "You should do this")
- [ ] Delete unused sections (Advanced Usage, Troubleshooting)

---

## Template 2: Script-Based Skill

**Use for**: Automation tasks, repeated code, deterministic operations

```markdown
---
name: your-skill-name
description: [TODO: What does this skill automate? When should it trigger? Include file types, operations, and example phrases. Example: "Processes CSV files with data cleaning, transformation, and export. Use when working with CSV data for: (1) cleaning, (2) transforming, (3) merging. Triggers: 'clean CSV', 'process data file', 'merge CSV files'."]
---

# Your Skill Title

## Overview

[1-2 sentences explaining what this skill automates]

## Quick Start

The most common operation:

\`\`\`bash
python scripts/main_script.py input.file output.file [options]
\`\`\`

## Available Scripts

### Script 1: [Operation Name]

**Purpose**: [What this script does]

**Usage**:
\`\`\`bash
python scripts/script1.py [arguments]
\`\`\`

**Example**:
\`\`\`bash
python scripts/script1.py input.txt output.txt --option value
\`\`\`

### Script 2: [Operation Name]

**Purpose**: [What this script does]

**Usage**:
\`\`\`bash
python scripts/script2.py [arguments]
\`\`\`

**Example**:
\`\`\`bash
python scripts/script2.py data.csv --format json
\`\`\`

## Advanced Usage

[Optional: Combining scripts, customization options]

## Script Reference

All scripts are in \`scripts/\` and can be read for customization or debugging.
```

**Bundled scripts** (create in `scripts/`):
- `main_script.py` - Primary automation script
- `helper_script.py` - Supporting operations
- Test each script before packaging

**Customization checklist**:
- [ ] Update `name` and `description`
- [ ] Create actual scripts in `scripts/` directory
- [ ] Test all scripts to ensure they work
- [ ] Document all script arguments and options
- [ ] Provide realistic examples for each script
- [ ] Delete example scripts from init template

---

## Template 3: Reference-Heavy Skill

**Use for**: API documentation, schemas, domain knowledge, extensive reference material

```markdown
---
name: your-skill-name
description: [TODO: What domain/API does this cover? When should it trigger? Include specific systems, data types, or operations. Example: "Provides schemas and documentation for company database including user tables, product catalog, and order management. Use when querying company data, understanding database structure, or writing SQL queries."]
---

# Your Skill Title

## Overview

[1-2 sentences explaining what knowledge this skill provides]

## Quick Reference

[Most commonly needed information - keep this section brief]

## Documentation Structure

This skill includes detailed reference documentation:

### [Category 1]

See [references/category1.md](references/category1.md) for:
- [Topic A]
- [Topic B]
- [Topic C]

### [Category 2]

See [references/category2.md](references/category2.md) for:
- [Topic D]
- [Topic E]
- [Topic F]

### [Category 3]

See [references/category3.md](references/category3.md) for:
- [Topic G]
- [Topic H]
- [Topic I]

## Common Patterns

[Show 2-3 most common usage patterns with examples]

### Pattern 1: [Use Case]

\`\`\`
[Example code or usage]
\`\`\`

### Pattern 2: [Use Case]

\`\`\`
[Example code or usage]
\`\`\`
```

**Bundled references** (create in `references/`):
- `category1.md` - Detailed documentation for category 1
- `category2.md` - Detailed documentation for category 2
- `category3.md` - Detailed documentation for category 3

**Reference file structure** (for files >100 lines, add TOC):
```markdown
# Category Name

## Table of Contents
- [Section 1](#section-1)
- [Section 2](#section-2)
- [Section 3](#section-3)

## Section 1
[Content]

## Section 2
[Content]

## Section 3
[Content]
```

**Customization checklist**:
- [ ] Update `name` and `description`
- [ ] Create reference files in `references/` directory
- [ ] Add table of contents to large reference files
- [ ] Link references clearly from SKILL.md
- [ ] Keep SKILL.md as navigation (under 300 lines)
- [ ] Show common patterns in SKILL.md, details in references

---

## Template 4: Tool Integration Skill

**Use for**: API integrations, external service connections, third-party tools

```markdown
---
name: your-tool-name
description: [TODO: What tool/service does this integrate? When should it trigger? Include service name, operations, and example phrases. Example: "Integrates with Stripe API for payment processing, subscription management, and customer billing. Use when handling payments, managing subscriptions, or querying billing data. Triggers: 'create Stripe payment', 'manage subscription', 'get customer billing'."]
---

# Your Tool Integration

## Overview

[1-2 sentences explaining what this integration enables]

## Setup

### Authentication

[How to authenticate with the service]

\`\`\`
[Example authentication code]
\`\`\`

### Configuration

[Required configuration, environment variables, API keys]

## Core Operations

### Operation 1: [Action Name]

**Purpose**: [What this operation does]

**Example**:
\`\`\`python
[Code example showing the operation]
\`\`\`

**Parameters**:
- \`param1\`: [Description]
- \`param2\`: [Description]

**Returns**: [What the operation returns]

### Operation 2: [Action Name]

**Purpose**: [What this operation does]

**Example**:
\`\`\`python
[Code example]
\`\`\`

**Parameters**:
- \`param1\`: [Description]
- \`param2\`: [Description]

**Returns**: [What the operation returns]

## Error Handling

[Common errors and how to handle them]

\`\`\`python
try:
    # Operation
except SpecificError as e:
    # Handle error
\`\`\`

## Advanced Usage

[Optional: Complex scenarios, webhooks, batch operations]

## API Reference

For complete API documentation, see [references/api-docs.md](references/api-docs.md)
```

**Optional bundled resources**:
- `references/api-docs.md` - Complete API reference
- `scripts/api_helper.py` - Helper functions for common operations

**Customization checklist**:
- [ ] Update `name` and `description`
- [ ] Document authentication clearly
- [ ] Show examples for each core operation
- [ ] Include error handling patterns
- [ ] Add API reference if extensive
- [ ] Test all code examples

---

## Choosing the Right Template

| Skill Type | Template | When to Use |
|------------|----------|-------------|
| Workflow guidance | Instruction-Only | Simple procedures, no repeated code |
| Automation | Script-Based | Repeated operations, deterministic tasks |
| Documentation | Reference-Heavy | Extensive knowledge, schemas, API docs |
| Service integration | Tool Integration | External APIs, third-party services |

**Mix and match**: Templates can be combined. For example, a tool integration skill might include both scripts and reference documentation.

---

## After Customizing

1. Delete all `[TODO]` and placeholder text
2. Test any scripts or code examples
3. Validate with `python scripts/quick_validate.py`
4. Package with `python scripts/package_skill.py`

Your skill is ready to use!
