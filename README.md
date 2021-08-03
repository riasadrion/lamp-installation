LAMP (Linux, Apache, MySQL, PHP) Installation Ubuntu 18.04 and 19.04
Download Chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb

Install VS Code
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt install code

Install Apache2
sudo apt install apache2

Install PHP
(We have to install lots of php packages to work with laravel composer and other stuff)
sudo add-apt-repository ppa:ondrej/php (It is to install latest php version)
sudo apt install php-common php-cli php-gd php-mysql php-curl php-intl php-mbstring php-bcmath php-imap php-xml php-zip

Install MySQL Server
sudo apt install mysql-server
sudo mysql-secure-connection
sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'admin';
Root password changed

Install Git & Composer
Sudo apt install git composer

Install phpmyadmin
sudo apt-get install -y phpmyadmin
Press space to add a star beside apache2 + tab + ok
Set password
systemctl reload apache2

Fast Virtual Host Setup
cd /usr/local/bin
sudo wget -O virtualhost https://raw.githubusercontent.com/RoverWire/virtualhost/master/virtualhost.sh
sudo chmod +x virtualhost
sudo wget -O virtualhost-nginx https://raw.githubusercontent.com/RoverWire/virtualhost/master/virtualhost-nginx.sh
chmod +x virtualhost-nginx
sudo virtualhost create mysite.dev my-directory
sudo virtualhost delete mysite.dev 


Manual Configure Virtual Hosts
sudo nano /etc/hosts
150
sudo nano /etc/apache2/sites-available/domain_name.conf

<VirtualHost *:80>
	ServerName domain.com
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/domain_path
</VirtualHost>

sudo a2ensite domain_name
sudo a2enmod rewrite
Edit /etc/apache2/apache2.conf
And AllowOverride All for /var/www/ directory
systemctl restart apache2
sudo chmod -R 777 /var/www
Then install laravel to its directory



Node JS Install (13.x)
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -
sudo apt install nodejs
npm install && npm run dev
npm run watch

Extra Tweaks
Chrome Color profile set to sRGB
chrome://flags/




var/www permissions
sudo chmod -R 777 /var/www






Ref:
https://www.youtube.com/watch?v=TrLAx27Npns
https://www.hostingadvice.com/how-to/install-phpmyadmin-on-ubuntu/
https://www.youtube.com/watch?v=CEghFZe7ALA
https://linuxize.com/post/how-to-install-laravel-on-ubuntu-18-04/

