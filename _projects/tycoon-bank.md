---
layout: page
title: TycoonBank 🏦
description: A touch-first digital board game banker built for tabletop iPad play — realistic credit cards, drag-and-drop transfers, kid-proof multiplier keypads, and an instant Undo button.
img: assets/img/tycoon-bank.png
importance: 1
category: fun
related_publications: false
---

## Why I built this

If you've ever played _Monopoly_ with young kids, you know the delicate balance between family fun and sheer financial chaos. We’ve been playing the modern _Electronic Banking_ edition for years — the one with plastic credit cards and a battery-powered terminal. It eliminated the dreaded mess of crumpled paper bills, missing change, and four-hour games where half the time is spent counting twenty-dollar notes off the carpet.

Until one weekend, the banking hardware gave up. A corroded battery contact, stuck membrane buttons, and a glitched LCD screen: our trusty plastic terminal officially died mid-game, leaving two very disappointed kids staring at a half-finished board.

Naturally, I reached for an iPad to find a replacement. Surely in this day and age, there must be a decent digital Monopoly banker app?

Turns out, virtually everything out there was **crap**:

- **Ad-infested nightmares** — games constantly interrupted by 30-second unskippable casino ads in front of 10-year-olds.
- **Clunky single-phone ergonomics** — apps designed for one person holding an iPhone, forcing everyone to pass a phone back and forth across the board for every single rent payment.
- **Paywalls & account spam** — requiring logins, cloud subscriptions, or tracking scripts just to add and subtract virtual cash.
- **Tiny buttons and zero safety nets** — one stray finger tap turns a 200k rent payment into a 20M bank-breaking catastrophe, with zero undo functionality and immediate sibling tears.

I didn't want a bloated native app, and I certainly didn't want ads at family game night. So I decided to **vibe code** my own solution tailored exactly to how we play: **TycoonBank**.

The design goal was simple: place an iPad flat in the center of the table, surround a central Bank Vault with personalized player credit cards, and make transactions tactile, intuitive, and completely kid-proof — all running 100% client-side in the browser, hosted for free on GitHub Pages.

## What it does

- **Central Tabletop iPad Layout** — designed specifically to sit flat in the center of the game table. The Bank Vault sits in the middle, framed by player accounts. Players sitting opposite the iPad can tap a 180° rotation button on their card so their balance and name face them right-side up.
- **Tactile Credit Cards** — each player gets a luxury credit card complete with EMV chip, contactless wave icon, customizable avatars (🎩, 🏎️, 🐈, 🚢, 👑, etc.), and metallic foil themes (Gold, Obsidian, Sapphire, Emerald, Ruby, Rose Gold, Titanium, and Amethyst).
- **Drag-and-Drop & Tap Transfers** — pay rent the way kids intuitively expect: drag your card onto another player's card to send funds, drag onto the Bank Vault to pay fines or buy properties, or drag the Bank Vault onto your card to collect Go rewards. Standard tap buttons are also right there for fast gameplay.
- **Kid-Proof Multiplier Keypad (`2` + `Mio` = 2.000.000)** — typing out six zeroes on glass is an invitation to accidental 10x blunders. The custom keypad features quick multiplier shortcuts (`Tsd/k`, `Mio`, `Mrd/B`) and a real-time written-words preview (_"2 Millionen"_ / _"2 Million"_), so everyone can see exactly what's being transferred before confirming.
- **The Sibling Peacekeeper: Audit Ledger with 1-Click Undo** — "Wait, you charged me twice!" or "I typed 2M instead of 200k!" no longer derails the evening. The full transaction drawer logs every single transfer chronologically, and a single click on **Undo** rolls back the balances instantly. You can even export the full game ledger to CSV.
- **Zero-Dependency Web Audio Effects** — satisfying mechanical cash register "cha-chings", card swipe beeps, and Pass GO fanfares synthesized entirely in the browser using the Web Audio API — no bulky MP3 downloads or network requests required.
- **Bilingual & Rule-Flexible** — toggle seamlessly between English and German with localized number abbreviations. Configure starting capital (e.g. 15.000.000 modern or classic 1.500), Pass GO payouts, and currency symbols (€, $, £, ℳ, CHF).
- **Offline-First & Instant Share via QR Code** — zero accounts, no server database. The full game state is compressed into a URL hash using `lz-string` and rendered as a live QR code. Scan it with a smartphone to view or transfer the game, and enjoy automatic background saving to `localStorage`.

## How it works

TycoonBank was vibe-coded using modern web tech: **React 19**, **TypeScript**, **Vite**, and **Tailwind CSS v4**, with **@dnd-kit** providing smooth touch and pointer drag-and-drop interactions.

Because there is zero backend, the entire application is bundled into static HTML, CSS, and JS assets. It deploys automatically via GitHub Actions directly to **GitHub Pages**, meaning it loads instantaneously, works completely offline once cached, and collects zero user data.

Whenever a game is in progress, any transaction automatically synchronizes to `localStorage`. If you want to switch devices mid-game or let someone spectate, the app serializes and compresses the entire store into a compact Base64/lz-string hash in the URL.

## Try it

**[petermue.github.io/tycoon-bank](https://petermue.github.io/tycoon-bank)**

Place your iPad or laptop on the table, customize your player cards, and take the stress (and paper mess) out of your next game night.

Source code: [github.com/PeterMue/tycoon-bank](https://github.com/PeterMue/tycoon-bank)
