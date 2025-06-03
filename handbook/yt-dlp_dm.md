# Download Manager using yt-dlp

## 1. Overview

### 1.1 What is yt-dlp?

yt-dlp is a powerful, open-source command-line program for downloading videos and audio from YouTube and over 1000 other websites. It's a fork of youtube-dl with enhanced features, better performance, and active development.

### 1.2 Dependencies
Essential Dependencies for Full Functionality
- **FFmpeg**: Critical for most yt-dlp operations:
  - Converting between video/audio formats (MP4, WebM, MP3, etc.)
  - Merging separate video and audio streams (common with high-quality downloads)
  - Embedding subtitles directly into video files
  - Adding metadata and thumbnails to downloaded files
  - Fixing timestamp issues in downloaded content

- **aria2c**: Significantly improves download performance:
  - Downloads video segments in parallel instead of sequentially
  - Provides much faster speeds for segmented content (m3u8/HLS streams)
  - Better handling of network interruptions and resume capability
  - Essential for downloading from sites that split videos into multiple fragments

## 2. Installation

### 2.1 Method 1: Direct Download (Latest Version)

This method ensures you get the most recent version with latest site support and bug fixes.

```bash
# Download latest release
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp

# Make executable
sudo chmod a+rx /usr/local/bin/yt-dlp

# Verify installation
yt-dlp --version
```

### 2.2 Method 2: Using Package Manager

This method uses Ubuntu's official repositories but may have an older version.

```bash
# Update package list
sudo apt update

# Install yt-dlp
sudo apt install yt-dlp

# Verify installation
yt-dlp --version
```

### 2.3 Installing Essential Dependencies

```bash
# Install FFmpeg (essential for most operations)
sudo apt update
sudo apt install ffmpeg

# Install aria2 for faster downloads
sudo apt install aria2

# Verify installations
ffmpeg -version
aria2c --version
```

### 2.4 Post-Installation Setup

```bash
# Create downloads directory
mkdir -p ~/Downloads/yt-dlp

# Test installation
yt-dlp --help
```

## 3. Uninstallation

### 3.1 Determine Installation Method

```bash
# Find where yt-dlp is installed
which yt-dlp

# Check installation method based on location:
# /usr/local/bin/yt-dlp = Direct download
# /usr/bin/yt-dlp = apt package
```

### 3.2 Uninstall Methods

#### 3.2.1 If Installed via Direct Download

```bash
# Remove binary
sudo rm /usr/local/bin/yt-dlp

# Remove cache
rm -rf ~/.cache/yt-dlp
```

#### 3.2.2 If Installed via APT

```bash
# Remove package
sudo apt remove yt-dlp
sudo apt autoremove

# Remove cache
rm -rf ~/.cache/yt-dlp
```

### 3.3 Clean Up Configuration Files

```bash
# Remove configuration files (optional)
rm -rf ~/.config/yt-dlp

# Remove downloaded content (be careful!)
# rm -rf ~/Downloads/yt-dlp
```

## 4. Configuration

### 4.1 Configuration File Location

yt-dlp looks for configuration files in this order:
1. `~/.config/yt-dlp/config`
2. `~/.config/yt-dlp.conf`
3. `~/.yt-dlp.conf`

### 4.2 Creating Configuration File

```bash
# Create config directory
mkdir -p ~/.config/yt-dlp

# Create configuration file
nano ~/.config/yt-dlp/config
```

### 4.3 Sample Configuration File

```bash
# ~/.config/yt-dlp/config

# Output directory and filename template
-o ~/Downloads/yt-dlp/%(uploader)s/%(title)s.%(ext)s

# Video quality preference (best quality up to 1080p)
-f "best[height<=1080]"

# Always merge to MP4
--merge-output-format mp4

# Embed metadata and thumbnails
--embed-metadata
--embed-thumbnail

# Download subtitles
--write-subs
--write-auto-subs
--sub-langs "en,id"
--embed-subs

# Use external downloader for better performance
--external-downloader aria2c
--external-downloader-args "-x 8 -s 8 -j 4"

# Retry settings for reliability
--retries 5
--fragment-retries 10

# Safe filenames (remove special characters)
--restrict-filenames

# Add delay between downloads (be nice to servers)
--sleep-requests 1

# Continue incomplete downloads
--continue

# Ignore errors and continue with next video
--ignore-errors
```

### 4.4 Environment Variables

```bash
# Add to ~/.bashrc for permanent settings
export YT_DLP_CONFIG_HOME="$HOME/.config/yt-dlp"
export YT_DLP_CACHE_DIR="$HOME/.cache/yt-dlp"

# Reload bashrc
source ~/.bashrc
```

## 5. Syntax and Commands

### 5.1 Basic Syntax

```bash
yt-dlp [OPTIONS] URL [URL...]
```

### 5.2 Essential Options

| Option | Description | Example |
|--------|-------------|---------|
| `-o TEMPLATE` | Output filename template | `-o "%(title)s.%(ext)s"` |
| `-f FORMAT` | Video format selection | `-f "best[height<=720]"` |
| `-F` | List available formats | `-F` |
| `-x` | Extract audio only | `-x` |
| `--audio-format FORMAT` | Audio format | `--audio-format mp3` |
| `--audio-quality QUALITY` | Audio quality | `--audio-quality 320K` |
| `--merge-output-format FORMAT` | Container format | `--merge-output-format mp4` |
| `--write-subs` | Download subtitle files | `--write-subs` |
| `--embed-subs` | Embed subtitles in video | `--embed-subs` |
| `--embed-metadata` | Embed metadata | `--embed-metadata` |
| `--embed-thumbnail` | Embed thumbnail | `--embed-thumbnail` |

### 5.3 Format Selection Syntax

```bash
# Quality-based selection
-f "best"                    # Best available quality
-f "worst"                   # Worst available quality
-f "best[height<=1080]"      # Best quality up to 1080p
-f "best[height>=720]"       # Best quality 720p or higher
-f "best[filesize<500M]"     # Best quality under 500MB

# Format-based selection
-f "best[ext=mp4]"           # Best MP4 format
-f "bestvideo[ext=mp4]+bestaudio[ext=m4a]"  # Best MP4 video + M4A audio

# Codec-based selection
-f "best[vcodec=h264]"       # Best H.264 video
-f "best[acodec=aac]"        # Best AAC audio

# Multiple format fallback
-f "best[height<=1080]/best[height<=720]/best"  # Try 1080p, then 720p, then best
```

### 5.4 Output Template Variables

```bash
# Video information
%(title)s           # Video title
%(uploader)s        # Channel/uploader name
%(uploader_id)s     # Channel/uploader ID
%(upload_date)s     # Upload date (YYYYMMDD)
%(id)s              # Video ID
%(description)s     # Video description

# Technical information
%(ext)s             # File extension
%(duration)s        # Duration in seconds
%(duration_string)s # Duration as HH:MM:SS
%(filesize)s        # File size in bytes
%(height)s          # Video height (720, 1080, etc.)
%(width)s           # Video width
%(fps)s             # Frame rate
%(vcodec)s          # Video codec
%(acodec)s          # Audio codec

# Engagement metrics
%(view_count)s      # View count
%(like_count)s      # Like count
%(comment_count)s   # Comment count

# Playlist information
%(playlist)s        # Playlist title
%(playlist_id)s     # Playlist ID
%(playlist_index)s  # Position in playlist
%(playlist_count)s  # Total videos in playlist
```

## 6. Basic Usage

### 6.1 Simple Video Download

```bash
# Download a single video (uses config file settings)
yt-dlp "https://www.youtube.com/watch?v=VIDEO_ID"

# Download with custom filename
yt-dlp -o "my_video.%(ext)s" "https://www.youtube.com/watch?v=VIDEO_ID"

# Download to specific directory
yt-dlp -o "~/Videos/%(title)s.%(ext)s" "URL"
```

### 6.2 Checking Available Formats

```bash
# List all available formats
yt-dlp -F "URL"

# Get video information without downloading
yt-dlp --dump-json "URL"

# Simulate download (show what would be downloaded)
yt-dlp --simulate "URL"
```

### 6.3 Audio Extraction

```bash
# Extract audio in best quality
yt-dlp -x "URL"

# Extract as MP3 with specific quality
yt-dlp -x --audio-format mp3 --audio-quality 320K "URL"

# Extract as FLAC (lossless)
yt-dlp -x --audio-format flac "URL"

# Extract audio with metadata
yt-dlp -x --audio-format mp3 --embed-metadata --embed-thumbnail "URL"
```

### 6.4 Quality Selection

```bash
# Download best quality up to 1080p
yt-dlp -f "best[height<=1080]" "URL"

# Download 720p specifically
yt-dlp -f "best[height=720]" "URL"

# Download best MP4 format
yt-dlp -f "best[ext=mp4]" "URL"

# Download for slow connections
yt-dlp -f "worst" "URL"
```

### 6.5 Basic Playlist Downloads

```bash
# Download entire playlist
yt-dlp "https://www.youtube.com/playlist?list=PLAYLIST_ID"

# Download first 5 videos only
yt-dlp --playlist-end 5 "PLAYLIST_URL"

# Download videos 5-10 from playlist
yt-dlp --playlist-start 5 --playlist-end 10 "PLAYLIST_URL"
```

### 6.6 Subtitle Downloads

```bash
# Download video with English subtitles
yt-dlp --write-subs --sub-langs "en" "URL"

# Download with auto-generated subtitles
yt-dlp --write-auto-subs --sub-langs "en" "URL"

# Embed subtitles in video file
yt-dlp --embed-subs --sub-langs "en" "URL"

# Download only subtitles (no video)
yt-dlp --write-subs --sub-langs "en" --skip-download "URL"
```

### 6.7 Using External Downloaders

```bash
# Use aria2c for faster downloads
yt-dlp --external-downloader aria2c "URL"

# aria2c with custom settings for optimal performance
yt-dlp --external-downloader aria2c \
       --external-downloader-args "-x 8 -s 8 -j 4" "URL"
```

## 7. Advanced Usage

### 7.1 Batch Downloads

```bash
# Download from file containing URLs
yt-dlp -a urls.txt

# Example urls.txt content:
# https://www.youtube.com/watch?v=VIDEO1
# https://www.youtube.com/watch?v=VIDEO2
# https://www.youtube.com/playlist?list=PLAYLIST_ID

# Download with different settings per URL
yt-dlp -a urls.txt -o "%(uploader)s/%(title)s.%(ext)s"
```

### 7.2 Channel and User Downloads

```bash
# Download all videos from a channel
yt-dlp "https://www.youtube.com/@channelname"

# Download only recent videos (after specific date)
yt-dlp --dateafter 20240101 "https://www.youtube.com/@channelname"

# Download videos before specific date
yt-dlp --datebefore 20241231 "https://www.youtube.com/@channelname"

# Download videos within date range
yt-dlp --dateafter 20240101 --datebefore 20240630 "CHANNEL_URL"
```

### 7.3 Advanced Filtering

```bash
# Filter by title keywords
yt-dlp --match-title "tutorial" "CHANNEL_URL"

# Exclude videos by title
yt-dlp --reject-title "livestream|live" "CHANNEL_URL"

# Filter by duration (seconds)
yt-dlp --match-filter "duration > 300" "CHANNEL_URL"  # Longer than 5 minutes
yt-dlp --match-filter "duration < 3600" "CHANNEL_URL"  # Shorter than 1 hour

# Filter by view count
yt-dlp --match-filter "view_count > 10000" "CHANNEL_URL"

# Complex filtering
yt-dlp --match-filter "duration > 300 & view_count > 1000" "CHANNEL_URL"
```

### 7.4 External Downloaders

```bash
# Use aria2c for faster downloads with optimal settings
yt-dlp --external-downloader aria2c \
       --external-downloader-args "-x 16 -s 16 -j 8" "URL"

# Conservative settings for unstable connections
yt-dlp --external-downloader aria2c \
       --external-downloader-args "-x 4 -s 4 -j 2 --retry-wait=3" "URL"

# Use FFmpeg for m3u8/HLS streams
yt-dlp --external-downloader ffmpeg "URL"
```

### 7.5 Post-Processing

```bash
# Convert to specific format after download
yt-dlp --recode-video mp4 "URL"

# Re-encode with specific quality
yt-dlp --postprocessor-args "ffmpeg:-crf 23 -preset medium" "URL"

# Add custom FFmpeg arguments
yt-dlp --postprocessor-args "ffmpeg:-c:v libx264 -c:a aac -b:a 192k" "URL"

# Extract audio and keep video
yt-dlp --keep-video -x --audio-format mp3 "URL"
```

### 7.6 Live Streams

```bash
# Download live stream
yt-dlp "LIVE_STREAM_URL"

# Download live stream from the beginning
yt-dlp --live-from-start "LIVE_STREAM_URL"

# Wait for live stream to start
yt-dlp --wait-for-video 300 "SCHEDULED_STREAM_URL"  # Wait up to 5 minutes
```

### 7.7 Advanced Output Templates

```bash
# Organize by year and month
yt-dlp -o "%(uploader)s/%(upload_date>%Y)s/%(upload_date>%m)s/%(title)s.%(ext)s" "URL"

# Include video quality in filename
yt-dlp -o "%(title)s [%(height)sp].%(ext)s" "URL"

# Sanitize title and limit length
yt-dlp -o "%(title).100s.%(ext)s" --restrict-filenames "URL"

# Complex organization with metadata
yt-dlp -o "%(uploader)s/%(upload_date)s - %(title)s [%(id)s].%(ext)s" "URL"
```

### 7.8 Playlist Advanced Features

```bash
# Download playlist in reverse order
yt-dlp --playlist-reverse "PLAYLIST_URL"

# Extract specific videos by index
yt-dlp --playlist-items "1,3,5-8,10" "PLAYLIST_URL"

# Skip videos already downloaded
yt-dlp --download-archive downloaded.txt "PLAYLIST_URL"
```

## 8. Tips and Tricks

### 8.1 Performance Optimization

```bash
# Recommended fast download command
yt-dlp --external-downloader aria2c \
       --external-downloader-args "-x 8 -s 8 -j 4" \
       --merge-output-format mp4 \
       --embed-metadata \
       -f "best[height<=1080]" "URL"

# For slow connections
yt-dlp --limit-rate 500K \
       --socket-timeout 30 \
       --retries 10 \
       -f "best[height<=720]" "URL"
```

### 8.2 Useful Aliases

Add to `~/.bashrc`:

```bash
# Basic aliases
alias ytdl='yt-dlp'
alias ytdl-audio='yt-dlp -x --audio-format mp3 --audio-quality 320K'
alias ytdl-playlist='yt-dlp --external-downloader aria2c'
alias ytdl-fast='yt-dlp --external-downloader aria2c --external-downloader-args "-x 16 -s 16"'

# Quality-specific aliases
alias ytdl-720p='yt-dlp -f "best[height<=720]"'
alias ytdl-1080p='yt-dlp -f "best[height<=1080]"'
alias ytdl-4k='yt-dlp -f "best[height<=2160]"'

# Special purpose aliases
alias ytdl-subs='yt-dlp --write-subs --embed-subs --sub-langs "en,id"'
alias ytdl-info='yt-dlp --dump-json'
alias ytdl-formats='yt-dlp -F'
```

### 8.3 Content Organization

```bash
# Auto-organize by content type
yt-dlp -o "~/Downloads/Videos/%(uploader)s/%(title)s.%(ext)s" "VIDEO_URL"
yt-dlp -x -o "~/Downloads/Music/%(uploader)s/%(title)s.%(ext)s" "MUSIC_URL"

# Organize by date
yt-dlp -o "~/Downloads/%(upload_date>%Y-%m)s/%(uploader)s/%(title)s.%(ext)s" "URL"
```

### 8.4 Download Queue Management

```bash
# Create download queue
echo "URL1" >> ~/queue.txt
echo "URL2" >> ~/queue.txt

# Process queue
yt-dlp -a ~/queue.txt --download-archive ~/downloaded.txt

# Clear processed queue
> ~/queue.txt
```

### 8.5 Monitoring and Logging

```bash
# Log all downloads
yt-dlp "URL" 2>&1 | tee ~/yt-dlp.log

# Monitor download progress
yt-dlp --newline "URL"

# Get download statistics
yt-dlp --print-traffic "URL"
```

## 9. Troubleshooting

### 9.1 Common Issues and Solutions

#### 9.1.1 "Video unavailable" or "Private video"

```bash
# Check if video is actually available
yt-dlp --simulate "URL"

# Try with different user agent
yt-dlp --user-agent "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36" "URL"

# Use cookies from browser for private/member content
yt-dlp --cookies-from-browser firefox "URL"
```

#### 9.1.2 "No video formats found"

```bash
# List available formats to debug
yt-dlp -F "URL"

# Try different format selector
yt-dlp -f "best" "URL"

# Try audio-only if video fails
yt-dlp -f "bestaudio" "URL"

# Check if site is supported
yt-dlp --list-extractors | grep -i "sitename"
```

#### 9.1.3 "HTTP Error 403: Forbidden"

```bash
# Add referer header
yt-dlp --add-header "Referer:https://www.youtube.com" "URL"

# Use different user agent
yt-dlp --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36" "URL"

# Add delay between requests
yt-dlp --sleep-requests 3 "URL"
```

#### 9.1.4 Download speed too slow

```bash
# Use aria2c for parallel downloads
yt-dlp --external-downloader aria2c \
       --external-downloader-args "-x 16 -s 16 -j 8" "URL"

# Try different format (sometimes faster)
yt-dlp -f "worst" "URL"  # For testing

# Limit concurrent downloads if overwhelming server
yt-dlp --external-downloader aria2c \
       --external-downloader-args "-j 2" "URL"
```

#### 9.1.5 "FFmpeg not found" errors

```bash
# Install FFmpeg
sudo apt update
sudo apt install ffmpeg

# Specify FFmpeg location manually
yt-dlp --ffmpeg-location /usr/bin/ffmpeg "URL"

# Check if FFmpeg is in PATH
which ffmpeg
```

#### 9.1.6 Audio/video sync problems

```bash
# Force re-encoding with sync fix
yt-dlp --postprocessor-args "ffmpeg:-c copy -avoid_negative_ts make_zero" "URL"

# Try different format combination
yt-dlp -f "best[ext=mp4]" "URL"
```

#### 9.1.7 Aria2c temp files not cleaned up

```bash
# Remove aria2c temp files manually
find . -name "*.aria2__temp" -delete
find . -name "*.part-Frag*" -delete

# Use aria2c with auto-cleanup
yt-dlp --external-downloader aria2c \
       --external-downloader-args "-x 8 -s 8 --remove-control-file=true" "URL"
```

### 9.2 Debugging Commands

```bash
# Verbose output for debugging
yt-dlp -v "URL"

# Very verbose (includes HTTP traffic)
yt-dlp -vv "URL"

# Simulate download without downloading
yt-dlp --simulate --verbose "URL"

# Get detailed video information
yt-dlp --dump-json "URL"

# Test specific extractor
yt-dlp --test "URL"
```

### 9.3 Update and Maintenance

```bash
# Update yt-dlp to latest version (direct download method)
yt-dlp -U

# Update using package manager
sudo apt update && sudo apt upgrade yt-dlp

# Check version and supported sites
yt-dlp --version
yt-dlp --list-extractors
```

### 9.4 Cleanup and Maintenance

```bash
# Clear cache
yt-dlp --rm-cache-dir

# Remove temporary files
find ~/Downloads -name "*.part" -delete
find ~/Downloads -name "*.ytdl" -delete

# Check for corrupted downloads
find ~/Downloads -name "*.mp4" -exec ffprobe {} \; 2>&1 | grep -i error
```

## 10. Additional Recommendations

### 10.1 Recommended Daily Workflow

#### 10.1.1 Setup Phase
```bash
# Install with all dependencies
sudo apt update
sudo apt install ffmpeg aria2

# Install yt-dlp (choose one method from section 2)
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp

# Create organized directory structure
mkdir -p ~/Downloads/yt-dlp/{Videos,Audio,Playlists,Channels}

# Setup configuration file
mkdir -p ~/.config/yt-dlp
cp sample-config ~/.config/yt-dlp/config
```

#### 10.1.2 Daily Usage
```bash
# Check what you're downloading first
yt-dlp -F "URL"

# Use standard quality for most content
yt-dlp -f "best[height<=1080]" "URL"

# Archive what you've downloaded
yt-dlp --download-archive ~/Downloads/downloaded.txt "URL"
```

#### 10.1.3 Maintenance
```bash
# Weekly updates
yt-dlp -U

# Monthly cleanup
yt-dlp --rm-cache-dir
find ~/Downloads -name "*.part" -delete
```

### 10.2 Essential Automation Scripts

#### 10.2.1 Daily Download Script
```bash
#!/bin/bash
# ~/bin/ytdl-daily.sh

URL="$1"
QUALITY="${2:-1080}"

if [ -z "$URL" ]; then
    echo "Usage: $0 <URL> [quality]"
    echo "Quality options: 720, 1080, 1440, 2160 (default: 1080)"
    exit 1
fi

echo "Downloading from: $URL"
echo "Quality: ${QUALITY}p"

yt-dlp \
  --external-downloader aria2c \
  --external-downloader-args "-x 8 -s 8 -j 4 --remove-control-file=true" \
  --merge-output-format mp4 \
  --embed-metadata \
  --embed-thumbnail \
  --retries 5 \
  --fragment-retries 10 \
  -f "best[height<=${QUALITY}]" \
  -o "~/Downloads/yt-dlp/%(uploader)s/%(title)s.%(ext)s" \
  --restrict-filenames \
  "$URL"

echo "Download completed!"
```

#### 10.2.2 Audio Extraction Script
```bash
#!/bin/bash
# ~/bin/extract-audio.sh

URL="$1"
FORMAT="${2:-mp3}"
QUALITY="${3:-320K}"

if [ -z "$URL" ]; then
    echo "Usage: $0 <URL> [format] [quality]"
    echo "Format options: mp3, flac, aac (default: mp3)"
    echo "Quality options: 128K, 192K, 320K (default: 320K)"
    exit 1
fi

yt-dlp \
  -x \
  --audio-format "$FORMAT" \
  --audio-quality "$QUALITY" \
  --embed-metadata \
  --embed-thumbnail \
  -o "~/Downloads/yt-dlp/Audio/%(uploader)s/%(title)s.%(ext)s" \
  --restrict-filenames \
  "$URL"
```

### 10.3 Browser Integration

#### 10.3.1 Browser Extensions
- Install "Video DownloadHelper" or similar extensions
- Configure to use yt-dlp for downloads
- Set custom download directory

#### 10.3.2 Command Line Integration
```bash
# Stream directly to media player without downloading
alias ytplay='yt-dlp -f "best[height<=720]" -o - "$1" | mpv -'

# Usage: ytplay "URL"
```

### 10.4 Backup and Organization

#### 10.4.1 Backup Strategy
```bash
# Create backup of downloads
rsync -av ~/Downloads/yt-dlp/ ~/Backup/yt-dlp/

# Sync to external drive
rsync -av --progress ~/Downloads/yt-dlp/ /media/external/yt-dlp/
```

#### 10.4.2 Content Organization
```bash
# Organize downloads by type and date
yt-dlp -o "~/Downloads/yt-dlp/%(uploader)s/%(upload_date>%Y-%m)s/%(title)s.%(ext)s" "URL"

# Separate music and videos automatically
yt-dlp -x -o "~/Music/%(uploader)s/%(title)s.%(ext)s" "MUSIC_URL"
yt-dlp -o "~/Videos/%(uploader)s/%(title)s.%(ext)s" "VIDEO_URL"
```