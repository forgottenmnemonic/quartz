---
tags:
  - linux
  - bash
  - functions
  - sysadmin
  - useful
aliases:
  - My Useful Linux Functions
  - Bash Functions
date: 2025-03-30
---
```bash
#!/bin/bash
# Jump to frequently used directories
jump() {
    case $1 in
        doc) cd ~/Documents ;;
        dl) cd ~/Downloads ;;
        s) cd ~/Scripts ;;
	      nc) cd ~/Nextcloud ;;
	      cfg) cd ~/.config ;;
        .b) cd ~/.bash ;;
        *) echo "Usage: jump {doc|dl|s|nc|cfg|.b}" ;;
    esac
}

# Find the largest files in a directory
largefiles() {
    find . -type f -exec du -h {} + | sort -rh | head -n ${1:-10}
}

# Easily compress a folder
compress() {
    tar -czvf "${1}.tar.gz" "$1"
}

# Extract archives
extract() {
    if [ -f "$1" ]; then
        case $1 in
            *.tar.bz2) tar xjf "$1" ;;
            *.tar.gz) tar xzf "$1" ;;
            *.tar.xz) tar xJf "$1" ;;
            *.bz2) bunzip2 "$1" ;;
            *.rar) unrar x "$1" ;;
            *.gz) gunzip "$1" ;;
            *.tar) tar xf "$1" ;;
            *.zip) unzip "$1" ;;
            *.7z) 7z x "$1" ;;
            *) echo "Cannot extract '$1': Unsupported format" ;;
        esac
    else
        echo "'$1' is not a valid file"
    fi
}

# Show disk usage of the current directory
duh() {
    du -sh "${1:-.}"/*
}

# Show local and public IP addresses
myip() {
    echo "Local IP: $(hostname -i | awk '{print $1}')"
    echo "Public IP: $(curl -s https://ipinfo.io/ip)"
}

# Search for a string in files recursively
search() {
    grep -rnw . -e "$1"
}

# Creates directory and cd into it
mcd() {
    if [ -z "$1" ]; then
        echo "Usage: mcd <directory-name>"
        return 1
    fi

    mkdir -p "$1" && cd "$1"
}

# Gives weather for indicated city - weather <city>
weather() {
    if [ -z "$1" ]; then
        echo "Usage: weather <city>"
        return 1
    fi
    curl -s "https://wttr.in/$1?format=3"
}

# Displays disk usage
diskfree() {
    df -h | grep -E '^Filesystem|/dev/'
}

# Backs up directory by zipping and labeling with date
backup_dir() {
    if [ -z "$1" ]; then
        echo "Usage: backup_dir <directory>"
        return 1
    fi
    tar -czvf "${1}_backup_$(date +%F).tar.gz" "$1"
}


# Add note to notes.txt <note here is my note>
note() {
    echo "$(date): $*" >> ~/.bash/notes.txt
    echo "Note saved."
}

# Define word - must be spelled correctly

define() {
    curl -s "https://api.dictionaryapi.dev/api/v2/entries/en/$1" | jq '.[0].meanings[0].definitions[0].definition' --raw-output
}

# Show system aliases and commands 

aliases() {
    if [ ! -f "$HOME/.bash/.bash_aliases" ]; then
        echo "Error: .bash_aliases file not found in your home directory."
        return 1
    fi

    echo "Available aliases in ~/.bash/.bash_aliases:"
    echo "--------------------------------------"

    # Extract and clean alias definitions, then sort them alphabetically
    awk '
    /^alias / {                                 # Match lines that start with "alias"
        gsub(/^alias /, "");                    # Remove "alias "
        gsub(/=/, " -> ");                      # Replace "=" with " -> " for clarity
        print $0                                # Print the cleaned line
    }
    ' "$HOME/.bash/.bash_aliases" | sort
}

# exit yazi with q to be in last explored directory, Q exits in original

function y() {
	local tmp="$(mktemp -t "yazi-cwd.XXXXXX")" cwd
	yazi "$@" --cwd-file="$tmp"
	if cwd="$(command cat -- "$tmp")" && [ -n "$cwd" ] && [ "$cwd" != "$PWD" ]; then
		builtin cd -- "$cwd"
	fi
	rm -f -- "$tmp"
}

# kills processes by name
kp () {
  ps aux | grep $1 > /dev/null
  mypid=$(pidof $1)
  if [ "$mypid" != "" ]; then
    kill -9 $(pidof $1)
    if [[ "$?" == "0" ]]; then
      echo "PID $mypid ($1) killed."
    fi
  else
    echo "None killed."
  fi
  return;
}

# displays all functions available
functions() {
    if [ ! -f "$HOME/.bash/.bash_functions" ]; then
        echo "Error: .bash_functions file not found in your home directory."
        return 1
    fi

    echo "Available functions in .bash_functions with descriptions:"

    # Use awk to extract function names and descriptions
    awk '
    BEGIN { 
        print "---------------------------------------------"; 
    }
    /^[[:space:]]*#[[:space:]]/ { description = $0 }  # Capture comments
    /^[[:space:]]*[a-zA-Z_][a-zA-Z0-9_]*[[:space:]]*\(\)[[:space:]]*{/ {  # Match function definitions
        gsub(/^[[:space:]]*#[[:space:]]*/, "", description);  # Remove the `#` from comments
        gsub(/^[[:space:]]+|[[:space:]]+$/, "", description); # Trim whitespace
        function_name = $1;                                   # Capture the function name
        gsub(/\(\)/, "", function_name);                      # Remove parentheses

        # Create dotted spacing
        dots = "";
        dot_count = 30 - length(function_name);
        for (i = 1; i <= dot_count; i++) dots = dots ".";

        printf "%-25s | %s\n", function_name dots, (description != "" ? description : "No description");
        description = "";                                     # Reset description
    }
    ' "$HOME/.bash/.bash_functions" | sort
}

# set wallpaper
wall() {
    gsettings set org.gnome.desktop.background picture-uri-dark "file:///home/john/Pictures/Wallpaper/$1"
}

# goes to year and month for journaling
med() {
    local dir=~/Documents/$(date +%Y/%m)
    mkdir -p "$dir"  # Create the directory if it doesn't exist
    cd "$dir" || return
}
```
