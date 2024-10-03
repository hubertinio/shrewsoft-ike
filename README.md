
### Installation 

Without GUI.

```
sudo apt install build-essential libssl-dev libedit-dev *qt5*dev cmake bison flex

cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=NO -DETCDIR=/etc -DNATT=YES .

make && sudo make install
```

#### Network Manager support (optional)

The script/linux/nm/ike-routes file is a script for network manager makes it automatically install routes when the tunnel goes up privates will go on the tunnel, publics will use normal home routing it should be copied into.

```
sudo cp script/linux/nm/ike-routes /etc/NetworkManager/dispatcher.d/
```


### Configuration 

Your sites settings. Modify to your needs.

```
mkdir -p ~/.ike/sites
cp -f sites/* ~/.ike/sites
```

### Usage 

__config__ - only filename from `~/.ike/sites`

```
#!/bin/bash

read -sp "Enter your password: " password
echo

sudo iked

ikec -r [config] -a -u [username] -p "$password" && send-notify "tunnel disabled"
```

