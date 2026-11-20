# Texts - global rules

Write to me in <your language>, briefly. Copy is written in the market's language.

## How we work
1. I name the text, the market and the situation, e.g. "client/category-pages, FR - optimization".
2. Read in order: this file -> `<client>/CLAUDE.md` -> text `CLAUDE.md` -> `changelog.md` -> latest version -> only the `source/` files this task needs.
3. If the live page differs from the latest version, save it first as the next version with `_live`.
4. Every change = new file in `versions/` (`<MARKET>_v<n>.html`). Never edit an existing version.
5. In chat: change list only. Never paste full HTML (unless I pasted the full code myself).
6. ALWAYS after each version paste Title and Meta description in chat, each in its own code block with character count. If unchanged, paste them anyway and say "unchanged".
7. Add one line to `changelog.md`: date | version | situation | what changed | source.
8. Don't pull Search Console / keyword data that is already in `source/`.

## Models
Strongest model: new text types, new client template. Faster model: corrections, conversions into an existing template.
