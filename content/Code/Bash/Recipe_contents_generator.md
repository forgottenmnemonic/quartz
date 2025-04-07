---
tags:
  - linux
  - bash
  - recipe
  - one-liner
aliases:
  - Create a Recipe Contents
  - One Liner Recipe Index
date: 2025-03-29
---

```

for file in *.md; do 
  [[ "$file" == "recipes.md" ]] && continue
  title=$(grep -i '^title:' "$file" | cut -d':' -f2- | tr -d '"')
  [[ -n "$title" ]] && echo "[[$file | $title]]" >> recipes.md
done
```