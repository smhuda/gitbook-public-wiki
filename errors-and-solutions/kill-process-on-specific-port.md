---
description: Killing a background process running on a specific port
---

# Kill Process On Specific Port

### To list any process listening to the port 8080:

```text
lsof -i:8080
```

### To kill any process listening to the port 8080:

```text
kill $(lsof -t -i:8080)
```

### or more violently:

```text
kill -9 $(lsof -t -i:8080)
```

