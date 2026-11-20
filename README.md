# SEO content workflow for Claude

A file-based way to keep website copy in order - category pages, landing pages, blog posts - for one client or ten, one market or many.

It doesn't matter who writes the text: you (typed or dictated), a copywriter, the client, or what is already on the site. The skill keeps every text in one place, applies the client's rules and HTML template, saves each change as a new version and logs why it changed.

## When it helps

- **A new text** - from brief and data to a finished page in the client's layout.
- **Your own draft** - notes or a voice dictation turned into clean HTML, in your words.
- **A copywriter's text** - a doc converted into the client's template, without rewriting it.
- **Optimization** - an existing text improved for search engines and AI search, based on data.
- **A correction** - a rule changed, delivery terms are new, a certificate finally has a document. Change one fragment, log why.
- **Feedback** - notes from the client or a native speaker applied as the next version.
- **Finding and comparing** - which text is where, what changed between versions, going back to an older one.

## The idea in one picture

```
name the text + situation -> save what is live -> change in a new file -> change list + meta in chat
      -> changelog line -> publish -> verify live -> (request indexing, check after 4 weeks)
```

- **Rules live in files**, not in prompts: global -> client -> text `CLAUDE.md`. Write a rule once and every later text follows it.
- **One HTML template per client**, built once from the brand. Every text uses it.
- **Versions, never overwrites** (`PL_v1.html`, `PL_v2.html`) plus a one-line changelog. Easy to go back, compare or explain a change.
- **The chat carries only decisions**: change list, title and meta description in copyable blocks.
- **Feedback is input, not orders.** Language fixes go in; changes that hurt search intent get a one-line reason.

## What's inside

```
SKILL.md                     <- the skill: folder, situations A-F, writing rules, lessons learned
templates/
  CLAUDE.global.md           <- rules for all clients
  CLAUDE.client.md           <- client brief: brand, audience, tone, what you may claim, links
  template.html              <- example HTML layout to replace with the client's
  index.md                   <- list of one client's texts (where each text is, latest version)
  _text-template/            <- copy for each new page or article
    CLAUDE.md, changelog.md, source/, versions/
```

## How to use it

**Claude app (desktop):**
1. Add `SKILL.md` as a skill (in Claude's settings, or upload the folder as a zip).
2. Create a `texts/` folder on your computer, copy the templates in, fill in the client brief and template.
3. Connect the folder to the chat ("Add folder").
4. Start, e.g.: *"client/category-sofas, PL - correction: new delivery time."* or *"client/blog-sizes, PL - here is my dictated draft, put it into the template."*

**Claude Code:** put `SKILL.md` in `.claude/skills/seo-content-workflow/` and the `CLAUDE.md` files in your project.

Helpful but not required: Google Search Console, a keyword tool (Ahrefs, Semrush, Senuto...), AlsoAsked or People Also Ask, browser access to check the live site.

## Lessons that made it into the skill

- **Search Console's page filter means "contains".** For a category hub it also counts every product under the same path - filter by *query + page* and keep the exact URL.
- **Singular vs plural is a data decision.** In one market the singular had more than three times the searches of the plural. Keep the high-volume form in the title, the natural plural in an H2.
- **The brief said "no text on the page". The page had a full old description.** Always save what is live first.
- **A published page looked unpublished** - CDN cache. Verify with a cache-buster.
- **"Referring URLs" in URL Inspection are history**, not proof that a broken link still exists.

## License

MIT - use it, adapt it, share it. If it helps, I'd love to hear how you changed it.
