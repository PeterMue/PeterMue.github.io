---
layout: page
title: Easy Invoice 🧾
description: A single-file, no-nonsense invoice generator for people who'd rather not open Word — click, type, print, done.
img: assets/img/easy-invoice.png
importance: 2
category: fun
related_publications: false
---

## Why I built this

I hate office products. Every time I needed to write an invoice, I'd end up fighting some
bloated word processor: hunting for the right template, fighting autocorrect and autoformat,
nudging text boxes by half a millimeter so the address lines up in the window envelope, and
waiting an eternity for the thing to even open. By the time the invoice was done, I was in a
genuinely bad mood over something that should take two minutes.

So I got grumpy enough to just build my own. **Easy Invoice** is a single HTML file that opens
instantly, lets you click directly on the text to edit it, and prints a clean, properly
formatted invoice — no typewriter-in-a-browser nonsense, no templates to hunt down, no
"why is this cell merged" moments.

The best part: I now keep a bookmark with my own sender details, bank info and footer already
filled in. Need to bill someone? Click the bookmark, fill in the recipient and line items,
hit print. That's the whole workflow.

## What it does

- **A4 / DIN 5008 print layout** — tuned for German window envelopes ("Fensterumschlag,
  Fenster links"), so the recipient address lines up correctly without any manual nudging.
- **Click-to-edit, nothing else** — every field (sender, recipient, invoice number/dates, line
  items, notes, footer) is directly editable right on the page. No config files, no forms, no
  dialogs — just click and type.
- **Dynamic line items** — add or remove rows with a button; net, VAT and gross totals
  recalculate automatically.
- **Handles Kleinunternehmer/private invoices too** — set the tax rate to `0` and it shows a
  single "Rechnungsbetrag" instead of a net/VAT breakdown. Unused optional fields
  (Kundennummer, Ansprechpartner, USt-IdNr., etc.) simply disappear from the printed result.
- **Print-only cleanup** — placeholder hints and all the on-screen editing affordances vanish
  automatically when printing or exporting to PDF, leaving a clean, professional document.
- **Bookmarkable state** — click "Aktuellen Stand als Link kopieren" to get a URL with the
  entire invoice (all fields and line items) baked in as Base64. That's how I get my
  pre-filled-with-my-data bookmark: save the link once, reuse it forever, no server or
  account required.

## How it works

There's no build step, no backend, no dependencies — everything is one HTML file that runs
entirely in the browser. Content is edited in place via `contenteditable`, totals are computed
with a bit of vanilla JavaScript, and the print stylesheet does the heavy lifting to turn the
editable page into a clean A4 document. The "copy as link" feature just Base64-encodes the
current DOM content into the URL's query string — nothing is ever sent anywhere, and reopening
that link restores the invoice exactly as it was.

Because it's static, it's hosted for free on GitHub Pages, works offline if you save the file
locally, and there's nothing to install, register for, or subscribe to.

## Try it

**[petermue.github.io/easy-invoice](https://petermue.github.io/easy-invoice)**

Fill in your own sender and bank details, add your line items, then copy the bookmark link so
next time you need an invoice you can skip straight to the part that actually changes.

Source code: [github.com/PeterMue/easy-invoice](https://github.com/PeterMue/easy-invoice)
