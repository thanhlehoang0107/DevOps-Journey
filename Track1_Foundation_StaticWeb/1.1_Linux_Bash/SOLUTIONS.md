# Solutions - Linux & Bash

## Quiz Answers

1. C - pwd
2. A - Owner: rwx, Group: rx, Others: rx
3. B - mkdir -p

## Exercise 1 Solution

```bash
mkdir -p project/src project/docs project/tests
touch project/src/main.sh project/src/utils.sh
touch project/docs/README.md
touch project/tests/test.sh
```

## Exercise 2 Solution

```bash
chmod 740 deploy.sh
# 7 = rwx (owner)
# 4 = r (group)
# 0 = none (others)
```

## Project Solution

```bash
#!/bin/bash
# health_check.sh

echo "=== System Health Report ==="
echo "Date: $(date)"
echo "Hostname: $(hostname)"
echo ""

echo "=== Disk Usage ==="
df -h | grep -E '^/dev'
echo ""

echo "=== Memory Usage ==="
free -h
echo ""

echo "=== Top 5 CPU Processes ==="
ps aux --sort=-%cpu | head -6
```
