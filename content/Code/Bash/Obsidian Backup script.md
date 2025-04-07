```bash
#!/bin/bash

# Define paths
BACKUP_DIR="$HOME/obsidian_backups"
SOURCE_DIR="/mnt/c/Users/john/Nectcloud/ObsidianVault"  # Update if needed

# Create backup directory if it doesn't exist
mkdir -p "$BACKUP_DIR"

# Generate timestamped filename
DATE=$(date +"%Y-%m-%d")
BACKUP_FILE="$BACKUP_DIR/${DATE}_obsidian_backup.zip"

# Create the ZIP archive
zip -r "$BACKUP_FILE" "$SOURCE_DIR"

# Keep only the last 7 backups
find "$BACKUP_DIR" -type f -name "*_obsidian_backup.zip" -mtime +7 -delete

echo "Backup completed: $BACKUP_FILE"
```