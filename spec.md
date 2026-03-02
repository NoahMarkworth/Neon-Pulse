# Neon Pulse - Rhythm Runner

## Overview
An endless runner where obstacles spawn synchronized to music beats. Players must time their jumps to the rhythm for maximum points. Synthwave aesthetic with heavy visual juice.

## Core Gameplay

### Movement
- Auto-scrolling runner (player moves right automatically)
- Variable jump: TAP for short hop, HOLD for full height jump
- Double-jump always available (tap again while airborne)
- Snappy physics with high gravity for quick landings

### Rhythm System
- BPM-based obstacle spawning (120 BPM)
- Clear "JUMP" hit zone line at player position
- Player must jump when obstacles reach the hit zone
- Timing windows:
  - PERFECT: ±100ms (100 pts × combo) - hit zone turns GOLD
  - GOOD: ±200ms (50 pts × combo) - hit zone turns GREEN
  - MISS: 0 pts, reset combo, lose 1 health

### Obstacle Types
1. **Normal Spikes** (red) - Clear with single jump
2. **Tall Barriers** (orange, marked "2X") - Require double jump to clear
   - Appear after 30 seconds of gameplay
   - Have warning stripes pattern

### Obstacle Spacing
- Minimum 350px between obstacles (prevents impossible patterns)
- Consistent rhythm patterns for learnable gameplay

### Scoring
- Base points from timing accuracy
- Combo multiplier: 1x → 2x → 3x → 4x (max)
- Builds every 5 consecutive perfect/good hits
- Best combo tracked separately

### Health System
- 3 hearts/lives
- Lose 1 on collision/miss
- Game over at 0 health
- No health regeneration

## Visual Design

### Hit Zone Indicator
- Vertical line at player X position labeled "JUMP"
- Color-coded timing feedback:
  - Default: Cyan glow
  - Good timing window: Green
  - Perfect timing window: Gold
- Expanding ring pulses on every beat

### Approach Indicators
- Progress bar under each approaching obstacle
- Fills as obstacle nears hit zone
- Color shifts: cyan → green → gold as timing improves

### Player Character
- Diamond shape with inner glow
- Trail effect behind character
- Squash/stretch on jump and land
- Color shifts with multiplier level:
  - 1x: Cyan
  - 2x: Green
  - 3x: Yellow
  - 4x: Magenta
- Ring indicator when double jump is available

### Beat Effects
- Screen-wide magenta pulse on every beat
- Grid floor pulses brighter on beat
- Obstacles glow intensifies on beat

### Juice Effects
- Screen shake on miss
- Chromatic aberration on high combo
- Colored particle explosions (gold=perfect, cyan=good, red=miss)
- Flash effects matching timing quality

## Audio

### Music
- Procedural beat generation (Web Audio API)
- Kick drum on primary beats
- Hi-hat on off-beats
- Bass line unlocks at 2x combo
- Synth arpeggios unlock at 3x combo

### Sound Effects
- Jump: Quick ascending whoosh
- Perfect: Bright three-tone chime
- Good: Soft confirmation tone
- Miss: Low impact thud
- Combo milestone: Ascending fanfare

## Game States

### Title Screen
- "NEON PULSE" logo pulsing
- "RHYTHM RUNNER" subtitle
- "PRESS SPACE TO START"
- High score display

### Gameplay
- Main runner view
- HUD: Score (top-left), Multiplier (top-center), Health hearts (top-right)
- Ghost runner shows previous best run

### Game Over
- Final score with grade:
  - S: 95%+ accuracy
  - A: 80%+ accuracy
  - B: 60%+ accuracy
  - C: Below 60%
- Statistics: Perfect/Good/Miss counts
- Accuracy percentage
- Best combo achieved

## Progression

### Speed Ramp
- Base speed: 5
- Gradual increase over 45 seconds
- Cap at 1.8x base speed

### Difficulty Curve
- 0-30s: Normal spikes every 2 beats
- 30s+: Mix of normal and tall obstacles
- Tall obstacles appear ~25% of the time

## Technical

### Implementation
- Single HTML file with embedded CSS/JS
- Canvas-based rendering (1200x800 max)
- Web Audio API for procedural sound
- RequestAnimationFrame game loop
- LocalStorage for high score and ghost data

### Controls
- Space (tap): Short hop / Double jump
- Space (hold): Full height jump
- Click/Touch: Same as space
- M: Mute toggle

## Polish Features

### Ghost Mode
- Transparent cyan silhouette of previous best run
- Automatically loads from localStorage
- Updates when new high score achieved

### Visual Feedback
- Perfect: Gold particles + gold flash + chime
- Good: Cyan particles + cyan flash + soft tone
- Miss: Red flash + screen shake + thud

### Accessibility
- High contrast neon colors
- Multiple visual cues for timing (color + position + progress bar)
- Audio feedback for all actions
