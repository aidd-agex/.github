# GitHub Issue Template Guide

## 📊 Issue Hierarchy System

We use a 4-level hierarchy to organize our work:

```
Epic (Highest Level)
  └─ Story
      └─ Feature  
          └─ Subtask (Lowest Level)
```

### Hierarchy Levels

| Level | Purpose | Example | Typical Duration |
|-------|---------|---------|-----------------|
| **Epic** | Large body of work with business value | "User Authentication System" | Weeks to months |
| **Story** | User-focused requirement | "As a user, I want to login with email" | Days to 2 weeks |
| **Feature** | Specific functionality | "Login API endpoint" | Hours to days |
| **Subtask** | Atomic work item | "Implement password validation" | Hours to 1 day |

### When to Use Each Level

#### 🎯 Epic
- Represents a major initiative or project
- Contains multiple Stories
- Has clear business objectives and success metrics
- Example: "Mobile App Launch", "AI Chat Feature", "Performance Optimization"

#### 📖 Story  
- Describes functionality from user perspective
- Follows "As a [user], I want [action], so that [benefit]" format
- Contains multiple Features
- Has acceptance criteria
- Example: "As a user, I want to search chat history so that I can find past conversations"

#### ⚡ Feature
- Specific technical implementation
- Contains multiple Subtasks
- Has detailed technical requirements
- Example: "Chat history search API", "Search UI component", "Search indexing"

#### 📝 Subtask
- Smallest unit of work
- Typically assigned to one developer
- Can be completed in a single work session
- Example: "Write unit tests for search API", "Add search icon to navbar"

## 🔗 Linking Issues

Always link child issues to their parents:

1. **When creating a Story**: Add the parent Epic number in the "Parent Epic" field (e.g., `#123`)
2. **When creating a Feature**: Add the parent Story number in the "Parent Story" field (e.g., `#456`)
3. **When creating a Subtask**: Add the parent Feature number in the "Parent Feature" field (e.g., `#789`)

### Updating Parent Issues

After creating child issues, **update the parent issue** to list all children:

**Epic Example:**
```markdown
### 📦 Child Stories
- #456 Story: User Login
- #457 Story: User Registration  
- #458 Story: Password Reset
```

**Story Example:**
```markdown
### 🔧 Child Features
- #789 Feature: Login API
- #790 Feature: Login UI
- #791 Feature: Session Management
```

**Feature Example:**
```markdown
### 📝 Child Subtasks
- #1001 Subtask: API endpoint implementation
- #1002 Subtask: Unit tests
- #1003 Subtask: Integration tests
```

## 👥 Owner Fields

### Organization-Level Templates (Simplified)

The organization-level templates use **text input fields** instead of dropdowns for better flexibility:

- **Product Owner**: Enter GitHub username(s) with @mention (e.g., `@username` or `@user1 @user2`)
- **Dev Owner**: Enter GitHub username(s) with @mention
- **QA Owner**: Enter GitHub username(s) with @mention

This approach allows:
- ✅ No maintenance of long dropdown lists
- ✅ Easy to mention multiple people
- ✅ Works across all projects
- ✅ People get notified automatically via @mentions

### Project-Level Templates (With Dropdowns)

Projects can override templates to add dropdown menus with project-specific team members. See [Customization Guide](#-customization-for-projects) below.

## 🔧 Component Fields

### Organization-Level (Text Input)

Components use text input for flexibility:
- Enter component(s) separated by commas
- Example: `Web, Backend, iOS App`

### Project-Level (Dropdown)

Projects can override to provide dropdown menus with predefined components:
- Web
- iOS App
- Android App
- Backend
- Prompt
- etc.

## 📋 Best Practices

### 1. Start from the Top
- Create Epic first
- Break it down into Stories
- Break Stories into Features
- Break Features into Subtasks

### 2. Keep It Organized
- Always link child to parent
- Update parent with child list
- Use consistent naming conventions

### 3. Size Guidelines
- **Epic**: 4-12 weeks of work
- **Story**: 3-10 days of work
- **Feature**: 4 hours - 3 days of work
- **Subtask**: 1-8 hours of work

### 4. Atomic Subtasks
- Each Subtask should be:
  - Independently testable
  - Completable in one sitting
  - Clearly defined
  - Assigned to one person

### 5. Clear Titles
Use descriptive prefixes:
- ✅ `[Epic]: User Authentication System`
- ✅ `[Story]: User can login with email`
- ✅ `[Feature]: Login API endpoint`
- ✅ `[Subtask]: Add email validation`

❌ Avoid vague titles:
- ❌ `[Feature]: Fix stuff`
- ❌ `[Story]: Update things`

## 🔄 Workflow Example

### Scenario: Adding Chat Export Feature

1. **Create Epic** (#100)
   ```
   Title: [Epic]: Chat History Management
   Components: Web, iOS App, Android App, Backend
   ```

2. **Create Stories** under Epic #100
   ```
   #101 [Story]: User can export chat history
   #102 [Story]: User can search chat history
   #103 [Story]: User can filter chat by date
   ```

3. **Create Features** under Story #101
   ```
   #110 [Feature]: Export to PDF
   #111 [Feature]: Export to TXT
   #112 [Feature]: Export UI button
   ```

4. **Create Subtasks** under Feature #110
   ```
   #120 [Subtask]: Implement PDF generation library
   #121 [Subtask]: Format chat messages for PDF
   #122 [Subtask]: Add download button
   #123 [Subtask]: Write unit tests
   ```

## 🎨 Customization for Projects

### When to Customize

Projects should create their own `.github/ISSUE_TEMPLATE/` directory if they need:
- Project-specific team member dropdowns
- Project-specific component lists
- Custom validation rules
- Additional fields

### How to Customize

1. **Copy templates** from `aidd-agex/.github` repository
2. **Modify owner fields** from text input to dropdown:

```yaml
# Organization template (text input):
- type: input
  id: dev_owner
  attributes:
    label: Dev Owner
    placeholder: "@username"

# Project template (dropdown):
- type: dropdown
  id: dev_owner
  attributes:
    label: Dev Owner
    multiple: true
    options:
      - "@alice"
      - "@bob"
      - "@charlie"
```

3. **Modify component field** from text to dropdown:

```yaml
# Organization template (text input):
- type: input
  id: component
  attributes:
    label: Component(s)
    placeholder: "Web, Backend"

# Project template (dropdown):
- type: dropdown
  id: component
  attributes:
    label: Component
    multiple: true
    options:
      - Web
      - iOS App
      - Android App
      - Backend
```

4. **Place in your repository** at `.github/ISSUE_TEMPLATE/`

### Keeping Templates in Sync

When organization templates are updated:
1. Review structural changes in `aidd-agex/.github`
2. Merge improvements while keeping your customizations
3. Test templates in your project

## 🏷️ Labels Reference

| Label | Usage |
|-------|-------|
| `epic` | Applied to Epic issues |
| `story` | Applied to Story issues |
| `feature` | Applied to Feature issues |
| `subtask` | Applied to Subtask issues |
| `bug` | Bug reports |
| `needs-triage` | Auto-applied, needs review |

## 🆘 Need Help?

- Questions about hierarchy? Ask in team chat
- Template issues? Open a bug report in `.github` repository
- Suggestions? Open a feature request

## 📝 Template Changelog

### v2.0 (Organization-Level)
- ✨ Added Epic, Story, Feature, Subtask hierarchy
- ✨ Simplified owner fields to text input (with @mentions)
- ✨ Simplified component field to text input
- ✨ Improved flexibility across projects
- 📚 Created comprehensive customization guide

### v1.0 (Legacy Project-Level)
- Basic bug_report and feature_request templates
- Project-specific dropdown fields

