Ravencore-deb
===========

Build DEB for coin
------------------
* Build requirements: make, docker.io
* Run "make" in coin subdirectory
* DEB file appear in coin subdirectory

First installation on target machine
------------------------------------
* ```sudo apt-get install -y apt-transport-https curl &&  sudo dpkg -i <package_name>```
* ```sudo apt-get update && sudo apt-get -f install```

Or you can use gdebi

* ```sudo gdebi <package_name>```

Upgrade on target machine
-------------------------
* ```sudo dpkg -i <package_name>```
* ```sudo apt-get update && sudo apt-get -f install```

Or use gdebi again

* ```sudo gdebi <package_name>```

Updating ravencore version
---------------------------------
* Change version in git checkout in rvn/ravencore/Makefile
* Create a new entry in rvn/ravencore/debian/changelog by using 'dch -i'
* Then build as usual
