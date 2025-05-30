# Dirty Rabbit NFC Clock Display with Audio Feedback

Professional NFC time tracking display page for Dirty Rabbit coffee shop employees.

## Features

- ✅ **Audio Feedback**: Gentle chime sounds for clock in/out actions
- ✅ **Professional UI**: Coffee shop branded interface
- ✅ **Employee Recognition**: Shows employee name and emoji
- ✅ **Spanish Interface**: Fully localized for Spanish staff
- ✅ **Auto-Close**: 5-second timer with automatic redirect
- ✅ **Mobile Optimized**: Perfect for NFC-enabled Android kiosk
- ✅ **Error Handling**: Visual and audio feedback for failures

## Audio Implementation

The page includes three types of audio feedback:
- **Clock In**: Success chime (green interface)
- **Clock Out**: Completion chime (red interface) 
- **Error**: Alert sound (orange interface)

### Audio Sources
- Primary: Google Actions CDN sounds (reliable)
- Fallback: Embedded data URL beeps (always work)
- Volume: 30% (gentle, non-intrusive)

### Browser Compatibility
- Auto-enables audio on any user interaction
- Works on Chrome, Safari, Firefox, Samsung Internet
- Handles audio policy restrictions gracefully

## URL Parameters

The page expects these parameters from the n8n webhook:

```
https://your-domain.com/?employee=DR001&status=success&action=CLOCK_IN&timestamp=...&hours=8.5
```

### Parameters:
- `employee`: DR001 (Maria), DR002 (Francisca), DR003 (Juan)
- `status`: success | error
- `action`: CLOCK_IN | CLOCK_OUT
- `timestamp`: ISO timestamp (optional)
- `hours`: Total hours worked (for clock out, optional)

## Employee Data

```javascript
const employees = {
    'DR001': { name: 'Maria Garcia', emoji: '👩‍💼' },
    'DR002': { name: 'Francisca Lopez', emoji: '👩‍🍳' },
    'DR003': { name: 'Juan Martinez', emoji: '👨‍💼' }
};
```

## Deployment

1. **GitHub Pages**: Already enabled at `https://spicycarrot25.github.io/dirty-rabbit-clock-display/`
2. **Custom Domain**: Point `clock.spicycarrot.xyz` to GitHub Pages
3. **n8n Integration**: Update redirect URLs in time tracking workflow

## Usage

1. Employee taps NFC tag
2. n8n processes time entry
3. Redirects to this display page with results
4. Page shows visual + audio confirmation
5. Auto-closes after 5 seconds

## Testing

Test with these URLs:
- Success: `?employee=DR001&status=success&action=CLOCK_IN`
- Error: `?employee=DR001&status=error`
- Clock Out: `?employee=DR001&status=success&action=CLOCK_OUT&hours=8.25`

## Audio Settings

For Android kiosk setup:
1. Enable "Allow Audio Playback" in browser settings
2. Set volume to ~30%
3. Test audio plays on first page load
4. Configure kiosk mode to allow audio

## Support

Part of the Dirty Rabbit AI-native time tracking system. For issues or modifications, update this repository and redeploy.