Ravencore-deb
===========

Build DEB for coin
------------------
* Build requirements: make, docker.io
* Run "make" in coin subdirectory
* DEB file appear in coin subdirectory

First installation on target machine
------------------------------------
* ```apt-get install apt-transport-https && dpkg -i <package_name>```
* ```apt-get update && apt-get -f install```

Or you can use gdebi

* ```gdebi <package_name>```

Upgrade on target machine
-------------------------
* ```dpkg -i <package_name>```
* ```apt-get update && apt-get -f install```

Or use gdebi again

* ```gdebi <package_name>```

Updating ravencore version for coin
---------------------------------
* Change version in git checkout in rvn/ravencore-rvn/Makefile
* Create a new entry in rvn/ravencore-rvn/debian/changelog by using 'dch -i'
* Then build as usual
