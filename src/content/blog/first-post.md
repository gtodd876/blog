---
title: 'First post'
description: 'Kick off of my game dev blog'
pubDate: 'May 25 2025'
heroImage: '/src/images/post1-featured.webp'
---

Hi, this is the start of my brand spanking new game dev blog. I'm starting this blog as an online diary to document my game development progress over time. After trying out SFML, Love2d, and Pico, I have settled on using Godot for now. I'm a senior software engineer doing full stack web development for my day job and I feel like Godot has had the maximum fun factor for me. Fun factor is really important to me with this hobby since last thing I want to do with my life is to spend 100% of my waking hours coding in front of a monitor. I'm spending a lot of time learning graphic design, animation, and getting back into music production, which is perfect. Every chance that I have some free time, a brand new adventure begins.

## Slippery socks - my first Ludum Dare

My first game jam attempt was for the April 2025 [Ludum Dare](https://ldjam.com/) and I made a game called [Slippery Socks](https://volts-alpaca.itch.io/slippery-socks). It's a pixel art platformer featuring my daughter jumping around on furniture as she runs through a house. The concept was simple but charming - exactly what you want for a game jam where time is limited.

### Mixing pixel art with smooth fonts

One of the biggest challenges I faced was achieving crisp, professional-looking text alongside pixel art graphics. I wanted the nostalgic pixel art aesthetic for the gameplay but modern, readable typography for the UI. Which I didn't realize, in my game dev blissful ingnorance, is a surprisingly difficult thing to manage.

The core issue was that my game used a 320x240 viewport scaled up 4x to 1280x960 for that authentic pixel art look. This made sprites look perfectly crisp, but any smooth fonts became blurry when scaled up from the low resolution.

Here's what I learned about Godot's rendering pipeline:

**The problem**: When you set your project's "Default Texture Filter" to "Nearest" (required for pixel-perfect sprites), it affects everything including fonts. But when you set it to "Linear" (needed for smooth fonts), your pixel art becomes blurry.

**The solution**: I used Godot's SubViewport system to create a dual-resolution rendering approach:
1. Created a [SubViewport](https://docs.godotengine.org/en/stable/classes/class_subviewport.html) at the full output resolution (1280x960)
2. Rendered text at high resolution in this viewport
3. Used a ViewportTexture to display the crisp text in the main low-res scene
4. Applied different texture filtering to different elements

This technique let me maintain pixel-perfect sprites while achieving crisp, professional typography - the best of both worlds.

### Tilemaps

Learning [TileMapLayers](https://docs.godotengine.org/en/stable/classes/class_subviewport.html) and [TileSets](https://docs.godotengine.org/en/stable/classes/class_tileset.html) was probably the most diffcult and stressful as I needed a way to apply different behavior based off of tile that the player is standing on. A certain type of couch cushion, for example, would launch the character into the air.

### Music

I went back to using [Ableton](https://www.ableton.com/) and [Logic](https://www.apple.com/logic-pro/) for the music production and surprisingly to me, this is where I had the most fun. I worked in a recording studio prior to becoming a software developer but it's been years since I've touched music software and didn't realize how much I missed it till making this game!

### Pixel art

Prior to starting this game jam I had been consuming lots of [Aesprite](https://github.com/aseprite/aseprite) tutorials so it made sense for me to go with pixel art for this game as that what I was actively learning. Animating my daughter as a pixel art character was pure joy and I'm really looking forward to learning more about animation. 

## Triads - A musical memory game

After Ludum Dare, I wanted to explore Godot's control node / UI capabilities more, so I created [Triads](https://volts-alpaca.itch.io/triads) - a musical memory game where players listen to and repeat increasingly complex sequences of notes and chords.

### Game design

The game features three progressive levels:
- **Level 1**: Single-note sequences (7 rounds)
- **Level 2**: Two-note chord sequences (4 rounds)  
- **Level 3**: Three-note chord sequences (3 rounds)

The difficulty progression keeps the learning curve manageable while challenging players' musical memory.

### Technical deep dive

**State management**: I implemented a robust game state system using enums (IDLE, COUNTDOWN, COMPUTER_TURN, PLAYER_TURN, etc.). This taught me the importance of clear state management in game development.

**Audio programming**: This was my first real dive into game audio programming. I built systems for:
- Dynamic audio playback based on player input
- Precise timing for musical sequences
- Polyphonic sound handling (playing multiple notes simultaneously)
- Audio management with different sound categories

**Creating the audio**
I create a layered synth sound I enjoyed and then sampled every note, each half step, for a little over an octave in range to have each of the 16 pads to coorespond to a single note. I also had a blast reocrding my own voice and running that through a [vocoder](https://en.wikipedia.org/wiki/Vocoder) as the voice of the synth giving instructions! 

**Multi-note chord recognition**: One of the trickiest challenges was building a system that could detect when a player had correctly played a complete chord. This required validating that all required notes were pressed simultaneously while handling timing windows for human input.

**Cross-platform considerations**: I added platform detection and optimized for both desktop and mobile, learning about the differences in input handling and performance requirements. I have an iPhone and got the game deployed to my iOS device but it was really challenging.  Some of the screenshots wee out of date with the current version of XCode. I got a PR in to fix the Godot docs and hopefully that will get merged to help out iOS folks in the future.

I realized at this point that the game is more more fun to play with multi touch on a phone compared to using a desktop keyboard.

### Key Lessons Learned

1. **Research hardware limitations**: I discovered that some laptops have keyboard limitations (key rollover) that affected gameplay - teaching me to consider hardware constraints in game design.

2. **Progressive difficulty works**: Starting simple and gradually increasing complexity kept players engaged without overwhelming them.

3. **Debugging tools save time**: Adding keyboard shortcuts to jump to any level made testing much more efficient.

4. **Immediate user feedback is crucial**: Visual and audio feedback helps players understand their mistakes and successes instantly.

## Looking Forward

I have started working on a [frogger](https://en.wikipedia.org/wiki/Frogger) clone and this time I am going to learn to create smooth 2D art and hand drawn animations with Procreate.