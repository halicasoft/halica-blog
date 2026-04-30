# Halica Blog - Astro Development Plan

## Overview

A minimal Astro blog with three pages: Homepage/Blog, About, and Projects. Focused on simplicity and performance.

---

## Scope

### Pages
1. **Homepage/Blog** - Combined landing page with recent blog posts
2. **About** - Information about the author
3. **Projects** - List of projects with external links

### Design Philosophy
- Minimal frontend
- Fast loading times
- Content-first approach
- Zero unnecessary JavaScript

---

## Phase 1: Project Setup

### 1.1 Initialize Astro Project
```bash
npm create astro@latest .
```
- [ ] Choose **Blog** template or start from scratch
- [ ] Install dependencies: `npm install`
- [ ] Verify setup: `npm run dev`

### 1.2 Basic Configuration
- [ ] Update `astro.config.mjs` with site URL
- [ ] Set build output to `static` (default)

---

## Phase 2: Project Structure

```
src/
├── components/
│   ├── Header.astro
│   ├── Footer.astro
│   └── PostCard.astro
├── layouts/
│   └── BaseLayout.astro
├── pages/
│   ├── index.astro         # Homepage + Blog listing
│   ├── about.astro
│   ├── projects.astro
│   └── blog/[slug].astro   # Individual blog posts
├── content/
│   └── blog/
│       └── *.md            # Blog post markdown files
└── styles/
    └── global.css
public/
└── favicon.svg
```

---

## Phase 3: Content Collections

### 3.1 Set up `src/content/config.ts`
```typescript
import { z, defineCollection } from 'astro:content';

const blogCollection = defineCollection({
  type: 'content',
  schema: z.object({
    title: z.string(),
    description: z.string(),
    pubDate: z.date(),
    tags: z.array(z.string()).optional(),
    draft: z.boolean().optional(),
  }),
});

export const collections = {
  blog: blogCollection,
};
```

---

## Phase 4: Components

### 4.1 BaseLayout.astro
- [ ] Simple HTML structure
- [ ] Header with navigation links
- [ ] Main content area
- [ ] Minimal footer

### 4.2 Header.astro
- [ ] Site title (linked to homepage)
- [ ] Navigation: Home | About | Projects

### 4.3 Footer.astro
- [ ] Copyright text
- [ ] Optional: social links

### 4.4 PostCard.astro
- [ ] Post title (linked to full post)
- [ ] Date
- [ ] Short description

---

## Phase 5: Pages

### 5.1 Homepage (`index.astro`)
- [ ] Site title and brief description
- [ ] List of recent blog posts (using `getCollection()`)
- [ ] Simple, clean layout

### 5.2 About (`about.astro`)
- [ ] About text/bio
- [ ] Optional: profile image
- [ ] Optional: social links

### 5.3 Projects (`projects.astro`)
- [ ] List of projects
- [ ] Each project: name, description, link
- [ ] Clean card or list layout

### 5.4 Blog Post (`blog/[slug].astro`)
- [ ] Dynamic routing from content collection
- [ ] Render Markdown content
- [ ] Display title, date, tags
- [ ] Back to home link

---

## Phase 6: Styling (Minimal)

### 6.1 Global Styles (`src/styles/global.css`)
- [ ] Basic reset
- [ ] Typography (font family, sizes)
- [ ] Spacing utilities
- [ ] Link styles
- [ ] Simple color scheme

### 6.2 Design Decisions
- [ ] Single font family (system fonts for speed)
- [ ] Limited color palette (2-3 colors)
- [ ] No complex animations
- [ ] Mobile-responsive with simple media queries

---

## Phase 7: Essential Integrations

### 7.1 Required
- [ ] **@astrojs/sitemap** - Auto-generate sitemap

### 7.2 Optional
- [ ] **@astrojs/rss** - RSS feed for blog

---

## Phase 8: Deployment

### 8.1 Build & Deploy
```bash
npm run build
```
- [ ] Build locally and test with `npm run preview`
- [ ] Deploy to hosting platform (Vercel, Netlify, or GitHub Pages)
- [ ] Connect custom domain (if needed)

---

## Quick Start Commands

```bash
# Create project
npm create astro@latest .

# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

---

## Simplified Checklist

- [ ] Initialize Astro project
- [ ] Set up content collections
- [ ] Create BaseLayout component
- [ ] Create Header and Footer components
- [ ] Create PostCard component
- [ ] Build homepage with blog listing
- [ ] Build about page
- [ ] Build projects page
- [ ] Build blog post template
- [ ] Add global CSS styles
- [ ] Write sample blog posts
- [ ] Build and deploy

---

## Resources

- [Astro Documentation](https://docs.astro.build/)
- [Astro Content Collections](https://docs.astro.build/en/guides/content-collections/)