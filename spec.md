# Neon Pulse - Rhythm Runner

## Overview
An endless runner where obstacles spawn synchronized to music beats. Players must time their jumps to the rhythm for maximum points. Synthwave aesthetic with heavy visual juice.

## Core Gameplay

### Movement
- Auto-scrolling runner (player moves right automatically)
- Single input: JUMP (spacebar or tap)
- Double-jump available (unlocked after first 1000 points)
- Gravity and air control feel snappy and responsive

### Rhythm System
- BPM-based obstacle spawning (120 BPM default)
- Visual beat indicators approach from the right
- Player must jump ON the beat when obstacle arrives
- Timing windows:
  - PERFECT: ±50ms (100 pts × combo)
  - GOOD: ±150ms (50 pts × combo)
  - MISS: 0 pts, reset combo, lose 1 health

### Scoring
- Base points from timing accuracy
- Combo multiplier: 1x → 2x → 3x → 4x (max)
- Builds every 5 consecutive perfect/good hits
- Near-miss bonus: Extra particles/effects (no points, just juice)

### Health System
- 3 hearts/lives
- Lose 1 on collision/miss
- Game over at 0 health
- No health regeneration (keeps tension high)

## Visual Design

### Aesthetic
- Synthwave/retrowave theme
- Color palette: Deep purple/black background, cyan and magenta neons
- Grid floor that extends to horizon (perspective)
- Glowing everything

### Player Character
- Simple geometric shape (triangle/diamond) with glow
- Trail effect behind character
- Squash/stretch on jump and land
- Color shifts with combo level

### Obstacles
- Neon blocks/spikes that pulse on beat
- Glow intensifies as beat approaches
- Shatter into particles when cleared with perfect timing

### Beat Indicators
- Visual pulse wave emanating from obstacles
- Ring that contracts toward obstacle center on beat
- Background grid pulses on every beat

### Juice Effects
- Screen shake on miss
- Chromatic aberration on high combo
- Particle explosions on perfect timing
- Flash effects on beat
- Speed lines at high velocity

## Audio

### Music
- Procedural beat generation (no external audio files needed)
- Kick drum on primary beats
- Hi-hat patterns for rhythm texture
- Synth bass line that follows the grid

### Dynamic Layers
- Layer 0 (base): Kick + hi-hat
- Layer 1 (2x combo): Add bass
- Layer 2 (3x combo): Add lead synth
- Layer 3 (4x combo): Full intensity, reverb, effects

### Sound Effects
- Jump: Quick synth whoosh
- Perfect: Bright ding/chime
- Good: Softer confirmation
- Miss: Low impact thud
- Combo milestone: Ascending tone

## Game States

### Title Screen
- "NEON PULSE" logo pulsing to beat
- "PRESS SPACE TO START"
- High score display
- Beat visualization in background

### Gameplay
- Main runner view
- HUD: Score (top-left), Combo (top-center), Health (top-right)
- Ghost runner if previous run exists

### Game Over
- Final score with grade (S/A/B/C based on accuracy %)
- Best combo achieved
- "Press SPACE to retry"
- Option to watch ghost of this run

## Progression

### Speed Ramp
- Starts at base speed
- +5% speed every 30 seconds
- Cap at 2x base speed

### Difficulty Curve
- Early game: Obstacles every 4 beats
- Mid game: Obstacles every 2 beats, some syncopation
- Late game: Complex rhythms, off-beat patterns

## Technical

### Implementation
- Single HTML file with embedded CSS/JS
- Canvas-based rendering
- Web Audio API for procedural sound
- RequestAnimationFrame game loop
- Local storage for high score and ghost data

### Controls
- Spacebar: Jump
- Enter: Start/Restart
- M: Mute toggle

## Polish Features

### Ghost Mode
- Transparent silhouette of previous best run
- Stored in localStorage
- Shows player position at each frame

### Visual Feedback
- Perfect: Golden particles, screen flash
- Good: White particles
- Miss: Red flash, screen shake
- Combo milestones: Text popup ("2X!", "3X!", etc.)

### Accessibility
- High contrast neon colors
- Audio cues for all visual feedback
- Timing windows tunable (future)
