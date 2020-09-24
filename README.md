## SSH into the server
SSH into the server running your HTTP website as a user with sudo privileges.

## Enable EPEL repo
You'll need to enable the EPEL (Extra Packages for Enterprise Linux) repository and make sure you follow all instructions for your system, including enabling any other recommended repositories that may be required.
Follow these instructions at the Fedora wiki to enable EPEL.

enable EPEL

## Install Certbot
Run this command on the command line on the machine to install Certbot.
```sh
sudo yum install certbot python2-certbot-apache
```
```sh
sudo yum install certbot python2-certbot-nginx
```
## Choose how you'd like to run Certbot
Either get and install your certificates...
Run this command to get a certificate and have Certbot edit your Apache configuration automatically to serve it, turning on HTTPS access in a single step.
```sh
sudo certbot --apache
```
```sh
sudo certbot --nginx
```
Or, just get a certificate
If you're feeling more conservative and would like to make the changes to your Apache configuration by hand, run this command.
```sh
sudo certbot certonly --apache
```
```sh
sudo certbot certonly --nginx
```
## Set up automatic renewal
We recommend running the following line, which will add a cron job to the default crontab.
```sh
echo "0 0,12 * * * root python -c 'import random; import time; time.sleep(random.random() * 3600)' && certbot renew -q" | sudo tee -a /etc/crontab > /dev/null
```
Confirm that Certbot worked
To confirm that your site is set up properly, visit https://yourwebsite.com/ in your browser and look for the lock icon in the URL bar.
