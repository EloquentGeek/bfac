+++
title = "Game Engines"
description = "Tools of the trade."
date = 2025-01-04
updated = 2025-01-13
draft = false
weight = 410
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = "<em>Tools of the trade.</em>"
toc = true
top = false
+++

## What's a game engine?

Honestly, when I started learning about games I thought I knew what a game engine was. Something
that gave me a higher-level [API](https://en.wikipedia.org/wiki/API) to draw graphics and play sounds, maybe some input handling. I
knew some of them provided an ability to distribute games cross-platform (develop on Linux, deploy
everywhere) and some supported drag-and-drop or point-and-click development.

I honestly didn't pay much attention to the big name engines and why people chose them. My childhood
memories were of people I looked up to writing games in assembly language and C, often developing
their own toolkits to assist in the process.

Turns out, engines evolved since then. The majors encompass one or more of the following features:

- sprite editing and animation previews
- tilemap editing
- visual UI editing/formatting
- drag and drop or code-lite development (sometimes referred to as a "blueprint" feature, especially in the Unreal
  Engine community)
- built-in code editing, analogous to an external editor but often with "batteries included":
  abilities specific to the engine or Language Server Protocol-like behaviours for the built-in
  language
- live preview of the game in a debugger with various features often including the ability to alter
  code or specific values and have the change appear in real time
- distribution pipelines for various platforms, including mobile devices

And the list goes on.

There are [plenty of game engines](https://enginesdatabase.com) available, including at least one
for most major platforms and languages. If you ask most people in and around the community, they'll
recognise at least one of the following. You should also check [PirateSoftware's gamedev
site](https://develop.games) for a ton of relevant background information and just general good
vibes.

## Unity

One of the better-known engines, [Unity](https://unity.com) is wildly popular in both professional
and amateur gamedev communities. A core strength is cross-platform distribution, including reliable
support for mobile devices. Development language is C#. A [wildly-unpopular licensing agreement](https://en.wikipedia.org/wiki/Uniy_(game_engine)#Runtime_fee_reception) was
modified in late 2024.

## Unreal Engine

The 3D specialist. While many other engines make 3D games possible, Unreal is one of the first tools
triple-A teams reach for. It's relatively easy to hire for, since most 3D developers have at least
some C++ background, and it provides the various art and asset pipelines needed by those teams. It
also has quite a friendly model for smaller gamedevs: if your title earns less than one million,
there's no license fee.

## Godot

Don't ask me how to pronounce it. I'm fairly convinced its own community doesn't know. However,
Godot is rapidly becoming a player in the 2D and 3D worlds, having a strong indie following and more
than a few commercial studios using it. It provides GDScript, a Python-like language, and games can
also be written in C#. Plugins are authored largely as C++ modules. Definitely a strong choice if
you're a fan of the open source model.

## GameMaker

An unassuming yet surprisingly capable player, especially in the 2D world. It provides GML, a
JavaScript-like language which is used with a variety of point-and-click mechanisms to build games.
It has a relatively friendly licensing structure (free to use initially, with a $100 USD lifetime
license option). There's a wide community of indie users, and plenty of YouTube tutorials.
