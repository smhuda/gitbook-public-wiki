# Running a Service at Boot

Your `.service` file should look like this:

```text
[Unit]
Description=Spark service

[Service]
ExecStart=/path/to/spark/sbin/start-all.sh

[Install]
WantedBy=multi-user.target
```

Now, take a few more steps to enable and use the `.service` file:

1. Place it in `/etc/systemd/system` folder with say a name of `myfirst.service`
2. Make sure that your script executable with:

   ```text
   chmod u+x /path/to/spark/sbin/start-all.sh
   ```

3. Start it:

   ```text
   sudo systemctl start myfirst
   ```

4. Enable it to run at boot:

   ```text
   sudo systemctl enable myfirst
   ```

5. Stop it:

   ```text
   sudo systemctl stop myfirst
   ```

#### Notes

1. You don't need to launch Spark with `sudo` in your service, as the default service user is already root.
2. Look at the links below for more `systemd` options.

#### Moreover

Now what we have above is just rudimentary, here is a complete setup for spark:

```text
[Unit]
Description=Apache Spark Master and Slave Servers
After=network.target
After=systemd-user-sessions.service
After=network-online.target

[Service]
User=spark
Type=forking
ExecStart=/opt/spark-1.6.1-bin-hadoop2.6/sbin/start-all.sh
ExecStop=/opt/spark-1.6.1-bin-hadoop2.6/sbin/stop-all.sh
TimeoutSec=30
Restart=on-failure
RestartSec=30
StartLimitInterval=350
StartLimitBurst=10

[Install]
WantedBy=multi-user.target
```

To setup the service:

```text
sudo systemctl start spark.service
sudo systemctl stop spark.service
sudo systemctl enable spark.service
```

#### Further reading

Please read through the following links. Spark is a complex setup, so you should understand how it integrates with Ubuntu's init service.

* [https://datasciencenovice.wordpress.com/2016/11/30/spark-stand-alone-cluster-as-a-systemd-service-ubuntu-16-04centos-7/](https://datasciencenovice.wordpress.com/2016/11/30/spark-stand-alone-cluster-as-a-systemd-service-ubuntu-16-04centos-7/)
* [https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)
* [https://www.freedesktop.org/software/systemd/man/systemd.unit.html](https://www.freedesktop.org/software/systemd/man/systemd.unit.html)

