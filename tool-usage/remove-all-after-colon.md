---
description: >-
  This one-liner uses the cut command to removing everything on a line after the
  occurrence of a colon.
---

# Remove All After Colon

This one-liner uses the cut command to removing everything on a line after occurence of a colon. A similar command can be used for another use case of another character, alphabet or numeric character.

```text
cut -f1 -d ":" file.txt > newfile.txt
```

