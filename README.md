# PREVIEW - A Bash File Manager with Preview Capabilities

**PREVIEW** is a lightweight, efficient file manager written in Bash, designed to provide seamless file navigation and preview functionalities in the terminal. Inspired by tools like `fff`, `lesspipe`, and `ranger`, it builds upon the `lf` foundation, enhancing file previews with customizable commands and configurable shortcuts. This script is part of the **[shell_utils](https://github.com/felipefacundes/shell_utils)** framework, one of the largest collections of scripts and utilities aimed at simplifying and enhancing user experience in the terminal.

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

### Usage
Once installed, simply run preview in your terminal to start the file manager. Use the default or customized key bindings to navigate directories, preview files, and perform operations. The script automatically generates a configuration file at ~/.config/preview/preview.conf on first run, which you can edit to tailor the experience to your needs.
Example Commands

    Start in the current directory: preview
    Start in a specific directory: preview /path/to/directory
    Show version: preview -v
    Show help: preview -h

### Configuration
The configuration file (preview.conf) is extensively documented within the script. It allows customization of:

    Preview mode (on/off)
    Maximum items displayed
    Hidden file visibility
    Colors for directories, status lines, and highlights
    Key bindings for all actions
    Preferred tools for file previews (e.g., markdown, images)

Edit ~/.config/preview/preview.conf to adjust these settings.
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
