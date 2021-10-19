#Odoo Install Script
This script is based on the install script from André Schenkels (https://github.com/aschenkels-ictstudio/openerp-install-scripts) but goes a bit further and has been improved. This script will also give you the ability to define an xmlrpc_port in the .conf file that is generated under /etc/ This script can be safely used in a multi-odoo code base server because the default Odoo port is changed BEFORE the Odoo is started.

#Installing Nginx
If you set the parameter INSTALL_NGINX to True you should also configure workers. Without workers you will probably get connection loss issues. Look at the deployment guide from Odoo on how to configure workers.

#Installation procedure
1. Download the script:
```sh
sudo wget https://raw.githubusercontent.com/Yenthe666/InstallScript/15.0/odoo_install.sh
```
#2. Modify the parameters as you wish.
There are a few things you can configure, this is the most used list:
OE_USER will be the username for the system user.
GENERATE_RANDOM_PASSWORD if this is set to True the script will generate a random password, if set to Falsewe'll set the password that is configured in OE_SUPERADMIN. By default the value is True and the script will generate a random and secure password.
INSTALL_WKHTMLTOPDF set to False if you do not want to install Wkhtmltopdf, if you want to install it you should set it to True.
OE_PORT is the port where Odoo should run on, for example 8069.
OE_VERSION is the Odoo version to install, for example 15.0 for Odoo V15.
IS_ENTERPRISE will install the Enterprise version on top of 15.0 if you set it to True, set it to False if you want the community version of Odoo 15.
OE_SUPERADMIN is the master password for this Odoo installation.
INSTALL_NGINX is set to False by default. Set this to True if you want to install Nginx.
WEBSITE_NAME Set the website name here for nginx configuration
ENABLE_SSL Set this to True to install certbot and configure nginx with https using a free Let's Encrypted certificate
ADMIN_EMAIL Email is needed to register for Let's Encrypt registration. Replace the default placeholder with an email of your organisation.
INSTALL_NGINX and ENABLE_SSL must be set to True and the placeholder in ADMIN_EMAIL must be replaced with a valid email address for certbot installation
By enabling SSL though Let's Encrypt you agree to the following policies

#3. Make the script executable
```sh
sudo chmod +x odoo_install.sh
```
#4. Execute the script:
```sh
sudo ./odoo_install.sh
```
