## Table of Contents

- [Download Manager Ubuntu](#download-manager-ubuntu)
  - [Tools Overview](#tools-overview)
  - [Installation](#installation)
- [YT-DLP Commands](#yt-dlp-commands)
  - [Basic Commands](#basic-commands)
  - [Format and Quality Options](#format-and-quality-options)
  - [Audio Extraction](#audio-extraction)
  - [Output Options](#output-options)
  - [Playlist Downloads](#playlist-downloads)
  - [Subtitles](#subtitles)
  - [Advanced Options](#advanced-options)
  - [Channel Downloads](#channel-downloads)
  - [Useful Combinations](#useful-combinations)
  - [Configuration File](#configuration-file)
  - [Common Examples](#common-examples)
  - [Supported Sites](#supported-sites)
  - [Help and Documentation](#help-and-documentation)
- [Using aria2c with yt-dlp for m3u8 Downloads](#using-aria2c-with-yt-dlp-for-m3u8-downloads)
  - [Install aria2c First](#install-aria2c-first)
  - [Basic aria2c Usage with yt-dlp](#basic-aria2c-usage-with-yt-dlp)
  - [Optimized aria2c Settings for m3u8](#optimized-aria2c-settings-for-m3u8)
  - [Complete m3u8 Download Command](#complete-m3u8-download-command)
  - [aria2c Specific Arguments for m3u8](#aria2c-specific-arguments-for-m3u8)
  - [Advanced Examples](#advanced-examples)
  - [Troubleshooting aria2c with m3u8](#troubleshooting-aria2c-with-m3u8)
  - [Performance Comparison](#performance-comparison)
  - [Create an Alias for Convenience](#create-an-alias-for-convenience)
  - [Key Benefits of aria2c for m3u8](#key-benefits-of-aria2c-for-m3u8)
  - [Quick Reference Commands](#quick-reference-commands)
- [How to Detect m3u8 Files on Websites](#how-to-detect-m3u8-files-on-websites)
  - [Method 1: Browser Developer Tools](#method-1-browser-developer-tools)
  - [Method 2: Browser Extensions](#method-2-browser-extensions)
  - [Method 3: Command Line Tools](#method-3-command-line-tools)
  - [Method 4: JavaScript Console Detection](#method-4-javascript-console-detection)
  - [Method 5: Using Specialized Tools](#method-5-using-specialized-tools)
  - [Method 6: Mobile Browser Detection](#method-6-mobile-browser-detection)
  - [Common m3u8 URL Patterns](#common-m3u8-url-patterns)
- [Additional Resources](#additional-resources)

# Download Manager Ubuntu
This documentation covers the usage of three powerful download tools on Ubuntu: yt-dlp, aria2c, and ffmpeg. These tools can be combined to create an efficient download management system.

## Tools Overview
### yt-dlp
yt-dlp is a feature-rich command-line download manager for video and audio content from various platforms including YouTube, Vimeo, and many other websites. It's a fork of youtube-dl with additional features and active maintenance.

### aria2c
aria2 is a lightweight multi-protocol & multi-source command-line download utility. It supports HTTP/HTTPS, FTP, SFTP, BitTorrent and Metalink, and can handle multiple connections per download for faster speeds.

### ffmpeg
FFmpeg is a complete solution for recording, converting, and streaming audio and video. It's often used in conjunction with yt-dlp for post-processing downloaded media.

## Installation
### Installing yt-dlp
```bash
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

### Installing aria2c
```bash
sudo apt update
sudo apt install aria2
```

### Installing FFmpeg
```bash
sudo apt update
sudo apt install ffmpeg
```

# YT-DLP Commands
## Basic Commands

**Download a video:**
```bash
yt-dlp "URL"
```

**Download audio only:**
```bash
yt-dlp -x "URL"
```

## Format and Quality Options
**List available formats:**
```bash
yt-dlp -F "URL"
```

**Download specific format:**
```bash
yt-dlp -f 137+140 "URL"  # Video format 137 + audio format 140
```

**Download best quality:**
```bash
yt-dlp -f "best[height<=1080]" "URL"  # Best quality up to 1080p
```

**Download worst quality (for slow connections):**
```bash
yt-dlp -f "worst" "URL"
```


## Audio Extraction

**Extract audio in specific format:**
```bash
yt-dlp -x --audio-format mp3 "URL"
yt-dlp -x --audio-format flac "URL"
yt-dlp -x --audio-format m4a "URL"
```

**Set audio quality:**
```bash
yt-dlp -x --audio-format mp3 --audio-quality 320K "URL"
```

## Output Options

**Custom filename:**
```bash
yt-dlp -o "%(title)s.%(ext)s" "URL"
yt-dlp -o "%(uploader)s - %(title)s.%(ext)s" "URL"
```

**Download to specific directory:**
```bash
yt-dlp -o "/path/to/directory/%(title)s.%(ext)s" "URL"
```

**Common filename templates:**
- `%(title)s` - Video title
- `%(uploader)s` - Channel name
- `%(upload_date)s` - Upload date (YYYYMMDD)
- `%(duration)s` - Video duration
- `%(view_count)s` - View count
- `%(like_count)s` - Like count


## Playlist Downloads

**Download entire playlist:**
```bash
yt-dlp "https://www.youtube.com/playlist?list=PLAYLIST_ID"
```

**Download specific range from playlist:**
```bash
yt-dlp --playlist-start 5 --playlist-end 10 "PLAYLIST_URL"
```

**Download only first N videos:**
```bash
yt-dlp --playlist-end 5 "PLAYLIST_URL"
```

**Reverse playlist order:**
```bash
yt-dlp --playlist-reverse "PLAYLIST_URL"
```

## Subtitles

**Download with subtitles:**
```bash
yt-dlp --write-subs "URL"
```

**Download auto-generated subtitles:**
```bash
yt-dlp --write-auto-subs "URL"
```

**Specific subtitle language:**
```bash
yt-dlp --write-subs --sub-langs "en,es,fr" "URL"
```

**Embed subtitles in video:**
```bash
yt-dlp --embed-subs "URL"
```

## Advanced Options

**Download with metadata:**
```bash
yt-dlp --write-info-json --write-thumbnail "URL"
```

**Set custom user agent:**
```bash
yt-dlp --user-agent "Mozilla/5.0..." "URL"
```

**Use proxy:**
```bash
yt-dlp --proxy "http://proxy-server:port" "URL"
```

**Limit download rate:**
```bash
yt-dlp --limit-rate 1M "URL"  # Limit to 1MB/s
```

**Continue interrupted downloads:**
```bash
yt-dlp -c "URL"
```


## Channel Downloads

**Download all videos from a channel:**
```bash
yt-dlp "https://www.youtube.com/@channelname"
```

**Download only recent videos:**
```bash
yt-dlp --dateafter 20231201 "CHANNEL_URL"  # After Dec 1, 2023
```

**Download videos matching criteria:**
```bash
yt-dlp --match-title "keyword" "CHANNEL_URL"
```

## Useful Combinations

**High-quality audio extraction:**
```bash
yt-dlp -x --audio-format flac --audio-quality 0 "URL"
```

**Download video with custom naming:**
```bash
yt-dlp -f "best[height<=1080]" -o "%(uploader)s/%(upload_date)s - %(title)s.%(ext)s" "URL"
```

**Download playlist with audio only:**
```bash
yt-dlp -x --audio-format mp3 --audio-quality 320K "PLAYLIST_URL"
```

## Configuration File

Create `~/.config/yt-dlp/config` file for default options:
```
# Default output template
-o ~/Downloads/%(uploader)s/%(title)s.%(ext)s

# Always extract audio
-x
--audio-format mp3
--audio-quality 320K

# Write metadata
--write-info-json
--write-thumbnail
```

## Common Examples

**Download YouTube video as MP3:**
```bash
yt-dlp -x --audio-format mp3 "https://youtu.be/VIDEO_ID"
```

**Download best quality under 2GB:**
```bash
yt-dlp -f "best[filesize<2G]" "URL"
```

**Download with progress bar:**
```bash
yt-dlp --newline "URL"
```

**Get video info without downloading:**
```bash
yt-dlp -j "URL"  # JSON format
yt-dlp --get-title "URL"  # Just title
yt-dlp --get-duration "URL"  # Just duration
```

## Supported Sites

yt-dlp supports 1000+ sites including YouTube, Vimeo, Twitter, Instagram, TikTok, Facebook, Dailymotion, and many more. Use the same commands for any supported site.

**Check if a site is supported:**
```bash
yt-dlp --list-extractors | grep -i "sitename"
```

## Help and Documentation

For more advanced features and options:
```bash
yt-dlp --help
```

# Using aria2c with yt-dlp for m3u8 Downloads

## Install aria2c First

**Install aria2c:**
```bash
sudo apt update
sudo apt install aria2
```

**Verify installation:**
```bash
aria2c --version
```

## Basic aria2c Usage with yt-dlp

**Simple command:**
```bash
yt-dlp --external-downloader aria2c "https://example.com/video.m3u8"
```

## Optimized aria2c Settings for m3u8

### Recommended Configuration

```bash
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 16 -s 16 -j 16" \
  "https://example.com/video.m3u8"
```

**Parameter explanation:**
- `-x 16` = Maximum 16 connections per download
- `-s 16` = Split download into 16 segments
- `-j 16` = Maximum 16 concurrent downloads

### Conservative Settings (for unstable connections)

```bash
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 4 -s 4 -j 4 --retry-wait=3" \
  "URL"
```

### Aggressive Settings (for fast, stable connections)

```bash
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 32 -s 32 -j 32 --max-overall-download-limit=0" \
  "URL"
```

## Complete m3u8 Download Command

**Full optimized command:**
```bash
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 16 -s 16 -j 16 --retry-wait=2 --max-tries=5" \
  --retries 10 \
  --fragment-retries 10 \
  --sleep-requests 1 \
  "https://example.com/video.m3u8"
```

## aria2c Specific Arguments for m3u8

### Connection Control

```bash
--external-downloader-args "-x 8 -s 8"           # 8 connections, 8 splits
--external-downloader-args "-j 4"                # 4 concurrent downloads
--external-downloader-args "--max-connection-per-server=8"
```

### Retry and Error Handling

```bash
--external-downloader-args "--retry-wait=3 --max-tries=10"
--external-downloader-args "--timeout=30 --connect-timeout=10"
```

### Speed Control

```bash
--external-downloader-args "--max-download-limit=5M"        # Limit to 5MB/s
--external-downloader-args "--max-overall-download-limit=0" # No limit
```

### Headers and User Agent

```bash
--external-downloader-args "--header='Referer: https://site.com'"
--external-downloader-args "--user-agent='Mozilla/5.0 (Linux)'"
```

## Advanced Examples

### For High-Quality m3u8

```bash
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 16 -s 16 -j 8 --retry-wait=2" \
  -f "best[height<=1080]" \
  --retries 5 \
  --fragment-retries 10 \
  "URL"
```

### For Slow/Unreliable Connections

```bash
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 4 -s 4 -j 2 --retry-wait=5 --max-tries=10 --timeout=60" \
  --sleep-requests 2 \
  --sleep-interval 1 \
  "URL"
```

### With Custom Headers

```bash
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 8 -s 8 --header='Referer: https://original-site.com'" \
  --add-header "User-Agent:Mozilla/5.0..." \
  "URL"
```

## Troubleshooting aria2c with m3u8

### If downloads are too aggressive

```bash
# Reduce connections and add delays
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 4 -s 4 -j 2 --retry-wait=3" \
  --sleep-requests 2 \
  "URL"
```

### For 403/429 errors

```bash
# Add user agent and reduce concurrent connections
yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 2 -s 2 -j 1 --user-agent='Mozilla/5.0 (Windows NT 10.0; Win64; x64)'" \
  --sleep-requests 3 \
  "URL"
```

### Check aria2c configuration

```bash
# Test aria2c directly
aria2c -x 8 -s 8 "https://example.com/video.m3u8"
```

## Performance Comparison

**Without aria2c (default):**
```bash
yt-dlp "URL"  # Sequential download
```

**With aria2c:**
```bash
yt-dlp --external-downloader aria2c --external-downloader-args "-x 16 -s 16" "URL"
# Parallel download - much faster for m3u8
```

## Create an Alias for Convenience

**Add to ~/.bashrc:**
```bash
alias yt-dlp-fast='yt-dlp --external-downloader aria2c --external-downloader-args "-x 16 -s 16 -j 8 --retry-wait=2"'
```

**Usage:**
```bash
yt-dlp-fast "https://example.com/video.m3u8"
```

## Key Benefits of aria2c for m3u8

- **Parallel downloads**: Multiple fragments simultaneously
- **Resume capability**: Continue interrupted downloads
- **Better error handling**: Automatic retries
- **Speed optimization**: Much faster than sequential download
- **Connection management**: Handles network issues better

## Quick Reference Commands

### Basic m3u8 Download
```bash
yt-dlp --external-downloader aria2c "URL"
```

### Optimized Download
```bash
yt-dlp --external-downloader aria2c --external-downloader-args "-x 16 -s 16 -j 8" "URL"
```

### Conservative Download
```bash
yt-dlp --external-downloader aria2c --external-downloader-args "-x 4 -s 4 -j 2 --retry-wait=3" "URL"
```

### With Quality Selection
```bash
yt-dlp --external-downloader aria2c --external-downloader-args "-x 8 -s 8" -f "best[height<=720]" "URL"
```

The key is finding the right balance of connections (`-x`), splits (`-s`), and concurrent jobs (`-j`) for your network and the server's capacity.

# How to Detect m3u8 Files on Websites
## Method 1: Browser Developer Tools

### Chrome/Firefox Developer Tools

**Step 1: Open Developer Tools**
```
F12 or Right-click → Inspect Element
```

**Step 2: Go to Network Tab**
- Click on "Network" tab
- Clear existing logs (🚫 icon)

**Step 3: Filter for Media Files**
- In the filter box, type: `m3u8` or `Media`
- Or click on "Media" filter button

**Step 4: Reload/Play Video**
- Refresh the page or start playing the video
- Watch for `.m3u8` files in the network requests

**Step 5: Copy m3u8 URL**
- Right-click on the m3u8 file → Copy → Copy link address

### Advanced Filtering

```
# Filter patterns in Network tab:
*.m3u8
master.m3u8
playlist.m3u8
index.m3u8
```

## Method 2: Browser Extensions

### Video DownloadHelper (Recommended)

```
1. Install Video DownloadHelper extension
2. Visit the video page
3. Click the extension icon
4. Look for HLS/m3u8 streams in the list
```

### Stream Detector

```
1. Install Stream Detector extension
2. Navigate to video page
3. Extension automatically detects m3u8 streams
4. Click to copy URLs
```

## Method 3: Command Line Tools

### Using yt-dlp to Extract m3u8

```bash
# Get video info (often reveals m3u8 URLs)
yt-dlp -j "https://website.com/video-page"

# List all available formats
yt-dlp -F "https://website.com/video-page"

# Verbose output to see m3u8 detection
yt-dlp -v "https://website.com/video-page"
```

### Using curl and grep

```bash
# Download page source and search for m3u8
curl -s "https://website.com/video-page" | grep -i "m3u8"

# More comprehensive search
curl -s "https://website.com/video-page" | grep -E "\.(m3u8|mpd)" -o
```

## Method 4: JavaScript Console Detection

### Manual JavaScript in Browser Console

```javascript
// Search for m3u8 in page source
document.documentElement.innerHTML.match(/https?:\/\/[^\s"']+\.m3u8[^\s"']*/g)

// Monitor network requests for m3u8
var originalOpen = XMLHttpRequest.prototype.open;
XMLHttpRequest.prototype.open = function(method, url) {
    if (url.includes('.m3u8')) {
        console.log('M3U8 detected:', url);
    }
    return originalOpen.apply(this, arguments);
};
```

### Advanced JavaScript Monitor

```javascript
// Comprehensive HLS detection script
(function() {
    // Monitor fetch requests
    const originalFetch = window.fetch;
    window.fetch = function(...args) {
        if (args[0].includes('.m3u8')) {
            console.log('M3U8 URL found via fetch:', args[0]);
        }
        return originalFetch.apply(this, args);
    };
    
    // Monitor video elements
    document.addEventListener('play', function(e) {
        if (e.target.tagName === 'VIDEO') {
            console.log('Video source:', e.target.src);
            console.log('Video sources:', Array.from(e.target.querySelectorAll('source')).map(s => s.src));
        }
    }, true);
})();
```

## Method 5: Using Specialized Tools

### FFprobe for Analysis

```bash
# If you suspect a URL contains m3u8
ffprobe -v quiet -print_format json -show_streams "https://example.com/video.m3u8"
```

### Using wget/curl to Test

```bash
# Test if URL is m3u8
curl -I "https://suspected-url.com/video.m3u8"

# Download and examine content
curl "https://example.com/video.m3u8" | head -20
```

## Method 6: Mobile Browser Detection

### Mobile Chrome

```
1. Open Chrome on mobile
2. Go to chrome://inspect/#devices
3. Enable USB debugging on phone
4. Inspect mobile page from desktop
5. Use Network tab as described above
```

## Common m3u8 URL Patterns

### Typical m3u8 URLs

```
https://example.com/hls/video.m3u8
https://cdn.example.com/live/stream/playlist.m3u8
https://streaming.site.com/videos/abc123/master.m3u8
https://media.example.com/v1/manifest.m3u8
```

### Search Patterns

```bash
# Grep patterns for finding m3u8
grep -i "\.m3u8"
grep -i "playlist\.m3u8"
grep -i "master\.m3u8"
grep -i "index\.m3u8"
```

# Additional Resources
- [yt-dlp GitHub Repository](https://github.com/yt-dlp/yt-dlp)
- [aria2 Documentation](https://aria2.github.io/)
- [FFmpeg Documentation](https://ffmpeg.org/documentation.html)
