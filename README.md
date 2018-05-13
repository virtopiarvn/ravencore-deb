Ravencore-deb
===========
Packaging system to deploy Ravencoin Block Explorer
**The current configuration of this repository creates deb packages suited to run on ubuntu, behind Cloudflare(snakeoil ssl only), and are customized for the domain https://ravencoin.network**

Using the build environment 
------------------
````
$sudo apt-get update
$sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
$curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
$sudo apt-get update
$sudo apt-get install -y docker-ce git make
$git clone https://github.com/underdarkskies/ravencore-deb
$cd ravencore-deb/rvn
$sudo make
````
DEB file will appear in ravencore-deb/rvn/

Deploying a Ravencore Deb file
------------------------------------
Download your deb to the home directory of your ubuntu instance
````
$wget https://github.com/underdarkskies/ravencore-deb/releases/download/<tag>/ravencore_<version>_amd64.deb
$sudo apt-get install -y apt-transport-https curl && sudo dpkg -i ravencore_4.7.3_amd64.deb
$sudo apt-get update && sudo apt-get -f install -y
$cd /etc/nginx/sites-enabled
$sudo ln -s ../sites-available/nginx-ravencore .
$sudo rm default
$sudo rm ../sites-available/default
````
at this point the ravencore service and nginx will automatically launch and run even after reboot

Optional: add a redirect from www.example.com to example.com
----
````$sudo nano /etc/nginx/conf.d/redirect.conf````
and edit the file with:
````
server {
    server_name www.example.com;
    return 301 $scheme://example.com$request_uri;
}
````
Restart NGINX
````
$sudo printf "[Service]\nExecStartPost=/bin/sleep 0.1\n" | sudo tee /etc/systemd/system/nginx.service.d/override.conf
$sudo systemctl daemon-reload
$sudo service nginx restart
````

Helpful commands to manage your Deb based install:
----
````
$sudo service ravencore start
$sudo service ravencore stop
$sudo service ravencore restart
$sudo service ravencore status

$sudo service nginx start
$sudo service nginx stop
$sudo service nginx restart
$sudo service nginx status
````
Undeploying a Ravencore Deb file
----
````
$sudo apt-get install -y aptitude
$sudo aptitude purge ravencore
````
Updating Ravencore version
---------------------------------
* Change version in git checkout in rvn/ravencore/Makefile
* Create a new entry in rvn/ravencore/debian/changelog by using 'dch -i'
* Then build as usual
