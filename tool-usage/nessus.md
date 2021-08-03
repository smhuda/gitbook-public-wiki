---
description: A small wiki about Nessus usage and associated plugins.
---

# Nessus

## Exporting Nessus plugins:

### How to export a list of all plugins available in a Nessus scanner

Exporting a list of all the plugins that exist in a Nessus scanner is done through the command line. The resulting XML file contains the plugin ID, title, description, and many other details. The resulting file may be quite large \(upwards of 1 GB\). NOTE: This will require direct access to the Nessus scanner's host. Before exporting the list of available plugins, make sure the scanner has a set of installed plugins. The machine in which you are exporting the plugins must have enough disk space available. If either of these conditions are not met, the system will not be able to export the plugins.

### Linux:

```text
# /opt/nessus/sbin/nessusd –X
```

Outputs to `/opt/nessus/lib/nessus/plugins/plugins.xml`

### Windows: \(from an administrator command prompt\)

```text
> C:\\Program Files\\Tenable\\Nessus\\nessusd -X
```

Replace the C:\ if Nessus is installed to a different drive. Outputs to `C:\ProgramData\Tenable\Nessus\nessus\plugins\plugins.xml`. This folder may be hidden by default on Windows so you may need to either need to navigate directly to it or show hidden folders\)

### Mac OS X:

```text
# /Library/Nessus/run/sbin/nessusd -X
```

Outputs to `/Library/Nessus/run/lib/nessus/plugins/plugins.xml`

### FreeBSD:

```text
# /usr/local/nessus/sbin/nessusd -X
```

Outputs to `/usr/local/nessus/lib/nessus/plugins/plugins.xml`

## Nessus Service Start and Stop

#### Windows

```text
C:\\Windows\\system32>net start "Tenable Nessus"
C:\\Windows\\system32>net stop "Tenable Nessus"
```

#### Linux

```text
sudo /etc/init.d/nessusd start
<https://127.0.0.1:8834/> or localhost:8834
```

