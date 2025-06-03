# Overview
- Basic navigation and file operation: `ls`, `cd`, `pwd`, `mkdir`, `rmdir`, `cp`, `mv`, `rm`, and `touch`
- File permission and ownership: `chmod`, `chown`, and `chgrp`
- Text manipulation: `cat`, `less`, `head`, `tail`, `grep`, `sed`, `awk`, `sort`, `uniq`, and `wc`
- Input/output redirection: pipes (`|`), redirections (`>`, `>>`, `<`)
- Package management: `apt update`, `apt upgrade`, `apt install`, `apt remove`, and `apt search`
- System monitoring: `ps`, `top`, `htop`, `df`, `du`, `free`, `uname`, and `lsof`
- Study the manual: `man`, `--help`

# Command Line

## 1. Basic Navigation and File Operations

### `ls` - List Directory Contents

**Purpose**: Display files and directories in the current or specified directory.

**Basic Syntax**: `ls [options] [directory]`

**Common Options**:
- `-l`: Long format (detailed information)
- `-a`: Show hidden files (starting with .)
- `-h`: Human-readable file sizes
- `-t`: Sort by modification time
- `-r`: Reverse order
- `-R`: Recursive listing

**Examples**:
```bash
# Basic listing
ls
# Output: Documents Downloads Pictures Videos

# Detailed listing with permissions, size, date
ls -l
# Output: 
# drwxr-xr-x 2 user user 4096 Jan 15 10:30 Documents
# -rw-r--r-- 1 user user 1024 Jan 14 15:20 file.txt

# Show all files including hidden ones
ls -la
# Output includes files like .bashrc, .profile

# Human-readable file sizes
ls -lh
# Output: -rw-r--r-- 1 user user 1.5K Jan 14 15:20 file.txt

# List specific directory
ls /home/user/Documents

# Sort by modification time (newest first)
ls -lt

# Recursive listing (shows subdirectories)
ls -R
```

### `cd` - Change Directory

**Purpose**: Navigate between directories.

**Basic Syntax**: `cd [directory]`

**Special Paths**:
- `~`: Home directory
- `..`: Parent directory
- `-`: Previous directory
- `/`: Root directory

**Examples**:
```bash
# Go to home directory
cd ~
# or simply
cd

# Go to specific directory (absolute path)
cd /home/user/Documents

# Go to subdirectory (relative path)
cd Documents

# Go up one directory level
cd ..

# Go up two directory levels
cd ../..

# Go to previous directory
cd -

# Go to root directory
cd /

# Navigate to nested directories
cd Documents/Projects/Website
```

### `pwd` - Print Working Directory

**Purpose**: Display the current directory path.

**Basic Syntax**: `pwd [options]`

**Examples**:
```bash
# Show current directory
pwd
# Output: /home/user/Documents

# After changing directories
cd /var/log
pwd
# Output: /var/log
```

### `mkdir` - Make Directory

**Purpose**: Create new directories.

**Basic Syntax**: `mkdir [options] directory_name`

**Common Options**:
- `-p`: Create parent directories as needed
- `-m`: Set permissions
- `-v`: Verbose output

**Examples**:
```bash
# Create single directory
mkdir new_folder

# Create multiple directories
mkdir folder1 folder2 folder3

# Create nested directories (parent directories created automatically)
mkdir -p project/src/css
mkdir -p project/src/js
mkdir -p project/docs/images

# Create directory with specific permissions
mkdir -m 755 public_folder

# Verbose output (shows what's being created)
mkdir -v test_folder
# Output: mkdir: created directory 'test_folder'
```

### `rmdir` - Remove Directory

**Purpose**: Remove empty directories only.

**Basic Syntax**: `rmdir [options] directory_name`

**Common Options**:
- `-p`: Remove parent directories if they become empty
- `-v`: Verbose output

**Examples**:
```bash
# Remove empty directory
rmdir empty_folder

# Remove multiple empty directories
rmdir folder1 folder2 folder3

# Remove directory and its empty parent directories
rmdir -p project/src/css
# This removes css, then src (if empty), then project (if empty)

# Verbose removal
rmdir -v old_folder
# Output: rmdir: removing directory, 'old_folder'

# Note: This will fail if directory is not empty
rmdir non_empty_folder
# Output: rmdir: failed to remove 'non_empty_folder': Directory not empty
```

### `cp` - Copy Files and Directories

**Purpose**: Copy files and directories from source to destination.

**Basic Syntax**: `cp [options] source destination`

**Common Options**:
- `-r` or `-R`: Copy directories recursively
- `-i`: Interactive mode (prompt before overwriting)
- `-v`: Verbose output
- `-u`: Copy only when source is newer
- `-p`: Preserve file attributes

**Examples**:
```bash
# Copy single file
cp file.txt backup.txt

# Copy file to different directory
cp file.txt /home/user/Documents/

# Copy multiple files to directory
cp file1.txt file2.txt file3.txt /backup/

# Copy directory recursively
cp -r project/ project_backup/

# Interactive copy (asks before overwriting)
cp -i important.txt important_backup.txt

# Verbose copy
cp -v file.txt copy.txt
# Output: 'file.txt' -> 'copy.txt'

# Preserve file attributes (permissions, timestamps)
cp -p original.txt preserved_copy.txt

# Copy only if source is newer
cp -u newer_file.txt destination/
```

### `mv` - Move/Rename Files and Directories

**Purpose**: Move files/directories or rename them.

**Basic Syntax**: `mv [options] source destination`

**Common Options**:
- `-i`: Interactive mode (prompt before overwriting)
- `-v`: Verbose output
- `-u`: Move only when source is newer

**Examples**:
```bash
# Rename file
mv old_name.txt new_name.txt

# Rename directory
mv old_folder new_folder

# Move file to different directory
mv file.txt /home/user/Documents/

# Move multiple files
mv file1.txt file2.txt file3.txt /destination/

# Move with interactive confirmation
mv -i important.txt /backup/
# Output: mv: overwrite '/backup/important.txt'? 

# Verbose move
mv -v document.txt Documents/
# Output: 'document.txt' -> 'Documents/document.txt'

# Move directory
mv project/ /home/user/projects/
```

### `rm` - Remove Files and Directories

**Purpose**: Delete files and directories.

**Basic Syntax**: `rm [options] file/directory`

**Common Options**:
- `-r` or `-R`: Remove directories recursively
- `-f`: Force removal (no prompts)
- `-i`: Interactive mode (prompt for each file)
- `-v`: Verbose output

**Examples**:
```bash
# Remove single file
rm file.txt

# Remove multiple files
rm file1.txt file2.txt file3.txt

# Remove with confirmation
rm -i important.txt
# Output: rm: remove regular file 'important.txt'? 

# Remove directory and its contents
rm -r old_project/

# Force remove (be very careful!)
rm -rf unwanted_folder/

# Verbose removal
rm -v test.txt
# Output: removed 'test.txt'

# Remove all .tmp files
rm *.tmp

# WARNING: Never run this command!
# rm -rf /  (This would delete everything!)
```

### `touch` - Create Empty Files or Update Timestamps

**Purpose**: Create empty files or update file timestamps.

**Basic Syntax**: `touch [options] filename`

**Common Options**:
- `-a`: Change only access time
- `-m`: Change only modification time
- `-c`: Don't create file if it doesn't exist
- `-t`: Use specific timestamp

**Examples**:
```bash
# Create empty file
touch new_file.txt

# Create multiple empty files
touch file1.txt file2.txt file3.txt

# Update timestamp of existing file
touch existing_file.txt

# Create files with specific timestamp
touch -t 202301151030 dated_file.txt
# Format: YYYYMMDDhhmm

# Don't create if file doesn't exist (just update if exists)
touch -c maybe_exists.txt
```

## 2. File Permissions and Ownership

### `chmod` - Change File Permissions

**Purpose**: Modify file and directory permissions.

**Basic Syntax**: `chmod [options] mode file/directory`

**Permission System**:
- **User (u)**: Owner of the file
- **Group (g)**: Group that owns the file
- **Others (o)**: Everyone else
- **All (a)**: User, group, and others

**Permission Types**:
- **Read (r)**: 4 in numeric, allows reading file content
- **Write (w)**: 2 in numeric, allows modifying file
- **Execute (x)**: 1 in numeric, allows running file/accessing directory

**Examples**:
```bash
# Numeric method (most common)
chmod 755 script.sh
# 7 (owner): read(4) + write(2) + execute(1) = rwx
# 5 (group): read(4) + execute(1) = r-x
# 5 (others): read(4) + execute(1) = r-x

chmod 644 document.txt
# 6 (owner): read(4) + write(2) = rw-
# 4 (group): read(4) = r--
# 4 (others): read(4) = r--

chmod 600 private.txt
# 6 (owner): read(4) + write(2) = rw-
# 0 (group): no permissions = ---
# 0 (others): no permissions = ---

# Symbolic method
chmod u+x script.sh        # Add execute permission for user
chmod g-w file.txt          # Remove write permission for group
chmod o+r document.txt      # Add read permission for others
chmod a+r public_file.txt   # Add read permission for all

# Multiple permissions
chmod u+rw,g+r,o-rwx private.txt
chmod a+x executable.sh

# Recursive permission change
chmod -R 755 /var/www/html/

# Common permission patterns
chmod 777 file.txt    # Full permissions for everyone (dangerous!)
chmod 755 directory/  # Standard directory permissions
chmod 644 file.txt    # Standard file permissions
chmod 600 ~/.ssh/id_rsa  # Private key permissions
```

### `chown` - Change File Ownership

**Purpose**: Change file and directory ownership.

**Basic Syntax**: `chown [options] owner:group file/directory`

**Examples**:
```bash
# Change owner only
sudo chown newuser file.txt

# Change owner and group
sudo chown newuser:newgroup file.txt

# Change group only (notice the colon)
sudo chown :newgroup file.txt

# Recursive ownership change
sudo chown -R www-data:www-data /var/www/

# Copy ownership from another file
sudo chown --reference=template.txt new_file.txt

# Verbose output
sudo chown -v user:group file.txt
# Output: changed ownership of 'file.txt' from root:root to user:group

# Common examples
sudo chown $USER:$USER ~/downloaded_file.txt
sudo chown -R apache:apache /var/www/html/
```

### `chgrp` - Change Group Ownership

**Purpose**: Change group ownership of files and directories.

**Basic Syntax**: `chgrp [options] group file/directory`

**Examples**:
```bash
# Change group ownership
sudo chgrp developers project.txt

# Recursive group change
sudo chgrp -R staff /shared/documents/

# Verbose output
sudo chgrp -v users file.txt
# Output: changed group of 'file.txt' from root to users

# Copy group from another file
sudo chgrp --reference=template.txt new_file.txt

# Common usage
sudo chgrp www-data /var/www/html/index.html
```

## 3. Text Manipulation

### `cat` - Display File Contents

**Purpose**: Display, concatenate, and create files.

**Basic Syntax**: `cat [options] file(s)`

**Common Options**:
- `-n`: Number all lines
- `-b`: Number non-empty lines only
- `-s`: Squeeze multiple blank lines into one
- `-A`: Show all characters (including hidden ones)

**Examples**:
```bash
# Display file contents
cat file.txt

# Display multiple files
cat file1.txt file2.txt

# Display with line numbers
cat -n document.txt
# Output:
#      1	First line
#      2	Second line
#      3	

# Number only non-empty lines
cat -b document.txt

# Create a new file (Ctrl+D to save)
cat > new_file.txt
# Type content, press Ctrl+D when done

# Append to existing file
cat >> existing_file.txt

# Concatenate files into a new file
cat file1.txt file2.txt > combined.txt

# Show hidden characters
cat -A file_with_tabs.txt
```

### `less` - View File Contents Page by Page

**Purpose**: View large files one screen at a time.

**Basic Syntax**: `less [options] file`

**Navigation Keys**:
- `Space` or `Page Down`: Next page
- `b` or `Page Up`: Previous page
- `G`: Go to end of file
- `g`: Go to beginning of file
- `/pattern`: Search forward
- `?pattern`: Search backward
- `q`: Quit

**Examples**:
```bash
# View file
less large_file.txt

# View with line numbers
less -N file.txt

# Case-insensitive search
less -i file.txt

# View multiple files
less file1.txt file2.txt
# Use :n for next file, :p for previous file

# Follow file changes (similar to tail -f)
less +F log_file.txt

# Start at specific line
less +50 file.txt
```

### `head` - Display First Lines of File

**Purpose**: Show the beginning of files.

**Basic Syntax**: `head [options] file(s)`

**Common Options**:
- `-n NUM`: Show NUM lines (default is 10)
- `-c NUM`: Show NUM bytes
- `-q`: Quiet mode (don't show filenames)

**Examples**:
```bash
# Show first 10 lines (default)
head file.txt

# Show first 20 lines
head -n 20 file.txt
head -20 file.txt    # Shorthand

# Show first 100 bytes
head -c 100 file.txt

# Show first lines of multiple files
head file1.txt file2.txt

# Quiet mode (no filename headers)
head -q file1.txt file2.txt

# Show all but last 5 lines
head -n -5 file.txt
```

### `tail` - Display Last Lines of File

**Purpose**: Show the end of files, often used for log monitoring.

**Basic Syntax**: `tail [options] file(s)`

**Common Options**:
- `-n NUM`: Show NUM lines (default is 10)
- `-f`: Follow file changes (live monitoring)
- `-c NUM`: Show NUM bytes
- `-q`: Quiet mode

**Examples**:
```bash
# Show last 10 lines (default)
tail file.txt

# Show last 20 lines
tail -n 20 file.txt
tail -20 file.txt    # Shorthand

# Follow file changes (great for logs)
tail -f /var/log/syslog
# Press Ctrl+C to stop following

# Show last 100 bytes
tail -c 100 file.txt

# Follow multiple files
tail -f /var/log/apache2/access.log /var/log/apache2/error.log

# Show lines starting from line 50
tail -n +50 file.txt

# Combine with other commands
tail -f access.log | grep "404"
```

### `grep` - Search Text Patterns

**Purpose**: Search for patterns in files or input streams.

**Basic Syntax**: `grep [options] pattern file(s)`

**Common Options**:
- `-i`: Case-insensitive search
- `-v`: Invert match (show non-matching lines)
- `-n`: Show line numbers
- `-r`: Recursive search
- `-l`: Show only filenames with matches
- `-c`: Count matching lines

**Examples**:
```bash
# Basic search
grep "error" log.txt

# Case-insensitive search
grep -i "ERROR" log.txt

# Show line numbers
grep -n "function" script.js
# Output: 15:function myFunction() {

# Invert match (lines NOT containing pattern)
grep -v "debug" log.txt

# Recursive search in directory
grep -r "TODO" project/

# Search multiple files
grep "import" *.py

# Count occurrences
grep -c "error" log.txt
# Output: 23

# Show only filenames with matches
grep -l "class" *.java

# Regular expressions
grep "^Error" log.txt        # Lines starting with "Error"
grep "\.txt$" filelist.txt   # Lines ending with ".txt"
grep "[0-9]+" data.txt       # Lines containing numbers

# Multiple patterns
grep -E "(error|warning|critical)" log.txt

# Context lines
grep -A 3 "error" log.txt    # Show 3 lines after match
grep -B 2 "error" log.txt    # Show 2 lines before match
grep -C 2 "error" log.txt    # Show 2 lines before and after
```

### `sed` - Stream Editor

**Purpose**: Edit text streams and files using patterns.

**Basic Syntax**: `sed [options] 'command' file`

**Common Commands**:
- `s/old/new/`: Substitute text
- `d`: Delete lines
- `p`: Print lines
- `i`: Insert text

**Examples**:
```bash
# Replace first occurrence per line
sed 's/old/new/' file.txt

# Replace all occurrences (global)
sed 's/old/new/g' file.txt

# Case-insensitive replacement
sed 's/old/new/gi' file.txt

# Save changes to file (in-place editing)
sed -i 's/old/new/g' file.txt

# Create backup before editing
sed -i.bak 's/old/new/g' file.txt

# Delete lines containing pattern
sed '/pattern/d' file.txt

# Delete specific line numbers
sed '3d' file.txt           # Delete line 3
sed '2,5d' file.txt         # Delete lines 2-5

# Print specific lines
sed -n '1,10p' file.txt     # Print lines 1-10
sed -n '/pattern/p' file.txt # Print lines matching pattern

# Insert text before specific line
sed '5i\New line of text' file.txt

# Append text after specific line
sed '5a\New line of text' file.txt

# Multiple operations
sed -e 's/old/new/g' -e 's/foo/bar/g' file.txt
```

### `awk` - Text Processing Tool

**Purpose**: Pattern scanning and processing language.

**Basic Syntax**: `awk 'pattern { action }' file`

**Built-in Variables**:
- `NR`: Number of records (line number)
- `NF`: Number of fields in current record
- `$0`: Entire line
- `$1, $2, ...`: Individual fields

**Examples**:
```bash
# Print entire file
awk '{ print }' file.txt

# Print specific field (space-separated)
awk '{ print $1 }' file.txt        # First field
awk '{ print $1, $3 }' file.txt    # First and third fields

# Print with line numbers
awk '{ print NR, $0 }' file.txt

# Print lines containing pattern
awk '/pattern/ { print }' file.txt

# Print lines longer than 80 characters
awk 'length($0) > 80' file.txt

# Sum values in a column
awk '{ sum += $1 } END { print sum }' numbers.txt

# Print specific lines
awk 'NR==5' file.txt              # Line 5
awk 'NR>=5 && NR<=10' file.txt    # Lines 5-10

# Custom field separator
awk -F':' '{ print $1 }' /etc/passwd  # Print usernames

# Calculate average
awk '{ sum += $1; count++ } END { print sum/count }' numbers.txt

# Print number of fields per line
awk '{ print NF }' file.txt

# Conditional printing
awk '$3 > 100 { print $1, $3 }' data.txt
```

### `sort` - Sort Lines in Files

**Purpose**: Sort lines of text files.

**Basic Syntax**: `sort [options] file(s)`

**Common Options**:
- `-n`: Numeric sort
- `-r`: Reverse order
- `-k`: Sort by specific field
- `-t`: Field separator
- `-u`: Remove duplicates

**Examples**:
```bash
# Basic alphabetical sort
sort file.txt

# Numeric sort
sort -n numbers.txt

# Reverse sort
sort -r file.txt

# Sort by specific field (2nd field)
sort -k 2 data.txt

# Sort numerically by 3rd field
sort -k 3 -n data.txt

# Custom separator (sort CSV by 2nd column)
sort -t ',' -k 2 data.csv

# Remove duplicates while sorting
sort -u file.txt

# Sort by multiple fields
sort -k 1,1 -k 2,2n data.txt  # First field alphabetically, then 2nd numerically

# Case-insensitive sort
sort -f file.txt

# Sort by file size (with ls)
ls -l | sort -k 5 -n
```

### `uniq` - Remove Duplicate Lines

**Purpose**: Remove or report duplicate lines (input must be sorted).

**Basic Syntax**: `uniq [options] file`

**Common Options**:
- `-c`: Count occurrences
- `-d`: Show only duplicate lines
- `-u`: Show only unique lines
- `-i`: Case-insensitive

**Examples**:
```bash
# Remove duplicates (input must be sorted)
sort file.txt | uniq

# Count occurrences
sort file.txt | uniq -c
# Output:
#    3 apple
#    1 banana
#    2 orange

# Show only duplicate lines
sort file.txt | uniq -d

# Show only unique lines (appear once)
sort file.txt | uniq -u

# Case-insensitive duplicate removal
sort file.txt | uniq -i

# Find most common lines
sort file.txt | uniq -c | sort -nr
```

### `wc` - Word, Line, Character, and Byte Count

**Purpose**: Count lines, words, characters, and bytes in files.

**Basic Syntax**: `wc [options] file(s)`

**Common Options**:
- `-l`: Count lines only
- `-w`: Count words only
- `-c`: Count bytes only
- `-m`: Count characters only

**Examples**:
```bash
# Count lines, words, and bytes
wc file.txt
# Output: 15 67 432 file.txt (lines words bytes)

# Count lines only
wc -l file.txt
# Output: 15 file.txt

# Count words only
wc -w file.txt
# Output: 67 file.txt

# Count characters
wc -m file.txt

# Count bytes
wc -c file.txt

# Multiple files
wc *.txt

# Use with pipes
cat file.txt | wc -l
ls | wc -l              # Count files in directory
grep "error" log.txt | wc -l  # Count error lines
```

## 4. Input/Output Redirection

### Pipes (`|`)

**Purpose**: Connect output of one command to input of another.

**Examples**:
```bash
# Basic pipe
ls | grep ".txt"

# Multiple pipes
cat file.txt | grep "error" | wc -l

# Sort and remove duplicates
cat names.txt | sort | uniq

# Find largest files
ls -la | sort -k 5 -n | tail -5

# Process monitoring
ps aux | grep "firefox" | awk '{ print $2 }'

# Log analysis
tail -f /var/log/apache2/access.log | grep "404"

# Count unique IPs in log
cat access.log | awk '{ print $1 }' | sort | uniq -c | sort -nr
```

### Output Redirection (`>`, `>>`)

**Purpose**: Redirect command output to files.

**Examples**:
```bash
# Redirect output to file (overwrite)
ls > filelist.txt
echo "Hello World" > greeting.txt

# Append to file
echo "New line" >> existing_file.txt
date >> log.txt

# Redirect error output
command_that_might_fail 2> error.log

# Redirect both output and errors
command > output.log 2>&1
command &> all_output.log  # Shorter syntax

# Redirect to null (discard output)
noisy_command > /dev/null
command 2> /dev/null       # Discard errors only

# Save and display simultaneously
ls -la | tee output.txt    # Shows on screen AND saves to file
```

### Input Redirection (`<`)

**Purpose**: Use file contents as input to commands.

**Examples**:
```bash
# Use file as input
sort < unsorted.txt

# Mail content from file
mail user@example.com < message.txt

# Count lines in file
wc -l < file.txt

# Here document (multi-line input)
cat << EOF > config.txt
server=localhost
port=8080
debug=true
EOF

# Here string
grep "pattern" <<< "search in this string"
```

## 5. Package Management

### `apt update` - Update Package Index

**Purpose**: Download package information from all configured sources.

**Examples**:
```bash
# Update package database
sudo apt update

# Verbose output
sudo apt update -V

# Update specific source
sudo apt update -o Dir::Etc::sourcelist="sources.list.d/specific.list"
```

### `apt upgrade` - Upgrade Packages

**Purpose**: Install available upgrades of all packages currently installed.

**Examples**:
```bash
# Upgrade all packages
sudo apt upgrade

# Upgrade with automatic yes to prompts
sudo apt upgrade -y

# Show what would be upgraded without doing it
sudo apt upgrade --dry-run

# Upgrade specific package
sudo apt upgrade package_name

# Full upgrade (may remove packages if needed)
sudo apt full-upgrade
```

### `apt install` - Install Packages

**Purpose**: Install new packages.

**Examples**:
```bash
# Install single package
sudo apt install firefox

# Install multiple packages
sudo apt install vim git curl

# Install specific version
sudo apt install package_name=version

# Install from local .deb file
sudo apt install ./package.deb

# Install recommended packages too
sudo apt install --install-recommends package_name

# Download only (don't install)
sudo apt install --download-only package_name

# Simulate installation
sudo apt install --dry-run package_name

# Fix broken installations
sudo apt install -f
```

### `apt remove` - Remove Packages

**Purpose**: Remove installed packages.

**Examples**:
```bash
# Remove package (keep configuration files)
sudo apt remove package_name

# Remove package and configuration files
sudo apt purge package_name

# Remove multiple packages
sudo apt remove package1 package2 package3

# Remove package and its dependencies
sudo apt autoremove package_name

# Remove orphaned packages
sudo apt autoremove

# Simulate removal
sudo apt remove --dry-run package_name
```

### `apt search` - Search for Packages

**Purpose**: Search for packages in repositories.

**Examples**:
```bash
# Search for packages
apt search firefox

# Search in package names only
apt search --names-only editor

# Show full description
apt search -v text_editor

# Search for specific functionality
apt search "web browser"

# Case-insensitive search
apt search -i FIREFOX
```

## 6. System Monitoring

### `ps` - Display Running Processes

**Purpose**: Show information about running processes.

**Basic Syntax**: `ps [options]`

**Common Options**:
- `aux`: All processes, user-oriented format
- `-ef`: All processes, full format
- `-u user`: Processes for specific user
- `--forest`: Show process tree

**Examples**:
```bash
# Show processes for current user
ps

# Show all processes
ps aux

# Full format listing
ps -ef

# Show process tree
ps --forest
ps -ef --forest

# Processes for specific user
ps -u username

# Find specific process
ps aux | grep firefox

# Show processes using most CPU
ps aux --sort=-%cpu | head -10

# Show processes using most memory
ps aux --sort=-%mem | head -10

# Custom format
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem

# Show threads
ps -eLf
```

### `top` - Display and Update Running Processes

**Purpose**: Display and continuously update information about running processes.

**Interactive Commands**:
- `q`: Quit
- `k`: Kill process
- `r`: Renice process
- `M`: Sort by memory usage
- `P`: Sort by CPU usage
- `1`: Toggle CPU core display

**Examples**:
```bash
# Basic top
top

# Update every 2 seconds instead of default 3
top -d 2

# Show processes for specific user
top -u username

# Batch mode (non-interactive, good for scripts)
top -b -n 1

# Show only specific number of processes
top -n 1 | head -20

# Save output to file
top -b -n 1 > system_snapshot.txt
```

### `htop` - Enhanced Process Viewer

**Purpose**: Interactive process viewer (enhanced version of top).

**Note**: May need to install with `sudo apt install htop`

**Examples**:
```bash
# Run htop
htop

# Show processes for specific user
htop -u username

# Show process tree
htop -t

# No color mode
htop -C
```

### `df` - Display Filesystem Disk Space Usage

**Purpose**: Show disk space usage of mounted filesystems.

**Basic Syntax**: `df [options] [filesystem]`

**Common Options**:
- `-h`: Human-readable format
- `-T`: Show filesystem type
- `-i`: Show inode information
- `-a`: Show all filesystems

**Examples**:
```bash
# Basic disk usage
df

# Human-readable format
df -h
# Output:
# Filesystem      Size  Used Avail Use% Mounted on
# /dev/sda1        20G  12G  7.1G  63% /
# /dev/sda2       100G  45G   50G  48% /home

# Show filesystem types
df -hT

# Show specific filesystem
df -h /home

# Show inode usage
df -i

# Include all filesystems (including pseudo filesystems)
df -ha

# Exclude specific filesystem types
df -h -x tmpfs -x devtmpfs
```

### `du` - Display Directory Space Usage

**Purpose**: Show disk usage of directories and files.

**Basic Syntax**: `du [options] [directory]`

**Common Options**:
- `-h`: Human-readable format
- `-s`: Summary (total only)
- `-a`: Show all files, not just directories
- `-d`: Max depth level

**Examples**:
```bash
# Show size of current directory and subdirectories
du

# Human-readable format
du -h

# Summary of directory size only
du -sh
# Output: 2.3G    .

# Show size of specific directory
du -sh /home/user/Documents

# Show all files and directories
du -ah

# Limit depth
du -h -d 1          # Only 1 level deep
du -h --max-depth=2 # Only 2 levels deep

# Sort by size
du -h | sort -hr

# Find largest directories
du -sh */ | sort -hr

# Show top 10 largest files/directories
du -ah | sort -hr | head -10
```

### `free` - Display Memory Usage
**Purpose**: Show amount of free and used memory in the system.

**Basic Syntax**: `free [options]`

**Common Options**:
- `-h`: Human-readable format
- `-m`: Show in megabytes
- `-g`: Show in gigabytes
- `-s`: Continuous updates

**Examples**:
```bash
# Basic memory info
free

# Human-readable format
free -h
# Output:
#               total        used        free      shared  buff/cache   available
# Mem:           7.7G        2.1G        3.8G        256M        1.
```

