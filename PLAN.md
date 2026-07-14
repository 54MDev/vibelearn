# VibeLearn — Website Plan

Free vibecoding classes for teens, hosted at the library. Two scrollable pages, phone-first.

## Design direction

Hack Club energy, simplified.

- **Background:** dark (near-black, e.g. `#0d0d12`)
- **Accent:** electric lime (`#c8ff00`) — swap to hot pink later if it doesn't land
- **Type:** big rounded sans-serif for headlines (e.g. system font stack or a free Google font like Outfit), regular sans for body
- **Touches:** sparkles/emoji in headings, subtle typing effect on the hero tagline. Nothing else animated.
- **Copy tone:** casual, talks *to* teens ("you'll build…"), no corporate jargon, short sentences
- **Layout:** cards for everything, one obvious button per section, everything readable on a phone

## Page 1 — `index.html` (Home)

1. **Hero**
   - Huge "VibeLearn ⚡"
   - Tagline: *"Build real apps with AI. No experience needed. Free at the library."*
   - Big accent button → Google Form (placeholder link until form exists)
2. **Next sessions**
   - Cards: date, time, library name/room, topic
   - Soonest session visually highlighted
   - Editing dates = editing one card in the HTML
3. **What's vibecoding?**
   - 3 short conversational lines explaining it
4. **What you'll make**
   - 3–4 small cards showing outcomes: a game, a website, a bot, your own idea
5. **How to join**
   - "It's free. Grab a spot 👇" + Google Form button again
6. **Footer**
   - Contact email, link to Resources page

## Page 2 — `resources.html` (Resources)

1. Small header + link back to Home
2. **Start here** — the 2–3 tools used in class (Claude, etc.), one line each on what it is
3. **From class** — slides/materials per session; starts small, grows each week
4. **Keep going** — practice ideas + good free links
5. Same footer

## Tech

- Two plain HTML files, inline CSS, no framework, no build step
- Host free on GitHub Pages (repo is already `vibelearn`)
- To update: edit the HTML, push, done

## Not doing (on purpose)

Sign-in, CMS, database, testimonials, blog, about page, analytics. It's a library class site — add any of these only when there's a real need.

## Open items (fill in before/while building)

- [ ] Google Form link
- [ ] Library name, room, and first class dates
- [ ] Contact email
- [ ] Confirm accent color after seeing it (lime vs pink)
