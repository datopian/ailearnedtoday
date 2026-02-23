# The Design Repo Pattern: Keep Your Inspiration Separate from Your Code

**Status**: Draft  
**Created**: 2026-02-23

A simple organizational pattern for managing design work, inspiration, and exploration without polluting your main application repository.

## The Problem

When working on a project, you naturally accumulate:
- Screenshots and examples from other sites
- Design inspiration and references
- Preliminary designs and mockups
- Notes about visual direction and UX patterns
- HTML prototypes and experiments

The question is: where do you put all this?

### Option 1: Main App Repo
Dumping everything into your main application repository has downsides:
- Clutters the codebase with non-code assets
- Mixes design artifacts with production code
- Makes the repo history noisy
- Complicates CI/CD and deployment

### Option 2: External Tools (Pinterest, Figma, etc.)
Using external design tools is common, but:
- Assets are scattered across multiple platforms
- Hard to work with AI agents on the content
- Version control is limited or absent
- Not easily searchable or referenceable from code

## The Solution: A Dedicated Design Repo

Create a separate repository specifically for design work:

```
your-project-design/
├── inspiration/
│   ├── README.md           # Index of all inspiration
│   ├── navigation.md       # Navigation examples
│   ├── typography.md       # Typography references
│   └── layouts.md          # Layout patterns
├── designs/
│   ├── home-v1.html        # HTML prototypes
│   ├── home-v2.html
│   └── dashboard-mockup.html
├── notes/
│   ├── design-principles.md
│   ├── color-palette.md
│   └── user-flows.md
└── assets/
    └── screenshots/        # Collected screenshots and images
```

## How It Works

### 1. Collecting Inspiration
Instead of saving to Pinterest or bookmarks:
- Take a screenshot
- Drop it in `assets/screenshots/`
- Reference it in the appropriate `inspiration/*.md` file
- Add context: what you liked, why it's relevant, how it might apply

Example `inspiration/navigation.md`:
```markdown
# Navigation Patterns

## Sticky Header with Dropdown
![Example from Stripe](../assets/screenshots/stripe-nav-2026-02-23.png)

What works:
- Clear hierarchy
- Subtle shadow on scroll
- Minimal but complete

Considerations for our project:
- Could adapt the dropdown transition
- Similar color contrast approach
```

### 2. Working with AI
Having everything in markdown and version-controlled means:
- AI agents can read and reference your inspiration library
- You can ask: "Look at the navigation examples in inspiration/ and suggest an approach for our site"
- Context is preserved and queryable
- Changes are tracked via git history

### 3. Prototyping
Drop HTML mockups directly into `designs/`:
- Self-contained HTML files with inline CSS
- Easy to open in a browser and iterate
- Can be referenced by AI: "Update home-v1.html based on the feedback in notes/"
- No build step required for early exploration

### 4. Design Notes and Decisions
Use `notes/` for:
- Design principles and guidelines
- Rationale for key decisions
- Color palettes and typography choices
- User flow diagrams (as markdown + mermaid)

## Benefits

### Organization
- Clear separation of concerns
- Design work doesn't clutter the application repo
- Easy to onboard designers or get second opinions

### AI-Friendly
- All content is version-controlled and in plain text (markdown)
- AI agents can read, reference, and work with the entire design context
- Prompts like "review the inspiration folder and suggest a design direction" become possible

### Collaborative
- Can be public or private
- Easy to share with collaborators
- Git-based workflow (branch, PR, merge)
- Design evolution is visible in commit history

### Portable
- Not locked into a proprietary platform
- Can reference from documentation
- Easy to archive or fork for related projects

## Public vs Private

**Public** (default):
- Transparency about design decisions
- Community can contribute inspiration or feedback
- Sets an example for others

**Private**:
- If you're working on something not yet launched
- If you want to iterate without external input
- Can always flip to public later

## Getting Started

1. Create a new repo: `your-project-design`
2. Set up the basic structure (inspiration/, designs/, notes/, assets/)
3. Start dumping inspiration immediately — don't overthink it
4. Add a README explaining the structure and purpose
5. Reference it from your main project's README or docs

## Variations

### Monorepo Approach
If you prefer, you can create a `/design` directory in your main repo but keep it clearly separated from `/src` or `/app`. The key is maintaining the separation between design artifacts and production code.

### Design Systems
For larger projects, this design repo can evolve into a full design system:
- Component library documentation
- Token definitions (colors, spacing, typography)
- Usage guidelines
- Accessibility notes

## Example Prompt for AI

With a design repo in place, you can prompt an AI agent like:

> "I'm working on the homepage. Review the layouts in `inspiration/layouts.md` and the color palette in `notes/color-palette.md`. Then update `designs/home-v1.html` to incorporate the hero pattern from the second Stripe example and our brand colors."

The agent has all the context it needs in one place.

## Why This Matters for AI Agents

As AI agents become more capable at design and development, having a well-organized, version-controlled design context becomes crucial:
- Agents need reference material to generate good designs
- Context is everything — scattered inspiration is hard to leverage
- Version control lets you track what the agent suggested and why
- Separation prevents the agent from accidentally modifying production code when experimenting with designs

## Related Patterns

- **AGENTS.md** — project-specific instructions for AI agents (OpenClaw pattern)
- **Design tokens** — extracting design decisions into reusable variables
- **Living style guides** — documentation that stays in sync with the codebase
- **Sketchbooks and lab projects** — dedicated spaces for experimentation

---

## Discussion

This pattern emerged from working with AI agents on design tasks. The key insight: **inspiration and exploration need a home that's separate from production code but still structured enough to be useful**.

What do you think? Would you make this public or private? How would you structure the `inspiration/` folder differently?

---

*This is a draft. Feedback welcome.*
