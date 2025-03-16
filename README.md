# PREVIEW - A Bash File Manager with Preview Capabilities

**PREVIEW** is a lightweight, efficient file manager written in `Bash`, designed to provide seamless file navigation and preview functionalities in the terminal. Inspired by tools like `fff`, `lesspipe`, and `ranger`, it builds upon the `lf` foundation, enhancing file previews with customizable commands and configurable shortcuts. This script is part of the **[shell_utils](https://github.com/felipefacundes/shell_utils)** framework, one of the largest collections of scripts and utilities aimed at simplifying and enhancing user experience in the terminal.

## Features
- **File Previews**: Supports previews for various file types including text, images, archives, PDFs, and more, with configurable tools like `img2sixel`, `viu`, `glow`, and others.
- **Customizable Shortcuts**: Offers extensive key bindings for navigation, file operations (copy, move, delete, etc.), and toggling preview modes.
- **Color Support**: Integrates with `LS_COLORS` for visually appealing file listings.
- **Configuration**: Comes with a detailed configuration file (`preview.conf`) allowing users to tweak settings like preview modes, colors, and key mappings.
- **Cross-Platform**: Works across different Unix-like systems with adaptive behavior for environments like Termux.

## Installation
To install and use PREVIEW, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/felipefacundes/preview.git
   cd preview

    Make the Script Executable:
    bash

    chmod +x preview

    Run the Script:
    bash

    ./preview

    Optional - Move to a System Path:
    For easy access, you can move it to a directory in your $PATH (e.g., /usr/bin):
    bash

    sudo mv preview /usr/bin/

### Distros

- Arch Linux: `yay -S preview`

### Usage
Once installed, simply run preview in your terminal to start the file manager. Use the default or customized key bindings to navigate directories, preview files, and perform operations. The script automatically generates a configuration file at ~/.config/preview/preview.conf on first run, which you can edit to tailor the experience to your needs.
Example Commands

    Start in the current directory: preview
    Start in a specific directory: preview /path/to/directory
    Show version: preview -v
    Show help: preview -h

```bash
# Usage for Preview File Manager
# A simple file manager with preview capabilities written in Bash.

# Navigation
j or Down Arrow:    Scroll down
k or Up Arrow:      Scroll up
h or Left Arrow or Backspace:  Go to parent directory
l or Right Arrow:   Enter child directory or open file
- :                 Go to previous directory
g:                  Go to top of file list
G:                  Go to bottom of file list
Ctrl+G:             Go to a specific directory (type path)
~ or H:             Go to home directory
r:                  Refresh current directory

# File and Directory Actions
F:                  Create new file
m:                  Create new directory
R:                  Rename file or directory
X:                  Toggle executable permission
e:                  Extract archive to folder
E:                  Delete file or marked files
C:                  Copy file or marked files
M:                  Move file or marked files
Z:                  Copy file to clipboard (images or text, max 10MB)

# Marking Files
y:                  Mark/unmark current file
Y:                  Mark/unmark all files in current directory
c:                  Clear all marked files

# Preview and Display
P or Ctrl+P:        Toggle preview/normal mode
i:                  Show file info or full-screen image preview
x:                  View file attributes (using 'stat')
.:                  Toggle hidden files visibility
/:                  Search files in current directory
' or ":             Exit search mode (preserves selection)

# Miscellaneous
!:                  Open shell in current directory
Ctrl+D or = or Q or q:  Quit (cd to last directory if enabled)
0-9:                Go to favorite directory (if set via PREVIEW_FAV_[0-9])

# Notes
- In preview mode, the screen splits to show file previews below the file list.
- In normal mode, the full screen shows the file list.
- Marked files persist within the same directory; changing directories clears marks.
- Search filters the file list dynamically; use ' or " to exit and restore the full list.
- Favorite directories can be set in the config file (e.g., PREVIEW_FAV_0=/path).
```

### Configuration and Customization
The configuration file (preview.conf) is extensively documented within the script. It allows customization of:

    Preview mode (on/off)
    Maximum items displayed
    Hidden file visibility
    Colors for directories, status lines, and highlights
    Key bindings for all actions
    Preferred tools for file previews (e.g., markdown, images)

Edit ~/.config/preview/preview.conf to adjust these settings.

```bash
# Customization for Preview File Manager
# Configuration file: ${XDG_CONFIG_HOME:-$HOME/.config}/preview/preview.conf
# Cache directory: ${XDG_CACHE_HOME:-$HOME/.cache}/preview

# Default preview mode
# 0: Normal mode (full file list), 1: Preview mode (split screen with previews)
# Default: 1
export PREVIEW_MODE=1

# Maximum items to show in preview mode
# Number of files displayed in the file list in preview mode
# Default: 9
export PREVIEW_MAX_ITEMS=9

# Show hidden files by default
# 0: Hidden files off, 1: Hidden files on
# Default: 0
export PREVIEW_HIDDEN=0

# Use LS_COLORS for file coloring
# 0: Disable, 1: Enable (uses LS_COLORS if available)
# Default: 1
export PREVIEW_LS_COLORS=1

# File format string
# Customize how file names are displayed (%f is the filename)
# Example: "\t%f" (tab before filename)
# Default: "%f"
export PREVIEW_FILE_FORMAT="%f"

# Mark format string
# Customize how marked files are displayed (%f is the filename)
# Example: "> %f" (prefix with ">")
# Default: "" (none)
export PREVIEW_MARK_FORMAT=""

# Default file opener
# Command to open files when no specific handler is found
# Default: "xdg-open"
export PREVIEW_OPENER="xdg-open"

# Change directory on exit
# 0: Disable, 1: Enable (cd to last directory on exit)
# Default: 1
export PREVIEW_CD_ON_EXIT=1

# File to store last directory for CD on exit
# Default: "${XDG_CACHE_HOME:-$HOME/.cache}/preview/.preview_d"
export PREVIEW_CD_FILE="${XDG_CACHE_HOME:-$HOME/.cache}/preview/.preview_d"

# Color for directories
# ANSI color code [0-9]
# Default: 2 (blue)
export PREVIEW_COL_DIRECTORY=2

# Color for marked files
# ANSI color code [0-9]
# Default: 1 (red)
export PREVIEW_COL_MARKED=1

# Status line background color
# ANSI background code (e.g., 48;5;128 for purple)
# Default: "48;5;128" (purple)
export PREVIEW_STATUS_BACKGROUND="48;5;128"

# Status line foreground color
# ANSI foreground code (e.g., 1;38;5;16 for black)
# Default: "1;38;5;16" (black)
export PREVIEW_STATUS_FOREGROUND="1;38;5;16"

# Selected item highlight color
# ANSI color code [0-9]
# Default: 6 (cyan)
export PREVIEW_SELECTED_HIGHLIGHT=6

# Previous directory color in status line
# ANSI foreground code (e.g., 1;38;5;16 for black)
# Default: "1;38;5;16" (black)
export PWD_PREVIOUS_DIRECTORY="1;38;5;16"

# Last directory color in status line
# ANSI foreground code (e.g., 1;33 for yellow)
# Default: "1;33" (yellow)
export PWD_LAST_DIR="1;33"

# Directory separator color in status line
# ANSI foreground code (e.g., 1;96 for cyan)
# Default: "1;96" (cyan)
export PWD_BAR="1;96"

# File attributes command
# Command to display file attributes with 'x' key
# Default: "stat"
export PREVIEW_STAT_CMD="stat"

# Scroll behavior
# 0: No loop (stops at ends), 1: Loop (wraps around)
# Default: 1
export PREVIEW_LOOP_SCROLL=1

# Favorite directories (Bookmarks) (keys 0-9)
# Set paths for quick access with numeric keys
# Example: export PREVIEW_FAV_0=~/Documents
export PREVIEW_FAV_0=""
export PREVIEW_FAV_1=""
export PREVIEW_FAV_2=""
export PREVIEW_FAV_3=""
export PREVIEW_FAV_4=""
export PREVIEW_FAV_5=""
export PREVIEW_FAV_6=""
export PREVIEW_FAV_7=""
export PREVIEW_FAV_8=""
export PREVIEW_FAV_9=""

# Image preview tool
# 1: img2sixel, 2: viu, 3: catimg, 4: chafa
# Default: 1 (img2sixel)
export PREVIEW_IMG=1

# Markdown preview tool
# 1: glow, 2: bat, 3: mdless, 4: mdcat, 5: markdown_reader.sh
# Default: 5 (markdown_reader.sh)
export PREVIEW_MARKDOWN=5

# Image preview sizes (full-size)
# Width and height for img2sixel (pixels)
export PREVIEW_SIXEL_W=540
export PREVIEW_SIXEL_H=420
# Width and height for viu (characters)
export PREVIEW_VIU_W=90
export PREVIEW_VIU_H=35
# Width for catimg (characters)
export PREVIEW_CATIMG_W=100
# Size for chafa (characters)
export PREVIEW_CHAFA_S=50

# Image preview sizes (thumbnail)
# Width and height for img2sixel (pixels)
export PREVIEW_THUMB_SIXEL_W=300
export PREVIEW_THUMB_SIXEL_H=200
# Width and height for viu (characters)
export PREVIEW_THUMB_VIU_W=50
export PREVIEW_THUMB_VIU_H=16
# Width for catimg (characters)
export PREVIEW_THUMB_CATIMG_W=60
# Size for chafa (characters)
export PREVIEW_THUMB_CHAFA_S=25

# Text preview settings
# Maximum lines for file content preview
# Default: 30 (non-Android), 20 (Android)
export sizeline=30
# Maximum width for text preview (characters)
# Default: 200 (non-Android), 50 (Android)
export width=200
# Margin for text folding (characters)
# Default: 5
export PREVIEW_MARGIN=5

# Code highlighting settings
# Tab width for highlighting
# Default: 8
export HIGHLIGHT_TABWIDTH=8
# Highlight style
# Default: "pablo"
export HIGHLIGHT_STYLE="pablo"
# Additional highlight options
# Default: ""
export HIGHLIGHT_OPTIONS=""
# Pygmentize style
# Default: "autumn"
export PYGMENTIZE_STYLE="autumn"

# Video/Image resolution
# Resolution for resizing previews (WIDTHxHEIGHT)
# Default: "854x480"
export RESOLUTION="854x480"
```
### Dependencies
PREVIEW leverages various external tools for enhanced functionality. Install these as needed:

    img2sixel, viu, catimg, chafa (image previews)
    glow, bat, mdless, mdcat (markdown previews)
    7z, unzip, tar (archive handling)
    exiftool, mediainfo (file metadata)

### License
PREVIEW is licensed under the GPLv3. See the script header for details.

### Credits
Developed by Felipe Facundes.

### Contributing
Contributions are welcome! Feel free to submit a Pull Request. For significant changes, please open an issue first to discuss what you would like to change.
