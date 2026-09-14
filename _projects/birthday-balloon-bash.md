---
layout: page
title: Birthday Balloon Bash 🎈
description: A PIN-protected, gamified birthday surprise page — no server, no accounts, just balloons, confetti and a heartfelt message delivered by QR code.
img: assets/img/birthday-balloon-bash.png
importance: 1
category: fun
related_publications: false
---

## Why I built this

My twin sons turned 10 — and it also happened to be the day they got their very first
smartphones. Their "real" present hadn't arrived in time, so I needed something to
bridge the gap that still felt special and personal.

So I built **Birthday Balloon Bash**: a single-page site that greets them by name, asks
for a secret 4-digit PIN, and then reveals a heartfelt message together with balloons,
confetti and some music — plus a little "pop the balloons before time runs out" mini-game
as a bonus surprise.

Since they'd just gotten their phones, a QR code felt like the perfect delivery mechanism.
I 3D-printed a little QR code stand, popped it next to their new phones, and let them scan
their way to the surprise. 🎉

## What it does

- **Personalized reveal** — enter a name and a message once on the creator page, get back
  a shareable, encrypted link.
- **PIN-protected** — recipients need a 4-digit PIN to unlock the message. It's fun
  suspense, not real security (this is for birthday wishes, not secrets).
- **Balloons, confetti & music** — a festive animated reveal with sound effects, built with
  plain CSS animations, the Web Audio API and `<canvas>` confetti.
- **A balloon-popping mini-game** — an easter egg: pop 20 balloons before the 60-second
  clock runs out to win, with escalating spawn waves to keep it exciting.
- **Selectable color themes** — Pink, Green, Blue, Purple or Gold, picked on the creator
  page and passed along as a plain (non-secret) `?theme=` URL parameter.
- **Bilingual** — automatically shows English or German based on the visitor's browser
  language, with a `?lang=` override.
- **Zero backend** — everything, including the encryption, runs entirely client-side.
  Nothing is ever sent to a server.

## How it works

Creating a surprise encrypts `{ name, message }` with **AES-GCM**, deriving the key from
the chosen 4-digit PIN via **PBKDF2** (200,000 iterations) using the browser's native
Web Crypto API. The result is packed into a URL-safe token and embedded as a `?payload=`
query parameter — no server round-trip required.

When the recipient opens the link, they're prompted for the PIN. A correct guess decrypts
the token entirely in the browser and reveals the personalized message, balloons, and
game. Messages support a small allowlist of safe HTML tags, so the sender can format text
without risking script injection.

Because it's 100% static, the whole project is hosted for free on **GitHub Pages** with
no build step and no dependencies — just `index.html`, `styles.css`, and `app.js`.

## Try it

**[petermue.github.io/birthday-balloon-bash](https://petermue.github.io/birthday-balloon-bash)**

Open the link with no parameters to create your own encrypted surprise link — no
installation, no account, just fill in a name, a message, a PIN and a color theme.

Source code: [github.com/PeterMue/birthday-balloon-bash](https://github.com/PeterMue/birthday-balloon-bash)
