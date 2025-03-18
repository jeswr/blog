---
title: "Impressed by Cursor"
date: 2025-03-18
permalink: /2025/03/18/impressed-by-cursor/
---

<video autoplay="" class="relative bottom-0 left-1/2 z-10 w-auto -translate-x-1/2 overflow-hidden rounded-t-lg lg:absolute lg:h-[90%]" loop="" playsinline="" preload="auto" src="https://assets.basehub.com/191e7e6d/2c99e8a087f981290dc74d2b621a7192/current-best-for-two-mp4.mp4"></video>
**Credit [cursor.com](https://cursor.com)**

I've been using [cursor](https://www.cursor.com) with [claude-3.7-sonnet-thinking](https://www.anthropic.com/news/claude-3-7-sonnet) for the last week for a range of programming tasks. I've been extremely impressed by some of the things it has been able to do - however there is still room to improve.

Things cursor excelled at:
 - Format Conversions: Such as markdown-to-table conversions can be done first-shot by highlighting the thing you want converted and telling it the format you want it converted to. It has for instance done [this table conversion](https://github.com/jeswr/blog/commit/60b8ea96ab72f36fa1ebb5fab4921761f1591b4c), and these [footer conversions](https://github.com/jeswr/blog/blob/f110776806e091c9550effa36d0d563b3653557e/raw-posts/disambiguating-data-wallets.md?plain=1#L739).
 - Reasonably complex node.js logic [like this](https://github.com/rdfjs/N3.js/pull/503) - though the example provided here was done with the assistance of copilot before I had discovered cursor. It also required me to prompt it describing the exact return types and proxy-based architecture that I was after.

Places where there is room to improve:
 - Full codebase generation: I tried to get it to generate an implementation of the [Model Context Protocol](https://modelcontextprotocol.io/introduction) for the [Solid Specification](https://solidproject.org/specification). As can be seen in the attempt [here](https://github.com/jeswr/solid-mcp/tree/56b951cc9577b36ed1b89540e7b233afbb5f0b4e), whilst the docs look *lovely* it severely over-complicates the implementation; which should look more like [this Google Drive example](https://github.com/modelcontextprotocol/servers/tree/main/src/gdrive). Similar issues were faced in trying to get it to generate a [Notation3 Proof Checker in Rust](https://github.com/jeswr/n3proof.rs/tree/7e7e8ceafacc31b0872349d0daf391054831f686).
 - Going [off topic](https://github.com/oxigraph/oxigraph/pull/1213#discussion_r1997515722) and [making up properties of manifest files](https://github.com/oxigraph/oxigraph/pull/1213#discussion_r1997649834).
