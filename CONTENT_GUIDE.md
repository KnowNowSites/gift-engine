# Content Creation Guide - Gift Engine

A comprehensive guide for creating and managing content for the Gift Engine affiliate website.

## Content Overview

Gift Engine publishes thoughtful gift recommendations organized by:
- **Relationships**: Partners, spouses, family members
- **Emotional Situations**: Difficult times, celebrations, milestones
- **Constraints**: Budget, time, location, preferences

## Creating a New Guide

### Step 1: Plan Your Content

Before writing, consider:
- **Target Audience**: Who is this guide for?
- **Emotional Context**: What situation are they in?
- **Relationship Type**: What's their relationship to the recipient?
- **Budget Range**: What price points should be covered?
- **Unique Angle**: What makes this guide different?

### Step 2: Create the Markdown File

1. Create a new file in `src/content/guides/`
2. Use descriptive filename: `kebab-case-guide-title.md`
3. Example: `thoughtful-gifts-girlfriend-hard-time.md`

### Step 3: Add Frontmatter

Every guide starts with YAML frontmatter:

```markdown
---
title: "Your Guide Title"
description: "A compelling 150-160 character description for SEO"
category: "Relationships"  # or "Emotions" or "Constraints"
publishDate: 2024-01-15
updatedDate: 2024-01-20
author: "Gift Engine"
tags: ["tag1", "tag2", "tag3"]
---
```

### Frontmatter Fields

| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Guide title (50-60 characters for SEO) |
| `description` | Yes | Meta description (150-160 characters) |
| `category` | Yes | One of: Relationships, Emotions, Constraints |
| `publishDate` | Yes | Format: YYYY-MM-DD |
| `updatedDate` | No | Last update date |
| `author` | No | Default: "Gift Engine" |
| `tags` | No | Array of relevant tags |

## Writing Guidelines

### Structure

A well-structured guide includes:

1. **Introduction** (1-2 paragraphs)
   - Hook the reader
   - Explain the situation
   - Preview what they'll learn

2. **Main Sections** (3-5 sections)
   - Clear headings
   - 2-4 gift ideas per section
   - Explanation of why each gift works

3. **Gift Presentation** (for each gift)
   - Gift name/title
   - Brief description
   - "Why it works" explanation
   - Price range (optional)

4. **Practical Guidance** (1-2 sections)
   - Timing and presentation tips
   - Budget considerations
   - Personalization ideas

5. **Conclusion** (1 paragraph)
   - Reinforce main message
   - Call to action

### Tone and Voice

- **Warm and Empathetic**: Acknowledge the emotional context
- **Practical**: Provide actionable advice
- **Authentic**: Avoid corporate jargon
- **Helpful**: Focus on the reader's needs
- **Conversational**: Write as if speaking to a friend

### Example Structure

```markdown
---
title: "Thoughtful Gifts for [Situation]"
description: "Meaningful gift ideas for [situation]. From [type] to [type] gifts."
category: "Relationships"
publishDate: 2024-01-15
---

## Understanding the Right Gift

[Context and emotional framing]

## [Gift Category 1]

### Gift Idea 1
Description of the gift.

**Why it works:** Explanation of emotional or practical benefit.

### Gift Idea 2
[Same structure]

## [Gift Category 2]

[Repeat structure]

## Timing and Presentation

[Practical advice]

## Budget Considerations

- **Under $25:** [Options]
- **$25-$50:** [Options]
- **$50-$100:** [Options]
- **$100+:** [Options]

## Final Thoughts

[Conclusion and encouragement]
```

## Content Best Practices

### SEO Optimization

1. **Keywords**
   - Use target keywords naturally
   - Include in title, description, headings
   - Don't force keywords

2. **Headings**
   - Use H2 for main sections
   - Use H3 for subsections
   - Include keywords where natural

3. **Meta Description**
   - 150-160 characters
   - Include main keyword
   - Compelling and action-oriented

4. **Internal Links**
   - Link to related guides
   - Use descriptive anchor text
   - 2-4 links per guide

### Writing Tips

1. **Be Specific**
   - "Luxury weighted blanket" not "nice gift"
   - "Silk pillowcase" not "bedding"
   - Specific details help readers visualize

2. **Include Price Ranges**
   - Helps readers budget
   - Organize gifts by price
   - Include affiliate links at appropriate price points

3. **Explain the "Why"**
   - Why does this gift work?
   - What emotional need does it address?
   - How does it show care?

4. **Use Lists and Formatting**
   - Break up long paragraphs
   - Use bullet points for clarity
   - Bold important terms

5. **Include Practical Advice**
   - When to give the gift
   - How to present it
   - Personalization ideas

### Affiliate Link Integration

1. **Natural Integration**
   - Link to specific products
   - Use Amazon Associates or similar
   - Place links contextually, not forced

2. **Disclosure**
   - Always disclose affiliate relationships
   - Include affiliate disclosure on site
   - Be transparent with readers

3. **Link Placement**
   - Include in gift descriptions
   - Add in "Where to Buy" sections
   - Use descriptive anchor text

## Content Categories

### Relationships Category

Focus on gift-giving for specific relationships:
- Girlfriend/Boyfriend
- Wife/Husband
- Mother/Father
- Sister/Brother
- Friend
- Coworker
- Mentor

**Example Topics:**
- Gifts for long-distance relationships
- Gifts for new relationships
- Gifts for anniversaries
- Gifts for reconnecting with old friends

### Emotions Category

Focus on emotional situations:
- Difficult times (breakup, loss, illness)
- Celebrations (promotion, graduation, new home)
- Support (encouragement, motivation)
- Milestones (birthday, anniversary)

**Example Topics:**
- Gifts for someone going through a breakup
- Gifts for someone dealing with grief
- Gifts for someone starting a new job
- Gifts for someone recovering from illness

### Constraints Category

Focus on specific limitations:
- Budget constraints (under $25, under $50)
- Time constraints (last-minute gifts)
- Location constraints (long-distance)
- Preference constraints (minimalist, eco-friendly)

**Example Topics:**
- Last-minute gifts under $20
- Gifts for minimalists
- Eco-friendly gift ideas
- Gifts that ship quickly

## Content Calendar

### Planning

1. **Identify Gaps**
   - What situations aren't covered?
   - What relationships need guides?
   - What constraints are underrepresented?

2. **Plan Seasonally**
   - Valentine's Day content
   - Holiday gift guides
   - Back-to-school gifts
   - New Year motivation

3. **Evergreen Content**
   - Always relevant topics
   - Timeless gift ideas
   - Fundamental relationships

### Publishing Schedule

- **Recommended**: 1-2 guides per week
- **Minimum**: 1 guide per month
- **Consistency**: Regular publishing improves SEO

## Editing Checklist

Before publishing, verify:

- [ ] Title is 50-60 characters
- [ ] Description is 150-160 characters
- [ ] Frontmatter is valid YAML
- [ ] All links work
- [ ] No spelling or grammar errors
- [ ] Tone is consistent
- [ ] Structure is logical
- [ ] Affiliate disclosure is present
- [ ] Internal links are included
- [ ] Images are optimized (if used)

## Common Mistakes to Avoid

1. **Vague Titles**
   - ❌ "Great Gifts for Your Girlfriend"
   - ✅ "Thoughtful Gifts for Your Girlfriend Going Through a Hard Time"

2. **Generic Descriptions**
   - ❌ "Gift ideas for different situations"
   - ✅ "Meaningful gift recommendations for emotional support during difficult periods"

3. **Too Many Gifts**
   - ❌ 20+ gift ideas in one guide
   - ✅ 8-12 well-explained gift ideas

4. **Insufficient Explanation**
   - ❌ "Nice gift, good for any situation"
   - ✅ "Weighted blankets provide physical comfort and can help reduce anxiety during stressful periods"

5. **Poor Organization**
   - ❌ Random gift ideas with no structure
   - ✅ Organized by category (comfort, experience, practical, etc.)

6. **Weak Calls to Action**
   - ❌ No clear next steps
   - ✅ "Check out our complete collection of gift guides"

## Markdown Formatting

### Headings

```markdown
# H1 - Page Title (use once per page)
## H2 - Main Sections
### H3 - Subsections
#### H4 - Minor subsections
```

### Emphasis

```markdown
**Bold text** for emphasis
*Italic text* for subtle emphasis
~~Strikethrough~~ for removed content
```

### Lists

```markdown
- Bullet point
- Another point
  - Nested point
  - Another nested point

1. Numbered item
2. Another item
   1. Nested numbered
   2. Another nested
```

### Links

```markdown
[Link text](https://example.com)
[Internal link](/guides/other-guide)
```

### Blockquotes

```markdown
> This is a blockquote
> It can span multiple lines
```

## Content Examples

### Good Example

```markdown
---
title: "Thoughtful Gifts for Your Girlfriend Going Through a Hard Time"
description: "Meaningful gift ideas to show support during difficult periods. From comfort items to experience gifts that provide emotional support."
category: "Relationships"
publishDate: 2024-01-15
---

## Understanding the Right Gift

When someone you love is going through a difficult time, the right gift can provide comfort, show you care, and remind them they're not alone.

## Comfort-Focused Gifts

### Luxury Candles

A high-quality scented candle creates a calming atmosphere and provides sensory escape.

**Why it works:** Aromatherapy reduces stress and anxiety. A luxury candle shows thoughtfulness and creates a personal sanctuary.

[Rest of guide...]
```

### Poor Example

```markdown
---
title: "Gifts for Girlfriend"
description: "Gift ideas"
category: "Relationships"
publishDate: 2024-01-15
---

## Gifts

Here are some gifts:

1. Candle - nice
2. Blanket - warm
3. Journal - write in it

[Vague and unhelpful]
```

## Updating Existing Content

### When to Update

- New information available
- Better gift recommendations found
- Seasonal updates needed
- Broken links to fix
- Improved writing

### How to Update

1. Edit the Markdown file
2. Update `updatedDate` in frontmatter
3. Commit and push changes
4. Site automatically rebuilds

## Measuring Success

### Metrics to Track

- Page views
- Time on page
- Bounce rate
- Click-through rate on affiliate links
- Conversion rate

### SEO Metrics

- Keyword rankings
- Organic traffic
- Backlinks
- Core Web Vitals

### Content Performance

- Most popular guides
- Guides needing updates
- Content gaps
- Seasonal trends

## Resources

### Writing Tools

- Grammarly: Grammar and spelling
- Hemingway Editor: Readability
- Yoast SEO: SEO optimization
- Google Keyword Planner: Keyword research

### Inspiration

- Reddit gift communities
- Gift recommendation websites
- Customer reviews (Amazon, etc.)
- Social media trends
- Personal experiences

### Research

- Product reviews
- Price comparisons
- Trend analysis
- Seasonal data
- Audience feedback

## Questions?

For content questions or suggestions:
- Check existing guides for style consistency
- Review this guide for best practices
- Test content locally before publishing
- Iterate based on performance data

---

**Happy creating! Your thoughtful gift guides help people show they care. 🎁**
