# Network Connectivity Cron

This script checks if the network manager is running or if there is network connectivity, if not it restarts network manager. Great for cronjobs to check every 2 minutes to ensure remotely managed machines always stay online.

Copy the following script in the a new file, in this case I'm calling it check\_network. Place it at the following location:

`/usr/local/bin/check_network`

```text
#!/bin/bash

if ping 8.8.8.8 ; then
	:
else
	service network-manager restart
fi
```

Add the following line to `/etc/crontab`. Change the `*/2` to whatever increment you want to have this script run in minutes. It's currently set to run `/usr/local/bin/check_network` every two minutes.

```text
*/2 * * * * root /usr/local/bin/check_network
```

Set the execute permissions on the script. As root, type: 

```text
chmod +x /usr/local/bin/check_network
```

To ensure the cronjob is running or not. Running the “systemctl” command along with the status flag will check the status of the Cron service as shown in the image below. If the status is “Active \(Running\)” then it will be confirmed that crontab is working perfectly well, otherwise not.

```text
$ systemctl status cron
```

To edit or add/remove cron jobs:

```text
$ crontab –e
```

