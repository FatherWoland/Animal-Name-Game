# Claude Context File - Animal Name Game

## Quick Project Overview
This is an interactive children's game that uses speech recognition to teach animal facts. When a child says an animal name, the game shows an animation and speaks three facts in a British female voice.

## Key Files
- `animal-game.html` - Main game (50 animals, facts, animations)
- `index.html` - Simple speech test & game launcher  
- `diagnostics.html` - Technical troubleshooting tool
- Live at: https://fatherwoland.github.io/Animal-Name-Game/

## Current Status
✅ Fully functional game with 50 animals
✅ Speech recognition working (Chrome/Edge)
✅ British female voice narration
✅ CSS animations for each animal
✅ Auto-restarts listening after speaking facts

## Recent Work
- Fixed voice to be female and slower (rate: 0.75)
- Stopped fact repetition issue
- Added auto-restart listening after speech ends
- Created animation recommendations guide

## Known Issues
- Chrome Speech API has 60-120 second limit
- Requires internet connection
- Basic CSS animations (could upgrade to Lottie/Rive)

## Next Steps Discussed
- Implement Lottie animations for studio quality
- Add score tracking and quiz mode
- Consider offline support with Whisper.js

## Tech Stack
- Vanilla JavaScript (no frameworks)
- Web Speech API for recognition
- Speech Synthesis API for voice
- CSS animations
- GitHub Pages hosting

## Git Info
- Repo: https://github.com/FatherWoland/Animal-Name-Game
- User: FatherWoland (mark@pensionable.ai)
- All changes auto-deploy to GitHub Pages

## Important Context
- Originally created to debug Linux VM speech recognition issues
- Designed for children with playful UI
- British accent was specifically requested
- User wants studio-quality animations (see animation-recommendations.md)