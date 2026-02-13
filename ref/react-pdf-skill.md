---
created: 2026-02-13
author: Alexey Taktarov (@mlfrg / molefrog)
tags: [claude-code, skills, pdf, react-pdf, document-generation, design]
---

# React-PDF Skill - High-Quality PDF Generation for Claude Code

**A Claude Code skill for generating professional PDF documents using React-PDF (@react-pdf/renderer).**

## Links

- **GitHub:** https://github.com/molefrog/skills
- **Twitter:** @mlfrg
- **Announcement:** https://x.com/mlfrg/status/2021998333263519879
- **React-PDF:** https://react-pdf.org/
- **Author Website:** https://molefrog.com

## What Is It?

A Claude Code skill that enables AI agents to generate high-quality PDFs using React-PDF, a React renderer for creating PDF documents using React components.

**Install:**
```bash
npx skills add molefrog/skills --skill react-pdf

# or as a Claude Code plugin
/plugin marketplace add molefrog/skills
/plugin install react-pdf@skills
```

## What Problem Does It Solve?

### Traditional PDF Generation Issues
Python PDF libraries (ReportLab, WeasyPrint, fpdf2) work, but have limitations:
- **Absolute coordinate math** - Complex positioning calculations
- **Imperative APIs** - Step-by-step drawing instructions
- **Limited layout engines** - No modern layout (flexbox, grid)
- **Separate graphics libraries** - Complex integration for charts/icons
- **Manual typesetting** - Poor line breaking and hyphenation

### React-PDF Advantages for AI-Generated Documents

**1. Flexbox & Grid Layout**
- Powered by Yoga (Facebook's layout engine)
- Centering, columns, wrapping grids — it just works
- No absolute coordinate math needed

**2. SVG Primitives**
- `<Svg>`, `<Path>`, `<Circle>` are first-class components
- Draw charts and icons inline
- No separate graphics library required

**3. Component Composition**
- Build PDFs like React components
- Reusable headers, tables, cards — all composable with props
- **Declarative, not imperative**

**4. Google Fonts Support**
- Register any TrueType font with `Font.register()`
- Skill bundles ~65 popular Google Fonts with direct download URLs
- Professional typography out of the box

**5. Knuth-Plass Line Breaking**
- Same algorithm used by TeX
- Produces professionally typeset paragraphs
- Proper hyphenation built-in

**6. Smart Page Breaks**
- `wrap`, `break`, `minPresenceAhead` control content flow declaratively
- Orphan/widow control built-in
- No manual page management

**7. Emoji Support**
- Register Twemoji assets
- Use emoji directly in text
- No custom rendering logic needed

## How It Works

The skill provides Claude Code with knowledge and patterns for using React-PDF:

### Example Document Structure

```jsx
import { Document, Page, Text, View, StyleSheet } from '@react-pdf/renderer';

const styles = StyleSheet.create({
  page: { flexDirection: 'column', padding: 30 },
  section: { margin: 10, padding: 10, flexGrow: 1 }
});

const MyDocument = () => (
  <Document>
    <Page size="A4" style={styles.page}>
      <View style={styles.section}>
        <Text>Section #1</Text>
      </View>
      <View style={styles.section}>
        <Text>Section #2</Text>
      </View>
    </Page>
  </Document>
);
```

### Key Features

**Layout:**
- Flexbox: `flexDirection`, `justifyContent`, `alignItems`
- Grid: Multi-column layouts
- Auto-wrapping: Content flows naturally

**Typography:**
- Custom fonts
- Professional line breaking (Knuth-Plass algorithm)
- Hyphenation
- Text styling (bold, italic, color, size)

**Graphics:**
- SVG components inline
- Charts and diagrams
- Icons and illustrations

**Document Structure:**
- Multi-page documents
- Headers and footers
- Page numbering
- Table of contents

## Why This Matters for AI Agents

### Declarative > Imperative

AI agents work better with declarative APIs:
- **React-PDF:** "Here's a centered column with three items"
- **Traditional PDF libs:** "Move cursor to (x, y), draw line, move to (x2, y2)..."

The React component model is more natural for LLMs to reason about.

### Professional Output

React-PDF's sophisticated typography (Knuth-Plass) and layout (Yoga) produce documents that look professionally designed, not AI-generated.

### Composability

AI agents can build complex documents by composing simple components:
```jsx
<Invoice>
  <Header company={data} />
  <LineItems items={data.items} />
  <Footer total={data.total} />
</Invoice>
```

This is much easier for AI to understand and manipulate than low-level drawing commands.

## Use Cases

### Business Documents
- Invoices
- Reports
- Proposals
- Contracts

### Technical Documentation
- API documentation
- User manuals
- Technical specifications
- Architecture diagrams

### Creative Documents
- Newsletters
- Brochures
- Presentations (as PDFs)
- Portfolios

### Data Visualization
- Charts and graphs
- Infographics
- Dashboards
- Analytics reports

## Comparison: React-PDF vs Traditional Libraries

| Feature | React-PDF | ReportLab/WeasyPrint |
|---------|-----------|----------------------|
| **Layout** | Flexbox, Grid (Yoga) | Absolute positioning |
| **API Style** | Declarative | Imperative |
| **Typography** | Knuth-Plass | Basic |
| **SVG** | First-class components | Separate library |
| **Composition** | React components | Manual functions |
| **Fonts** | Easy (Font.register) | Manual embedding |
| **Page Breaks** | Declarative (wrap/break) | Manual calculations |
| **AI-Friendly** | ✅ Very | ❌ Less so |

## Philosophy Alignment

React-PDF aligns with modern AI-assisted development:

### From [[steve-yegge]]'s vibe coding:
- Declarative > imperative
- Composition > manual assembly
- Best-effort outputs that look professional

### From [[crawshaw-eight-more-months-agents]]:
> "The best software for an agent is whatever is best for a programmer."

React-PDF was built for human developers. Turns out it's also perfect for AI agents.

### Skills as Agent Superpowers

This skill represents a trend: giving AI agents domain expertise through curated knowledge packages. Instead of hoping the LLM knows about React-PDF, the skill provides:
- Best practices
- Common patterns
- Font references
- Layout recipes

## Who Created It

**Alexey Taktarov** (@mlfrg / molefrog)
- Creator of [wouter](https://github.com/molefrog/wouter) - minimalist React routing library (~2.1KB)
- GitHub: https://github.com/molefrog
- Website: https://molefrog.com

Part of the growing ecosystem of Claude Code skills and agent tooling.

## Installation Details

**As a skill:**
```bash
npx skills add molefrog/skills --skill react-pdf
```

**As a plugin:**
```bash
/plugin marketplace add molefrog/skills
/plugin install react-pdf@skills
```

Once installed, Claude Code can generate PDF documents using React-PDF patterns automatically.

## Example: What Claude Can Do

**Prompt:** "Generate an invoice PDF for Acme Corp"

**Claude (with react-pdf skill):**
- Creates a Document component
- Uses flexbox for layout
- Registers fonts for professional typography
- Adds SVG logo
- Properly breaks pages
- Exports clean, professional PDF

**Without the skill:** Claude might try to use fpdf2 or similar, resulting in coordinate math and manual positioning.

## Why It's Noteworthy

This skill demonstrates:

1. **AI agents benefit from domain-specific knowledge** - React-PDF is better for PDFs than general coding knowledge
2. **Declarative > imperative for AI** - Component composition is more LLM-friendly
3. **Professional output matters** - Knuth-Plass typography and Yoga layout produce better results
4. **Skills are AI superpowers** - Curated knowledge packages make agents more capable

## Related Skills & Tools

- [[github-spec-kit]] - Spec-driven development with structured knowledge
- [[openspec.dev]] - Planning with artifacts
- [[onecontext]] - Context management for agents
- Claude Code skills ecosystem

## Technical Details

**Based on:**
- React-PDF (@react-pdf/renderer)
- Yoga layout engine (Facebook)
- Knuth-Plass line breaking algorithm (TeX)
- Twemoji for emoji rendering

**Bundled resources:**
- ~65 Google Fonts with direct download URLs
- Reference documentation
- Common patterns and recipes

## License

MIT

## Why This Matters

PDF generation is a common task in business applications. By providing a skill that uses React-PDF's declarative, component-based API instead of imperative Python libraries, molefrog has made it easier for AI agents to generate professional-quality documents.

This is part of a broader trend: **building the right abstractions for AI agents**, not just porting existing tools.
