# SSH Port

## RHEL, CentOS 8+, Rocky 8&9

```Bash
sudo vim /etc/ssh/sshd_config
#Port 22 -> Port UR_PORT

systemctl restart sshd
```

## Ubuntu

```Bash
sudo vim /etc/ssh/sshd_config
#Port 22 -> Port UR_PORT

sudo service ssh restart
```