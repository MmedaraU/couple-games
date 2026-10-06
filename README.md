# 💕 Us Two

A single-file, offline-capable card game for couples — conversation, connection, gratitude, and (behind a consent gate) adult play. Works solo on one device or synced across two, so long-distance partners can play together.

Built as one HTML file with zero build steps, zero backend, and zero accounts. Drop it on any static host, share the link, and play.

> Looking for the party/friends version? That lives [here](https://github.com/MmedaraU/party-games) with its own README.

---

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [How to Play](#how-to-play)
- [The Decks](#the-decks)
- [Adult Content & Consent](#adult-content--consent)
- [Safety & Responsible Play](#safety--responsible-play)
- [Mix Modes](#mix-modes)
- [Party Mode (Double Dates)](#party-mode-double-dates)
- [Onboarding Guide](#onboarding-guide)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Responsive Design](#responsive-design)
- [Deployment](#deployment)
- [Customization](#customization)
- [Technical Architecture](#technical-architecture)
- [Browser Support](#browser-support)
- [Troubleshooting](#troubleshooting)
- [Known Limitations](#known-limitations)
- [Roadmap](#roadmap)
- [License](#license)

---

## Features

- **700 prompts** across seven decks — four sweet decks and three adult decks (18+).
- **Consent gate for adult content** — a three-checkbox agreement appears before any mature deck, remembered for 24 hours and clearable anytime.
- **Sweet Mix and Full Mix** — one safe shuffle, one that includes everything.
- **Action cards** — some prompts ask you to do something together. Accept with **💕 LET'S DO IT** or skip with **⏭️ SKIP FOR NOW**.
- **Drunk Desire safety note** — a small responsible-play reminder appears on the card itself.
- **Real-time Party Mode** — for double dates: one host, everyone sees the same card.
- **Hamburger deck selector on mobile** — full-width button opens a bottom sheet with the sweet and adult sections separated.
- **Onboarding guide** — an 8-step tour on first open, reopenable anytime.
- **Fully responsive** — tuned for phones, tablets, laptops, and landscape phones.
- **Zero backend** — pure client-side, deploys anywhere static files are served.
- **Offline solo play** — works without internet if you skip Party Mode.

---

## Quick Start

### Run locally

1. Download `us-two.html` (or copy the code into a file with that name).
2. Double-click it to open in any modern browser.
3. Tap **Next Card** to draw.

Solo mode works fully offline over `file://`.

### Long-distance or two devices

1. Open the file on one device and tap **🎉 Party → Host a Party**.
2. Share the 4-character code, link, or QR code with your partner.
3. They open the link or join by typing the code.
4. Draw cards — both screens stay in sync.

> Party Mode needs internet access for the initial peer connection. Solo mode does not.

---

## How to Play

### On one device

1. Pick a deck using the chips at the top (desktop) or the game selector bar (mobile).
2. Tap **Next Card**, swipe left on the card, or press **Space / →**.
3. Read the prompt aloud. Take turns, or answer together.
4. For action cards, tap **💕 LET'S DO IT** or **⏭️ SKIP FOR NOW**.
5. Tap **Reset** (or press **R**) to reshuffle and start over.

### Across two devices

- One partner **hosts** and controls the deck: draws cards, switches modes, resets.
- The other partner **joins** and sees the same card in real time.
- Guests can tap **Let's Do It** or **Skip** — the host's device receives the choice and advances both.
- The host's device must stay open and online.

---

## The Decks

| Deck            | Emoji | Count   | Style                                                      | Adult   | In Sweet Mix |
| --------------- | ----- | ------- | ---------------------------------------------------------- | ------- | ------------ |
| Flamingo Nights | 🦩     | 100     | Deep conversation + playful dilemmas                       | No      | ✅            |
| Unboxed Us      | 📦     | 100     | Conversation + actionable dares                            | No      | ✅            |
| Unboxed NG      | 🇳🇬     | 100     | Nigerian couple conversation                               | No      | ✅            |
| Heart to Heart  | 💗     | 100     | Tiered deep questions — Perception, Connection, Reflection | No      | ✅            |
| Dirty Jenga     | 🧱     | 100     | Jenga-block style dares and questions                      | **18+** | ❌            |
| Sexy Commands   | 🎭     | 100     | Simon-Says style intimate commands                         | **18+** | ❌            |
| Drunk Desire    | 🥃     | 100     | Drinking-game prompts                                      | **18+** | ❌            |
| **Sweet Mix**   | 💕     | **400** | The four sweet decks shuffled together                     | No      | —            |
| **Full Mix**    | 🔥     | **700** | Every deck shuffled together                               | **18+** | —            |

> Internally the Heart to Heart deck uses the key `wnrs`, since its tiered format was inspired by that style. The prompts are original.

### Card behaviour by type

- **Plain cards** — a question or prompt, no buttons.
- **Action cards** — from Unboxed Us, Dirty Jenga, and Sexy Commands. Show **💕 LET'S DO IT** and **⏭️ SKIP FOR NOW**.
- **Drunk Desire cards** — show the action buttons *and* a small safety reminder on the card face.

---

## Adult Content & Consent

The three 18+ decks are gated. Selecting any of them — or **Full Mix** — triggers a consent modal before anything loads.

### The gate

The modal shows three checkboxes, and the **I understand** button stays disabled until all three are ticked:

1. We are both 18 or older.
2. We both consent to the content in this deck.
3. Either of us can stop or skip a card at any time, no questions asked.

### What happens after consent

- Consent is remembered for **24 hours** in `localStorage`.
- After that, the gate reappears the next time an adult deck is selected.
- You can clear consent early from **⚙️ Settings → 🔞 Reset 18+ consent**.
- If you clear consent while an adult deck is active, the app automatically drops back to Sweet Mix.

### Visual indicators

- Adult chips have a red border tint.
- Adult cards show a red **18+** badge in the tag.
- Adult cards have a gradient red-rose-gold accent stripe.
- The deck sheet is split into **Sweet 💕** and **Mature 18+** sections.
- Sweet Mix **never** includes adult content.

---

## Safety & Responsible Play

A few things worth stating plainly, since these decks deal with intimacy and alcohol.

### Consent is continuous

- Ticking the gate is the start of consent, not the end.
- Either partner can stop, pause, or skip at any time — during a card, between cards, or mid-round.
- A safe word (or a simple "not now") always wins over any card. The app has no enforcement; the two of you do.

### Skip is always free

- **⏭️ SKIP FOR NOW** exists on every action card.
- Skipping has no penalty, no counter, no record. It just moves on.

### Drunk Desire

- This deck is a drinking game. **Know your limits.**
- Hydrate. Eat something. Alternate drinks with water.
- Never pressure your partner to drink, and never let a card override their no.
- If either of you is feeling unwell, stop. The deck will wait.
- The safety reminder appears on the card itself whenever Drunk Desire is active.

### Privacy

- Everything runs in the browser. No analytics, no tracking, no server.
- Prompts are not stored anywhere except on your device in the active session.
- Party Mode is peer-to-peer; the only data leaving a device is the current card and counters.

---

## Mix Modes

Two shuffle options sit at the top of the chip list and at the top of the deck sheet.

### 💕 Sweet Mix

Draws from the four sweet decks: Flamingo Nights, Unboxed Us, Unboxed NG, and Heart to Heart. **400 prompts total.** Safe for any mood, any time, any place.

### 🔥 Full Mix

Draws from all seven decks. **700 prompts total.** Triggers the 18+ consent gate the first time it's selected in a 24-hour window.

```js
const SWEET_MIX_DECKS = ["flamingo", "unboxed", "unboxedNg", "wnrs"];
const FULL_MIX_DECKS  = ["flamingo", "unboxed", "unboxedNg", "wnrs", "jenga", "commands", "desire"];
```

To change what goes into either mix, edit those two arrays.

---

## Party Mode (Double Dates)

Party Mode uses WebRTC (via PeerJS) so two devices — or two couples on four devices — share the same card.

### Hosting

- Tap **🎉 Party → Host a Party**.
- A 4-character room code is generated (e.g. `M4TX`).
- The host panel shows the room code, a QR code, a copyable link (`?room=M4TX`), and a live guest count.
- Actions the host takes are broadcast to every connected guest.

### Joining

- Open the shared link (auto-joins), or
- Tap **🎉 Party → Join a Party** and type the 4-character code.

### What syncs

- Current card
- Deck tag and accent colour
- Drawn / done / skipped counters
- Remaining cards in the deck
- Selected mode (Sweet Mix, Full Mix, or a single deck)

### What does *not* sync

- The 18+ consent gate is **per device**. Each device must confirm independently.
- Sound effects and confetti are local to each device.

### Guests and adult decks

- If the host selects an adult deck, guests see the same card.
- Guests do not see the consent gate again — they already consented on their own device when they first opened the site, or the host selected the deck for the group.
- If a guest hasn't consented and the host switches to an adult deck, the guest's device shows a consent prompt before rendering the card.

---

## Onboarding Guide

An 8-step guide appears automatically on first open and can be reopened anytime.

1. **Welcome** — what the app is and what's inside
2. **Choose your game** — chips on desktop, hamburger selector on mobile
3. **Draw a card** — button, swipe, keyboard
4. **Action cards** — Let's Do It vs Skip
5. **Adult decks** — how the 18+ gate works
6. **Drunk Desire** — responsible play reminder
7. **Party Mode** — for double dates
8. **Reset anytime** — sound, reset, consent clearing

Reopen with the **❓** button in the header or the **How to play ❓** link in the footer.

**Keyboard navigation while the guide is open:**

- **→ / Enter** = next slide
- **←** = back
- **Esc** = close

---

## Keyboard Shortcuts

| Key                     | Action                      |
| ----------------------- | --------------------------- |
| `Space` / `→` / `Enter` | Draw next card              |
| `1`                     | Let's Do It (action cards)  |
| `2`                     | Skip For Now (action cards) |
| `R`                     | Reset the deck              |

Shortcuts are paused while the onboarding guide is open, while the deck sheet is open, or while typing in an input field.

---

## Responsive Design

### Desktop and large tablets

- Chips row at the top with all nine options (two mixes + seven decks).
- Adult chips have a red border tint.
- Full-size card, both footer shortcut hints visible.

### Phones and portrait tablets (≤1024px portrait)

- Chips hidden, replaced by a full-width game selector bar with a staggered hamburger icon.
- Tapping the bar opens a bottom sheet split into **Sweet 💕** and **Mature 18+** sections.
- Each option shows its emoji, name, card count, and an 18+ badge where relevant.
- Guests in Party Mode cannot open the sheet.

### Small phones (≤560px)

- Brand text hides, icon buttons shrink.
- Action buttons stack full-width.
- Next and Reset split 50/50.
- Modals collapse to single-column actions.

### Other touches

| Feature          | Behaviour                                          |
| ---------------- | -------------------------------------------------- |
| Notched devices  | Header and footer respect `env(safe-area-inset-*)` |
| Touch devices    | Keyboard hints hidden; tap delay removed           |
| iOS text scaling | Prevented with `text-size-adjust: 100%`            |
| iOS focus zoom   | Inputs stay at 16px                                |
| Reduced motion   | All animations and transitions disabled            |

---

## Deployment

Everything lives in a single HTML file. Host it anywhere static. **HTTPS is required for Party Mode** (WebRTC).

### GitHub Pages

```bash
git add us-two.html
git commit -m "Add Us Two"
git push origin main
```

Then enable GitHub Pages in **Settings → Pages**.

### Netlify

Drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop), or connect your repo.

### Vercel

```bash
vercel --prod
```

### Cloudflare Pages

Create a project, point it at your repo, set the output directory.

### Any shared hosting

Upload `us-two.html` to `public_html` or your web root and confirm HTTPS.

### Running locally for testing

```bash
python3 -m http.server 8080
# or
npx serve .
```

Then visit `http://localhost:8080`.

---

## Customization

All editable content lives near the top of the `<script>` tag.

### Add or change prompts

Find the `RAW` object. Sweet decks are arrays of strings. Action decks use objects with `kind: "action"`:

```js
const RAW = {
  flamingo: [
    "What about me is hardest for you to understand?",
    // ...
  ],
  unboxed: [
    { text: "Look into each other's eyes without speaking for 30 seconds.", kind: "action" },
    // ...
  ]
};
```

- Plain string = question card, no buttons.
- Object with `kind: "action"` = action card with **Let's Do It / Skip** buttons.

### Rename a deck or change its colour

```js
const DECKS = {
  flamingo: { label: "Flamingo Nights", emoji: "🦩", color: "#EC4899", adult: false },
  jenga:    { label: "Dirty Jenga",     emoji: "🧱", color: "#DC2626", adult: true  },
  // ...
};
```

Set `adult: true` to gate the deck behind the consent modal.

### Mark a deck as a drinking game

```js
desire: { label: "Drunk Desire", emoji: "🥃", color: "#B45309", adult: true, drunk: true }
```

`drunk: true` displays the safety note on every card from that deck.

### Change what goes into Sweet Mix or Full Mix

```js
const SWEET_MIX_DECKS = ["flamingo", "unboxed", "unboxedNg", "wnrs"];
const FULL_MIX_DECKS  = ["flamingo", "unboxed", "unboxedNg", "wnrs", "jenga", "commands", "desire"];
```

### Change the consent duration

```js
const CONSENT_TTL_MS = 1000 * 60 * 60 * 24; // 24 hours
```

Change to `1000 * 60 * 60 * 1` for one hour, or `1000 * 60 * 5` for five minutes.

### Change the room code length

In `makeCode()`, change the loop count from `4`, and update `maxlength="4"` in `showJoinPanel()` to match.

### Bundling dependencies locally (optional)

By default the page loads **PeerJS** from `unpkg.com` and **QR codes** from `api.qrserver.com`. To make it fully self-contained, download `peerjs.min.js` locally and swap the QR image for a client-side generator.

---

## Technical Architecture

### Stack

- **HTML + CSS + vanilla JavaScript** — no framework, no bundler, no build step.
- **PeerJS** — WebRTC wrapper for peer discovery and data channels.
- **Canvas 2D** — heart-toned confetti animation.
- **Web Audio API** — synthesized sounds (no audio files).
- **LocalStorage** — sound preference, onboarding state, consent timestamp.
- **QR Server API** — QR code image for the host panel.

### File structure

```
us-two.html   ← everything (markup, styles, logic, decks)
```

### State model

The host owns:

- `state.queue` — shuffled pool of remaining cards
- `state.current` — the visible card
- `state.drawn`, `state.doCount`, `state.skipCount` — counters
- `state.filter` — selected mode or deck

Guests mirror this via `applyRemoteState()`.

### Consent state

- `adultConsentGiven` — in-memory flag for the session
- `usTwo.adultConsent` — localStorage entry with an `expires` timestamp

### Sync messages

**Host → guests:**

```js
{ type: "state", card, drawn, doCount, skipCount, remaining, filter }
```

**Guest → host:**

```js
{ type: "action", action: "next" | "do" | "skip" }
```

### Persistence keys

| Key                  | What                                  |
| -------------------- | ------------------------------------- |
| `usTwo.v1`           | Sound preference                      |
| `usTwo.introSeen`    | Whether onboarding has been completed |
| `usTwo.adultConsent` | Consent timestamp (expires after 24h) |

Rooms are ephemeral. There is no server-side state.

---

## Browser Support

| Browser                           | Solo | Party Mode | 18+ Gate |
| --------------------------------- | ---- | ---------- | -------- |
| Chrome / Edge (desktop + Android) | ✅    | ✅          | ✅        |
| Safari (macOS + iOS)              | ✅    | ✅          | ✅        |
| Firefox                           | ✅    | ✅          | ✅        |
| Samsung Internet                  | ✅    | ✅          | ✅        |
| Older browsers without WebRTC     | ✅    | ❌          | ✅        |

Party Mode requires HTTPS (or `localhost`).

---

## Troubleshooting

**Adult deck asks for consent every time**

- Consent expires after 24 hours by design. If you'd rather it not expire, increase `CONSENT_TTL_MS`.
- In private browsing, localStorage may be cleared when the tab closes — the gate will reappear each session.

**Consent gate won't accept**

- All three checkboxes must be ticked. The **I understand** button stays disabled until they are.

**Dropped back to Sweet Mix unexpectedly**

- If you cleared consent from Settings while on an adult deck, the app returns to Sweet Mix. Reselect the deck and re-confirm.

**Guests can't connect**

- Confirm both devices are online and the host hasn't refreshed.
- Check the site is served over HTTPS.
- Some corporate or public Wi-Fi blocks WebRTC — try a hotspot.

**Room code not found**

- Codes are case-insensitive, use `A–Z` (minus I/O) and `2–9` (minus 0/1). Ask the host to re-read it.

**Sound doesn't play**

- Browsers block audio until the first user interaction. Tap once, then draw.
- Check the Sound toggle in ⚙️ Settings.

**Action buttons don't appear**

- Only cards from Unboxed Us, Dirty Jenga, and Sexy Commands have buttons. All other decks are plain prompts.

**Cards feel repetitive**

- The queue avoids repeats until exhausted, then reshuffles. Switching decks rebuilds it from scratch.

**The hamburger selector doesn't show on mobile**

- It appears at ≤1024px **and** in portrait orientation. Rotate to portrait.

---

## Known Limitations

- **Host-dependent Party Mode** — closing the host tab ends the room.
- **No reconnection** — dropped guests must rejoin manually.
- **No persistence** — refreshing the host starts a new room.
- **No authentication** — 4-character codes are guessable. Fine for a private double date, not for public events.
- **Consent is honour-based** — the gate is a good-faith check, not enforcement.
- **Public PeerJS cloud** — subject to rate limits and occasional downtime.
- **Sound and confetti are local** — each device reacts on its own.

---

## Roadmap

- **Custom deck builder** — add your own prompts from the UI.
- **Per-deck consent** — remember consent separately for each adult deck.
- **Date-night timer** — a soft countdown per card.
- **Mood presets** — "cozy," "playful," "deep," "spicy" as shortcuts to specific decks.
- **Shared journal** — save favourite prompts locally.
- **Localization** — Yoruba, Igbo, Hausa, Pidgin UI strings.
- **Self-hosted PeerJS + TURN** for reliability behind strict NATs.
- **PWA install** — offline caching and home-screen launch.

---

## License

Free to use, modify, and share for personal use between consenting adults.

All prompt content is original and written for this project. If you redistribute, a credit link back is appreciated but not required.

The 18+ decks are intended for consensual adult play only. Neither the app nor its authors are responsible for how the prompts are used. **Play responsibly.**

---

## Credits

- Game concept and content: written for Us Two.
- Sync layer: [PeerJS](https://peerjs.com/) over WebRTC.
- QR generation: [qrserver.com](https://goqr.me/api/).
- Sound effects: synthesized in-browser with the Web Audio API.
- Confetti: custom canvas animation.

Enjoy each other. 💕