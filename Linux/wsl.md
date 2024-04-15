# install standard
wsl --install

# install after error
wsl --update --web-download
wsl --install --web-download -d Ubuntu

## when no internet connection
### /etc/wsl.conf should look like
[user]
default=user1

[network]
generateResolvConf = false

### /etc/resolv.conf should look like
nameserver 10.100.40.1
nameserver 10.100.40.2
nameserver 10.100.40.3
nameserver 10.100.40.4
