# OpenVAS installation from sources for Ubuntu 25 systems.

<br>
<br>
<br>

# Usage

## Download the script and make it executable.
```
mkdir openvas
cd openvas
wget https://raw.githubusercontent.com/FeralDucka/OpenVAS-Installation/master/openvas_install.sh
chmod +x openvas_install.sh
sudo ./openvas_install.sh
```

<br>

## Check Services status.

```
sudo systemctl status notus-scanner
sudo systemctl status ospd-openvas
sudo systemctl status gvmd
sudo systemctl status gsad
```

<br>

## Login.

*Make sure the TCP port 9392 is open on your firewall.*<br>
Open your browser and login to the Greenbone Security Assistant.
```
http://<server_ip>:9392
```
<br>
<br>
<br>

# Documentation

```
https://greenbone.github.io/docs/latest/22.4/source-build/
```

<br>
<br>
<br>

# Troubleshooting

Update the Openvas feeds:
```
/usr/local/bin/greenbone-feed-sync
```

<br>

Create a user:
```
/usr/local/sbin/gvmd --create-user=<username>
```

Reset a user password:
```
/usr/local/sbin/gvmd --user=<username> --new-password=<password>
```

<br>

Setting the Feed Import Owner:
```
/usr/local/sbin/gvmd --modify-setting 78eceaec-3385-11ea-b237-28d24461215b --value `/usr/local/sbin/gvmd --get-users --verbose | grep admin | awk '{print $2}'`
```
