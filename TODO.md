
# Random notes / commands used to set up new systems

## TODO: Convert to Ansible

### Install rbenv and ruby-build

	apt-get -y install git autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev

	adduser app --disabled-password --gecos ''

	su - app
	git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
	git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
	echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
	echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
	source ~/.bash_profile
	rbenv install 2.1.2
	rbenv local 2.1.2
	gem install bundler
	rbenv rehash
	exit

### Install passenger

https://www.phusionpassenger.com/documentation/Users%20guide%20Nginx.html#install_on_debian_ubuntu

    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 561F9B9CAC40B2F7
    apt-get install apt-transport-https ca-certificates
    echo 'deb https://oss-binaries.phusionpassenger.com/apt/passenger trusty main' > /etc/apt/sources.list.d/passenger.list
    chown root: /etc/apt/sources.list.d/passenger.list
    chmod 600 /etc/apt/sources.list.d/passenger.list
    apt-get update
    apt-get -y install nginx-extras passenger

Then uncomment out lines in passenger nginx config file to enable passenger

### ghost

    unzip -d ghost
    apt-get install nodejs, nodejs-legacy, npm

    npm install --production

Change forceAdminSSL: true in ghost config file

### Set timezone to brisbane

    sudo dpkg-reconfigure tzdata

    echo "Australia/Adelaide" | sudo tee /etc/timezone
    sudo dpkg-reconfigure --frontend noninteractive tzdata

### Install Uncomplicated Firewall

	sudo apt-get install ufw
	sudo ufw default deny incoming
	sudo ufw default allow outgoing

	sudo ufw allow ssh
	sudo ufw allow http
	sudo ufw allow https

	sudo ufw limit ssh/tcp

## DONE: Converted to Ansible

### Secure SSH

Edit /etc/ssh/sshd_config -> 
PermitRootLogin no
PasswordAuthentication no

### Run updates
	apt-get update
	apt-get upgrade -y

### Install fail2ban
	sudo apt-get install fail2ban
	sudo service fail2ban restart




