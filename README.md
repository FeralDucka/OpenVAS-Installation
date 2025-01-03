# OpenVAS installation from sources for Ubuntu 24 systems.

A simple bash script that installs OpenVAS from sources on Debian 12.

# Usage

### System Update

Prior beginning the installation, make sure the system is fully updated.

```
sudo apt update
```
```
sudo apt-get dist-upgrade
```

### ⚙ Step #1: Login as root.

```
sudo su
```

### ⚙ Step #2: Download the script and make it executable.

```
wget https://raw.githubusercontent.com/FeralDucka/OpenVAS-Installation/master/openvas_install.sh
```
```
chmod +x openvas_install.sh
```

### ⚙ Step #3: Execute the script.

```
./openvas_install.sh
```

### ⚙ Step #4: The admin password.

Grab the admin password right after the "Creating the admin user." message.

### ⚙ Step #5: Service status.

Verify the services are running without errors.
```
sudo systemctl status notus-scanner
sudo systemctl status ospd-openvas
sudo systemctl status gvmd
sudo systemctl status gsad
```

### ⚙ Step #6: Login.

Open your browser and login to the Greenbone Security Assistant.
```
http://<server_ip>:9392
```
*Make sure the TCP port 9392 is open on your firewall.*

# Documentation

```
https://greenbone.github.io/docs/latest/22.4/source-build/
```

# Troubleshooting

Update the Openvas feeds:
```
/usr/local/bin/greenbone-feed-sync
```

Create a user:
```
/usr/local/sbin/gvmd --create-user=<username>
```

Reset a user password:
```
/usr/local/sbin/gvmd --user=<username> --new-password=<password>
```

Setting the Feed Import Owner:
```
/usr/local/sbin/gvmd --modify-setting 78eceaec-3385-11ea-b237-28d24461215b --value `/usr/local/sbin/gvmd --get-users --verbose | grep admin | awk '{print $2}'`
```

# License

This repository is licensed under the Apache License 2.0 license.

# Disclaimer

The contents in this repository provided AS IS with absolutely NO warranty. KASTERVO LTD is not responsible and without any limitation, for any errors, omissions, losses or damages arising from the use of this repository.
