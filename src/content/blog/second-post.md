---
title: 'Building Beat Orbit'
description: 'My experience participating in the GMTK 2025 Game jam'
pubDate: 'Aug 09 2025'
heroImage: '/beat-orbit-1.webp'
---

When a friend on Discord gave us the heads up about the GMTK Game Jam 2025 I wasn't sure if I had the time and energy to particpate. The theme ended up being the word "Loop" which was awesome because I used to be heavily into musical looping performance! I was excited for the theme, but that didn't change the fact my day job has been pretty stressful, I have a 7 year old, and a 3 month old puppy! What really pushed me over the edge was my buddy John handed me a great idea on a silver platter and told me to use it! 
![Original screenshot from John.](/johns-idea.webp)

At this point, I felt like I had no excuse. What emerged was **Beat Orbit** – a synthwave-styled rhythm game where players build drum loops by timing button presses as an arrow rotates around a neon wheel. This is the story of how it came together in a few days, with some help from AI.

## The Concept: Drums in the Round

The core idea changed through a few iterations. During the initial prototyping phase I experimented with a clock hand spinning, as well as a wheel with values spinning with a hit zone.
![Prototype 1](/prototype-1.webp)

![Prototype 2](/prototype-2.webp)

I ended up choosing the spinning arrow mechanic with a synthwave aesthetic for some simple vector art. I'm still learning the ins and outs of Affinity Designer 2 and it's really growing on me. 

![Affinity Designer](/affinity.webp)

## Setting Up the AI Collaboration

This jam marked my first time using [Claude Code](https://www.anthropic.com/claude-code) with the [Godot MCP (Model Context Protocol)](https://github.com/Coding-Solo/godot-mcp) server, and it transformed my development workflow. Game development is my creative outlet so I enjoy that Claude allowed me to free up more time to create music, sound effects, and art from scratch as a solo participant. I set up Godot to use VS Code as my GDScript editor, with both the godot-tools, and GDScript Formatter & Linter extensions. I added my own `.gdlintrc` file to maintain a strict static analysis of the codebase. I also included a `requirements.md` file to have small bite sized tasks the Claude code could help with along the way. Although before I got started with Claude code (with `/init`) I set up all my project settings, as well as scene and node structions within the Godot editor, first to establish a good foundation to build upon. Intellisense + linting + format on save + Claude code = one happy Dad!

## Wild Animations: Finding the Personality

While implementing hit feedback, I accidentally created what became Beat Orbit's signature feature. I was testing rotation animations and set the values way too high – the drum wheel went absolutely wild, spinning multiple times with random direction changes. Instead of fixing it, I realized this could be the game's personality.

Each drum type got its own "wild animation" style:
- **Kick**: 1-2 fast full rotations, like the wheel got punched
- **Snare**: Multiple chaotic half-turns, creating a frantic energy  
- **Hi-Hat**: Simple direction reversal, keeping the beat tight

These animations gave each drum hit a distinct visual personality that matched their sonic character.

## Audio
I had a blast creating and mixing the background music! The danger here is that I lose track of time and space when working on music. I could easily spend the whole game jam making music so it definetly helps to set a timer to timebox the audio production.
![Ableton Session](/ableton-1.webp)

## Lessons Learned

I had trouble keeping the neon wheel and the drum sample grid in sync with the music. I chose to focus on synchronization of only the drum grid and music, as that was necessary. This left the drum wheel being more of a visual timing game and less of a rhythm game, which confused some of the players during the jam. If I could go back I might spend more time trying to remove the wild spinning arrow mechanic and see if there could be a different solution that keeps all mechanics more firmly rooted in the rhythm game genre. 

## Looking Back

Beat Orbit represents what modern game jam can be for a solo dad: a collaboration between human creativity and AI assistance, focused on player experience over technical complexity. The final product wasn't great, but I was really happy to be able to finish something that works (kinda), combining code, art, and music in such a short amount of time.

You can try out Beat Orbit on [itch.io](https://volts-alpaca.itch.io/beat-orbit).
