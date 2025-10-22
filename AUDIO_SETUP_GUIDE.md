# 🎵 Audio Setup Guide - Adding Background Music

This guide explains how to add background music to your Prompt Engineering Battle Royale application.

## 📁 Supported Audio Formats

The application supports the following audio formats:

| Format | Extension | Browser Support | Recommended |
|--------|-----------|-----------------|-------------|
| M4A (AAC) | `.m4a` | ✅ Chrome, Safari, Edge | ✅ Yes |
| MP3 | `.mp3` | ✅ All modern browsers | ✅ Yes |
| OGG | `.ogg` | ✅ Chrome, Firefox | ⚠️ No Safari |
| WAV | `.wav` | ✅ All modern browsers | ❌ Large file size |

**✅ M4A files work great!** They're supported in all modern browsers and provide good quality with reasonable file sizes.

---

## 🎶 Adding Your Music File

### Step 1: Prepare Your Audio File

1. **Get your M4A file** (or convert your audio to M4A/MP3)
2. **Recommended specs**:
   - Format: M4A (AAC) or MP3
   - Bitrate: 128kbps - 192kbps (good balance of quality and size)
   - Length: Loop-friendly (seamless beginning and end)
   - Volume: Normalized (not too loud or quiet)

### Step 2: Add to Project

Copy your audio file to the project:

```bash
# Copy your M4A file to the assets/audio folder
cp /path/to/your/music.m4a "/Users/cbrondon/Downloads/Prompt Eng Training Proto/assets/audio/background-music.m4a"
```

Or simply drag and drop the file into:
```
Prompt Eng Training Proto/
└── assets/
    └── audio/
        └── background-music.m4a  👈 Your file here
```

### Step 3: Multiple Music Tracks (Optional)

You can add multiple tracks for different screens:

```
assets/audio/
├── menu-music.m4a       # For lobby/menu screens
├── battle-music.m4a     # For battle arena
└── victory-music.m4a    # For win screens
```

---

## 🎚️ Audio Controls Included

The application now includes:

✅ **Music toggle button** - Play/pause background music
✅ **Volume slider** - Adjust music volume (0-100%)
✅ **Persistent settings** - Your preferences are saved
✅ **Auto-play support** - Respects browser autoplay policies
✅ **Mute option** - Quick mute when needed

---

## 🎮 How It Works

### Audio Control Panel

The audio control panel appears in the bottom-right corner of the screen:

- **🔊/🔇 Icon** - Click to toggle music on/off
- **Volume Slider** - Drag to adjust volume
- **Minimize Button** - Collapse the control panel

### User Experience

- Music **doesn't auto-play** on page load (browser restrictions)
- Users can enable music with one click
- Settings persist across sessions
- Volume defaults to 50%

---

## 🔧 Configuration

### Updating the Audio File Path

The audio file path is configured in `/js/config.js`:

```javascript
// In CONFIG object
AUDIO: {
    BACKGROUND_MUSIC: './assets/audio/background-music.m4a',
    DEFAULT_VOLUME: 0.5,  // 50% volume
    LOOP: true,            // Loop continuously
    AUTOPLAY: false        // Don't autoplay (browser policy)
}
```

### Changing the Default Music File

Edit `/js/config.js` and update the path:

```javascript
BACKGROUND_MUSIC: './assets/audio/your-custom-music.m4a'
```

---

## 🎵 Music Recommendations

### For Training/Learning Apps:

**Best music types:**
- ✅ Lo-fi hip hop beats
- ✅ Ambient electronic
- ✅ Chill instrumental
- ✅ Light classical
- ✅ Soft jazz

**Avoid:**
- ❌ Music with lyrics (distracting)
- ❌ Loud/intense music
- ❌ Dramatic music with ups and downs
- ❌ Music that draws attention

### Free Music Resources:

**Royalty-free music sources:**
- [YouTube Audio Library](https://www.youtube.com/audiolibrary) - Free for commercial use
- [Incompetech](https://incompetech.com/music/) - Creative Commons
- [FreePD](https://freepd.com/) - Public domain
- [Bensound](https://www.bensound.com/) - Free with attribution
- [Purple Planet](https://www.purple-planet.com/) - Free for all uses

**For internal company use:**
- Check your company's licensed music library
- Use royalty-free music services your company subscribes to
- Create custom music or hire a composer

---

## 🛠️ Advanced Customization

### Multiple Tracks for Different Screens

To play different music on different screens, modify `/js/main.js`:

```javascript
// Example: Different music for battle screen
function showScreen(screenName) {
    // ... existing code ...

    if (screenName === 'battle') {
        changeBackgroundMusic('./assets/audio/battle-music.m4a');
    } else if (screenName === 'lobby') {
        changeBackgroundMusic('./assets/audio/menu-music.m4a');
    }
}
```

### Fade In/Fade Out

Add smooth transitions between tracks:

```javascript
function fadeOutMusic(duration = 1000) {
    const audio = document.getElementById('background-music');
    const startVolume = audio.volume;
    const fadeStep = startVolume / (duration / 50);

    const fadeInterval = setInterval(() => {
        if (audio.volume > 0.01) {
            audio.volume -= fadeStep;
        } else {
            audio.volume = 0;
            audio.pause();
            clearInterval(fadeInterval);
        }
    }, 50);
}
```

### Sound Effects

Add sound effects for UI interactions:

```javascript
// Add to assets/audio/
// - click.m4a
// - success.m4a
// - error.m4a
// - achievement.m4a

function playSound(soundName) {
    const audio = new Audio(`./assets/audio/${soundName}.m4a`);
    audio.volume = 0.3; // Quieter for SFX
    audio.play().catch(err => console.log('Sound play failed:', err));
}

// Use in your code:
playSound('success'); // On battle win
playSound('achievement'); // On achievement unlock
```

---

## 🐛 Troubleshooting

### Music Not Playing

**Issue**: Music doesn't start when clicking play button

**Solutions**:
1. **Check browser console** (F12) for errors
2. **Verify file path** is correct in config.js
3. **Check file format** - ensure it's M4A or MP3
4. **Test file** - try opening it directly in browser
5. **Browser policy** - some browsers block autoplay until user interaction

### Music Cuts Off or Stutters

**Issue**: Audio playback is choppy

**Solutions**:
1. **Reduce file size** - compress to 128kbps
2. **Preload audio** - audio loads before playing
3. **Check network** - ensure stable connection if hosted remotely
4. **Use local files** - host audio with the app, not CDN

### Volume Control Not Working

**Issue**: Slider doesn't change volume

**Solutions**:
1. **Check JavaScript errors** in console
2. **Verify audio element** has ID `background-music`
3. **Test in different browser** - may be browser-specific issue
4. **Clear browser cache** and reload

---

## 📱 Mobile Considerations

### iOS Safari

- **Autoplay blocked** - User must tap to enable
- **Background playback** - Pauses when app loses focus
- **Volume locked** - Physical volume buttons control audio

### Android Chrome

- **Better autoplay support** - Works with user gesture
- **Background playback** - Can continue playing
- **Volume control** - Both software and hardware work

### Best Practices

- ✅ Always provide visible play button
- ✅ Save user's preference (music on/off)
- ✅ Don't force music - let users choose
- ✅ Provide volume control
- ✅ Use compressed audio files

---

## 📊 File Size Guidelines

| Quality | Bitrate | 1 min | 5 min | 10 min |
|---------|---------|-------|-------|--------|
| Low | 96kbps | 720KB | 3.6MB | 7.2MB |
| Good | 128kbps | 960KB | 4.8MB | 9.6MB |
| High | 192kbps | 1.4MB | 7.2MB | 14.4MB |
| Very High | 320kbps | 2.4MB | 12MB | 24MB |

**Recommended**: 128kbps for background music (good quality, reasonable size)

---

## ✅ Quick Checklist

Before deploying with audio:

- [ ] Audio file added to `/assets/audio/` folder
- [ ] File path updated in `/js/config.js`
- [ ] File format is M4A or MP3
- [ ] File size is reasonable (< 10MB for 5-min track)
- [ ] Tested in multiple browsers (Chrome, Safari, Firefox)
- [ ] Volume control works
- [ ] Toggle button works
- [ ] Settings persist after page reload
- [ ] Mobile tested (if applicable)
- [ ] Audio is loop-friendly (no jarring restarts)

---

## 🎨 Customizing the Audio Control UI

The audio controls are styled in `/css/main.css`. You can customize:

- Position (default: bottom-right)
- Colors
- Size
- Icons
- Animation

Example customization in CSS:

```css
.audio-control-panel {
    bottom: 100px;  /* Move higher */
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);  /* Purple gradient */
    border-radius: 20px;  /* More rounded */
}
```

---

## 📞 Need Help?

**Common questions:**

**Q: Can I use Spotify/Apple Music links?**
A: No, those require authentication and won't work in an embedded player. Use downloaded audio files.

**Q: What if my file is too large?**
A: Compress it using online tools like:
- [Audio Compressor](https://www.audiocompressor.com/)
- [Online Audio Converter](https://online-audio-converter.com/)
- FFmpeg (command line): `ffmpeg -i input.m4a -b:a 128k output.m4a`

**Q: Can I have different music for different players?**
A: Not with this setup - all players hear the same music. For personalized audio, you'd need a more complex system.

**Q: Does this affect page load time?**
A: Slightly. The audio file loads in the background. For a 5MB file at decent connection, it's 1-2 seconds.

---

## 🎉 You're All Set!

Your application now has background music! Enjoy the enhanced experience. 🎵

Remember:
- Keep volume moderate (default 50%)
- Use loop-friendly tracks
- Test across browsers
- Respect user choice (don't force music on)

Happy gaming! 🎮
