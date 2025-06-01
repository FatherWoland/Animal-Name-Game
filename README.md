# Chrome Speech Recognition Test

This project provides tools to test Chrome's Web Speech API for speech recognition.

## Files

- `index.html` - User-friendly speech recognition test with colorful interface
- `diagnostics.html` - Technical diagnostic tool with advanced features

## Features

- Real-time speech recognition using Chrome's Web Speech API
- Microphone permission handling
- Error handling for common issues
- Diagnostic tools to troubleshoot problems
- Alternative solutions documentation

## Requirements

- HTTPS connection (or localhost)
- Chrome, Edge, or other Chromium-based browser
- Internet connection (Chrome's API requires this)
- Microphone permissions

## Known Limitations

- Chrome's Speech API stops after 60-120 seconds
- Requires internet connection for speech processing
- May not work in Electron or non-standard browser environments

## Deployment

This site is hosted on AWS S3 + CloudFront for HTTPS support.