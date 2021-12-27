---
description: A small wiki to kill an SSH port forwarding process running in the background.
---

# Kill SSH Port Forwarding

If you are using Linux you can kill the process by:

```text
ps aux | grep ssh
```

and then use

```text
kill <id>
```

To kill the process. If the kill command is not successful you can try

```text
kill -9 <id>
```



