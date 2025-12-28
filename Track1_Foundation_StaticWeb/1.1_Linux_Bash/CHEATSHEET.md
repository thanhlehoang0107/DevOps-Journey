# Linux & Bash - Cheatsheet

## File System Navigation

```bash
pwd                 # Print working directory
ls                  # List files
ls -la              # List all files with details
cd /path            # Change directory
cd ..               # Go up one level
cd ~                # Go to home directory
```

## File Operations

```bash
touch file.txt      # Create empty file
mkdir dir           # Create directory
mkdir -p a/b/c      # Create nested directories
cp src dst          # Copy file
mv src dst          # Move/rename file
rm file             # Delete file
rm -rf dir          # Delete directory recursively
```

## File Viewing

```bash
cat file            # View entire file
less file           # View with pagination
head -n 10 file     # View first 10 lines
tail -n 10 file     # View last 10 lines
tail -f file        # Follow file changes
```

## Permissions

```bash
chmod 755 file      # rwxr-xr-x
chmod +x file       # Add execute permission
chown user:group file  # Change owner
```

## Process Management

```bash
ps aux              # List all processes
top                 # Interactive process viewer
kill PID            # Kill process by ID
kill -9 PID         # Force kill
```

## Bash Scripting

```bash
#!/bin/bash
# Variables
NAME="DevOps"
echo "Hello $NAME"

# Conditionals
if [ -f file.txt ]; then
    echo "File exists"
fi

# Loops
for i in 1 2 3; do
    echo $i
done
```
