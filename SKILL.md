---
name: seo-content-workflow
description: File-based workflow for keeping website copy in order with Claude (category pages, landing pages, blog posts) - client rules and HTML template in files, one folder per text, versions and a changelog. Use when creating, converting, optimizing or correcting page copy - your own draft, a copywriter's text or an existing page - especially across clients, markets or languages.
---

# SEO content workflow (file-based)

This skill is about keeping order in your texts, not about who writes them. The copy can come from you (typed or dictated), from a copywriter, from the client or from what is already on the site. Claude works in a connected folder: it applies the client's rules and HTML template, saves every change as a new version and logs why it changed.

Client rules live in `CLAUDE.md` files and always win over this skill.

## Folder

```
texts/
  CLAUDE.md              <- global rules (all clients)
  _text-template/        <- copy to start a new text
  <client>/
    CLAUDE.md            <- client brief: brand, audience, tone, what we may claim, banned words, links
    template.html        <- the client's HTML layout (built once, from the brand)
    index.md             <- list of this client's texts: folder, URL, market, latest version, last change
    <text>/              <- one folder per page or article, e.g. category-sofas
      CLAUDE.md          <- URL, market(s), goal, what "done" means
      source/            <- input: draft, dictation transcript, copywriter doc, old text, data, questions, feedback
      versions/          <- XX_v0_live.html, XX_v1.html, XX_v2.html ... (never overwritten)
      changelog.md       <- one line per version: date, what changed, why, source
```

Read in this order and nothing else: global `CLAUDE.md` -> client `CLAUDE.md` -> text `CLAUDE.md` -> `changelog.md` -> latest version -> only the files in `source/` this task needs.

## Every task starts the same way

1. The user names the text, the market and the situation, e.g. *"client/category-sofas, PL - correction: new delivery time"*.
2. If the page already exists, check what is live. If it differs from the latest version, or there is no version yet, save the live state first as the next version with `_live` (e.g. `PL_v0_live.html`). Briefs often say "no text on the page" when there is an old description.
3. Make the change in a new file. Never edit an existing version.
4. In chat: a 3-5 point change list, and the title + meta description in separate code blocks with character counts - also when unchanged (say "unchanged"). Never paste full HTML in chat.
5. Add one line to `changelog.md` and update the text's row in the client's `index.md`.

## Situations

### A. New text
Brief and data first (see *Data*). Outline in chat (max ~15 lines), full text after "ok", in the client template.

### B. Your own draft (notes, voice dictation)
Save the raw draft in `source/`. Keep the author's wording and order. Fix typos and dictation errors, add structure (headings, lists, tiles, a table) and put it into the client template. Suggest SEO additions (terms, links, FAQ) as a list and add them only after "ok".

### C. A text from a copywriter or the client (doc, email, plain text)
Save the original in `source/`. Convert it to the client template without rewriting the content. Flag what conflicts with the client brief (claims, tone, banned words, missing links) instead of changing it silently.

### D. Optimizing an existing text (search engines and AI search)
Pull data, then propose a short list of changes with a reason for each: main term in the title and first paragraph, singular vs plural from data, links to subcategories, FAQ from real questions, short paragraphs that make sense on their own. Leave everything else as it is.

### E. Correction
Something on the page is wrong or out of date: a rule changed (e.g. price-reduction rules), delivery terms, a phone number, a product that is gone, or a certificate the client can now document. Change only that fragment. Write the reason and the source (law, client email, document) in the changelog.

### F. Feedback from the client or a native speaker
Save the feedback in `source/`. Treat it as input, not orders: accept language fixes; push back on changes that hurt search intent or break client rules, with a one-line reason (e.g. keep the higher-volume term in the title and use the reviewer's wording in an H2). The result is the next version.

### Finding and comparing
"Where is the delivery text for client X?" -> look it up in `index.md`. "What changed between v2 and v4?" -> compare the two files and list the differences. "Go back to v2" -> copy v2 as the next version and log it; never delete newer versions.

## Data (when the situation needs it)

- **Search Console:** baseline for the exact URL. The page filter usually means *contains*, so a category URL also catches every product under it - use *query + page* and keep the exact URL.
- **Keyword tool:** volume for singular and plural forms and size variants.
- **Questions:** People Also Ask, AlsoAsked, Google suggestions, the keyword tool's questions filter.
- Save what you pulled in `source/`. Don't pull data that is already there.

## Writing rules (defaults - the client file overrides)

- **Title:** main term first, <= 60 characters, brand last.
- **Meta description:** 140-155 characters, what is on the page + a reason to click.
- **Navigation before prose:** links or tiles to subcategories; a table where it helps to choose.
- **FAQ from real questions,** 1-3 sentence answers.
- **Short paragraphs, one idea each.**
- **Only verified facts.** No certificates, standards or test seals without a document from the client.
- **Localize, don't translate:** terms, links and FAQ come from that market's data.
- **One form of address per page,** as agreed with the client.
- **HTML follows `template.html`:** inline styles, no classes unless the CMS needs them.

## Publish and verify

- Paste the whole file into the CMS; title and meta come from chat. No hand edits in the CMS - change the file and paste it again.
- Verify live: title, meta, a phrase that only exists in the new version, links return 200. Use a cache-buster (`?nc=<timestamp>`) - CDNs often serve the old page.
- If the last crawl is before publishing, request indexing. For bigger changes note a check date (+4 weeks) in the changelog.

## Changelog line

```
2026-11-18 | v3 | correction | delivery time 14 -> 10 days | source: client email 17.11 | live 18.11
```

## Lessons learned (keep adding)

- Search Console "page" filter = contains.
- URL Inspection "referring URLs" are history, not proof that a broken link still exists.
- CDN cache makes a published page look unpublished.
- Briefs miss the live state - save it before changing anything.
- Reviewers polish language but don't see search volume.

## Tokens

- One text per chat. Claude reads files instead of a long conversation.
- Limit data pulls (top 25 queries, 10 questions).
