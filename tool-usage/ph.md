# PhantomJS

## How to install PhantomJS on Ubuntu

First, install or update to the latest system software.

```text
sudo apt-get update
sudo apt-get install build-essential chrpath libssl-dev libxft-dev
```

Install these packages needed by PhantomJS to work correctly.

```text
sudo apt-get install libfreetype6 libfreetype6-dev
sudo apt-get install libfontconfig1 libfontconfig1-dev
```

Get it from the [PhantomJS website](http://phantomjs.org/).

```text
cd Downloads
wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2
export PHANTOM_JS="phantomjs-2.1.1-linux-x86_64"
sudo tar xvjf $PHANTOM_JS.tar.bz2
```

Once downloaded, move Phantomjs folder to `/usr/local/share/` and create a symlink:

```text
sudo mv $PHANTOM_JS /usr/local/share
sudo ln -sf /usr/local/share/$PHANTOM_JS/bin/phantomjs /usr/local/bin
```

**On Kali you might receive an OpenSSL error, quick fix to this is as follows:**

**Create an empty openssl.cnf file and set environment variable to use it.**

```text
touch /tmp/openssl.cnf 
```

```text
export OPENSSL_CONF="/tmp/openssl.cnf"
```

Now, It should have PhantomJS properly on your system.

```text
phantomjs --version
```

