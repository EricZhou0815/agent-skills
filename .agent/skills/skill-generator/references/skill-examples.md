# Skill Examples

This document provides complete, real-world skill examples showing different patterns and design choices.

---

## Example 1: Instruction-Only Skill

**Pattern**: Simple workflow guidance without scripts or references  
**Use when**: Procedural knowledge is sufficient, no repeated code needed

```markdown
---
name: git-workflow
description: Guides developers through common Git workflows including branching, merging, rebasing, and conflict resolution. Use when users need help with Git operations like "how to rebase", "resolve merge conflict", "create a branch", "cherry-pick commits", or any Git-related tasks.
---

# Git Workflow Guide

## Common Workflows

### Creating a Feature Branch

1. Ensure you're on the main branch:
   \`\`\`bash
   git checkout main
   git pull origin main
   \`\`\`

2. Create and switch to a new branch:
   \`\`\`bash
   git checkout -b feature/your-feature-name
   \`\`\`

3. Make your changes and commit:
   \`\`\`bash
   git add .
   git commit -m "feat: add your feature description"
   \`\`\`

### Resolving Merge Conflicts

1. Identify conflicted files:
   \`\`\`bash
   git status
   \`\`\`

2. Open each conflicted file and look for conflict markers:
   \`\`\`
   <<<<<<< HEAD
   Your changes
   =======
   Their changes
   >>>>>>> branch-name
   \`\`\`

3. Edit the file to resolve conflicts, removing markers

4. Stage and commit the resolution:
   \`\`\`bash
   git add <resolved-file>
   git commit -m "chore: resolve merge conflicts"
   \`\`\`

### Rebasing

1. Fetch latest changes:
   \`\`\`bash
   git fetch origin
   \`\`\`

2. Rebase your branch:
   \`\`\`bash
   git rebase origin/main
   \`\`\`

3. If conflicts occur, resolve them and continue:
   \`\`\`bash
   git add <resolved-files>
   git rebase --continue
   \`\`\`

4. Force push if needed:
   \`\`\`bash
   git push --force-with-lease
   \`\`\`
```

**Design notes**:
- No scripts needed - Git commands are straightforward
- All content in SKILL.md (under 200 lines)
- Clear step-by-step instructions
- Uses imperative form throughout

---

## Example 2: Script-Based Skill

**Pattern**: Automation with reusable scripts  
**Use when**: Same code is rewritten repeatedly, deterministic operations needed

```markdown
---
name: pdf-editor
description: Comprehensive PDF manipulation including form filling, text extraction, merging, splitting, and rotation. Use when working with PDF files for: (1) Filling forms, (2) Extracting text/data, (3) Merging or splitting PDFs, (4) Rotating pages, (5) Adding annotations. Triggers: "edit PDF", "fill PDF form", "extract from PDF", "merge PDFs", "rotate PDF pages".
---

# PDF Editor

## Quick Start

Common PDF operations use the bundled scripts in \`scripts/\`.

### Fill PDF Forms

Use \`scripts/fill_form.py\` to populate PDF form fields:

\`\`\`bash
python scripts/fill_form.py input.pdf output.pdf --data form_data.json
\`\`\`

**Data format** (\`form_data.json\`):
\`\`\`json
{
  "field_name_1": "value1",
  "field_name_2": "value2"
}
\`\`\`

### Extract Text

Use \`scripts/extract_text.py\`:

\`\`\`bash
python scripts/extract_text.py input.pdf output.txt
\`\`\`

### Merge PDFs

Use \`scripts/merge_pdfs.py\`:

\`\`\`bash
python scripts/merge_pdfs.py output.pdf file1.pdf file2.pdf file3.pdf
\`\`\`

### Rotate Pages

Use \`scripts/rotate_pdf.py\`:

\`\`\`bash
python scripts/rotate_pdf.py input.pdf output.pdf --rotation 90
\`\`\`

## Advanced Usage

For complex operations, combine scripts or modify them as needed. All scripts are in \`scripts/\` and can be read for customization.
```

**Bundled scripts** (in `scripts/`):
- `fill_form.py` - Fills PDF form fields from JSON
- `extract_text.py` - Extracts text from PDF
- `merge_pdfs.py` - Merges multiple PDFs
- `rotate_pdf.py` - Rotates PDF pages

**Design notes**:
- Scripts handle repetitive, error-prone operations
- SKILL.md shows usage, not implementation
- Scripts are self-contained and tested
- Clear examples for each operation

---

## Example 3: Multi-Framework Skill

**Pattern**: Progressive disclosure for multiple variants  
**Use when**: Supporting multiple frameworks/platforms with variant-specific details

```markdown
---
name: cloud-deploy
description: Deploys applications to cloud platforms (AWS, GCP, Azure) with infrastructure as code. Use when deploying applications, setting up cloud infrastructure, or managing cloud resources. Triggers: "deploy to AWS", "deploy to GCP", "deploy to Azure", "set up cloud infrastructure", "create cloud resources".
---

# Cloud Deployment

## Overview

Deploy applications to major cloud platforms with automated infrastructure provisioning.

## Workflow

### 1. Choose Cloud Provider

Select your target platform:
- **AWS** - See [references/aws.md](references/aws.md)
- **GCP** - See [references/gcp.md](references/gcp.md)
- **Azure** - See [references/azure.md](references/azure.md)

### 2. Prepare Application

Ensure your application has:
- Dockerfile (for containerized deployments)
- Environment configuration
- Dependencies documented

### 3. Configure Infrastructure

Each provider has specific configuration:
- AWS: CloudFormation or Terraform
- GCP: Deployment Manager or Terraform
- Azure: ARM templates or Terraform

See provider-specific guides in \`references/\` for details.

### 4. Deploy

Run the deployment script for your provider:

\`\`\`bash
python scripts/deploy.py --provider <aws|gcp|azure> --config config.yaml
\`\`\`

### 5. Verify

Check deployment status and health endpoints.
```

**Bundled references** (in `references/`):
- `aws.md` - AWS-specific deployment patterns, services, and examples
- `gcp.md` - GCP-specific deployment patterns, services, and examples
- `azure.md` - Azure-specific deployment patterns, services, and examples

**Design notes**:
- SKILL.md stays lean with overview and workflow
- Provider-specific details in separate references
- Claude loads only the relevant reference
- Avoids bloating context with unused information

---

## Example 4: Reference-Heavy Skill

**Pattern**: Detailed documentation and schemas  
**Use when**: Complex domain knowledge, API docs, or extensive reference material needed

```markdown
---
name: company-api
description: Integrates with internal company APIs including user management, billing, analytics, and reporting. Use when working with company systems, querying internal data, or automating business processes. Triggers: "query user data", "get billing info", "run analytics report", "call company API".
---

# Company API Integration

## Overview

Access company systems through standardized REST APIs.

## Quick Start

1. **Authentication**: All APIs require OAuth2 tokens
2. **Base URL**: \`https://api.company.com/v1\`
3. **Rate Limits**: 1000 requests/hour per token

## API Categories

### User Management API

See [references/user-api.md](references/user-api.md) for:
- User CRUD operations
- Authentication endpoints
- Role management
- Complete schema documentation

### Billing API

See [references/billing-api.md](references/billing-api.md) for:
- Invoice retrieval
- Payment processing
- Subscription management
- Billing schemas

### Analytics API

See [references/analytics-api.md](references/analytics-api.md) for:
- Report generation
- Metrics queries
- Data export
- Analytics schemas

## Common Patterns

### Making Authenticated Requests

\`\`\`python
import requests

headers = {
    "Authorization": f"Bearer {token}",
    "Content-Type": "application/json"
}

response = requests.get(
    "https://api.company.com/v1/users",
    headers=headers
)
\`\`\`

### Error Handling

All APIs return standard error format:
\`\`\`json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable message"
  }
}
\`\`\`

See individual API references for specific error codes.
```

**Bundled references** (in `references/`):
- `user-api.md` - Complete user API documentation with schemas
- `billing-api.md` - Complete billing API documentation with schemas
- `analytics-api.md` - Complete analytics API documentation with schemas

**Design notes**:
- SKILL.md provides navigation and common patterns
- Detailed API docs in separate references
- Each reference has table of contents for large files
- Claude loads only needed API documentation

---

## Key Takeaways

1. **Instruction-only**: Best for simple workflows, no repeated code
2. **Script-based**: Best for automation, deterministic operations
3. **Multi-framework**: Use progressive disclosure to avoid context bloat
4. **Reference-heavy**: Keep SKILL.md as navigation, details in references

Choose the pattern that fits your skill's purpose. Patterns can be combined as needed.
