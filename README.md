# CyberEnvironment
This is a repo for various Cyber Security deployments

This is an environment build using Ansible, Vagrant, and VirtualBox to create an environment suitable for study and practice in various operating systems. In order to make use of this environment, some software will need to be installed on your computer. The computer you use for this should have at least 16Gb of RAM and a CPU that has at least 2 cores. You may be able to get away with a little less, however for the optimum experience it is recommended. This can be setup on hosts with a variety of operating systems.
# Environment Build Instructions
## macOS
_Gatekeeper will block virtualbox from installing. All you have to do is go into Security & Privacy of System Preferences and click Allow under the General tab and rerun installation._
##### Install all at once with the command below:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" && xcode-select --install &&brew install ansible ; brew install python ; brew cask install vagrant ; brew cask install VirtualBox ; brew cask install virtualbox-extension-pack ; vagrant plugin install vagrant-guest_ansible
```

##### Alternatively, you can install everything individually below.
- [Install the Latest Version of Vagrant](https://www.vagrantup.com/downloads.html) - (`brew cask install vagrant`)
    - Vagrant Plugin - `vagrant plugin install vagrant-guest_ansible`
- [Install the Latest Version of Virtualbox](https://www.virtualbox.org/wiki/Downloads) (`brew cask install VirtualBox`)
    - Virtual Box Extension Pack (`brew cask install virtualbox-extension-pack`)

##### Once the above software is installed. Do the following if you're running the environment on Mac:
1. Create a separate `~/bin` directory and `cd` to it.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Clone the environment repo to it with `git clone https://github.com/OpenCloudJedi/CyberEnvironment.git`
3. Change to the `Environment` directory that is now in your `~/bin` directory.
4. Run `vagrant up` to deploy the environment It will take the longest to deploy the first time only, this is because the system will have to download the images from vagrant on the first time this is run

## CentOS/RHEL - Install all at once by Copy/Pasting the below command into your terminal as root.
_NOTE - If it's been awhile since you've run yum update, do that first. Reboot if the kernel was updated. There may be some dependencies errors but don't be alarmed as this won't stop the environment from working._

_NOTE2 - If you receive an error for an ansible guest vagrant plugin, DO NOT worry, as there are two different plugins related to Ansible and only one needs to be installed._
##### For CentoOS/RHEL7 (Continue below for RHEL 8 specific script)
```
systemctl stop packagekit; yum install -y epel-release && yum install -y git binutils gcc make patch libgomp glibc-headers glibc-devel kernel-headers kernel-devel dkms libvirt libvirt-devel ruby-devel libxslt-devel libxml2-devel libguestfs-tools-c ; mkdir ~/Vagrant ; cd ~/Vagrant ; curl -o  vagrant_2.2.6_x86_64.rpm https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.rpm && yum install -y vagrant_2.2.6_x86_64.rpm && vagrant plugin install vagrant-guest_ansible ; vagrant plugin install vagrant-guest-ansible ; wget -O /etc/yum.repos.d/virtualbox.repo wget http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo ; yum install -y VirtualBox-6.0 && systemctl start packagekit
```
##### If you're using RHEL 8, use the script below:
```
systemctl stop packagekit; dnf -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm ; dnf install -y git binutils gcc make patch libgomp glibc-headers glibc-devel kernel-headers kernel-devel dkms libvirt libvirt-devel ruby-devel libxslt-devel libxml2-devel libguestfs-tools-c ; mkdir ~/Vagrant ; cd ~/Vagrant ; curl -o  vagrant_2.2.6_x86_64.rpm https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.rpm && dnf install -y vagrant_2.2.6_x86_64.rpm && vagrant plugin install vagrant-guest_ansible ; wget -O /etc/yum.repos.d/virtualbox.repo wget http://download.virtualbox.org/virtualbox/rpm/rhel/virtualbox.repo ; dnf install -y VirtualBox-6.0 && /usr/lib/virtualbox/vboxdrv.sh setup ; usermod -a -G vboxusers root ; systemctl start packagekit
```
##### Also, install the Virtualbox extension pack below
- [Install the Virtual Box Extension Pack](https://www.virtualbox.org/wiki/Downloads)

##### Once the above software is installed. Do the following if you're running the environment on Linux:
1. Create a separate `~/bin` directory and `cd` to it.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Clone the environment repo to it with `git clone https://github.com/OpenCloudJedi/CyberEnvironment.git`
3. Change to the `Environment` directory that is now in your `~/bin` directory.
4. Run `vagrant up` to deploy the environment It will take the longest to deploy the first time only, this is because the system will have to download the images from vagrant on the first time this is run

## Windows
- If using Windows:
- [Install the Latest Version of Vagrant](https://www.vagrantup.com/downloads.html)
- [Install the Latest Version of Virtualbox and Virtual Box Extension Pack](https://www.virtualbox.org/wiki/Downloads)
- Then install the following vagrant plugin via PowerShell as Administrator `vagrant plugin install vagrant-guest_ansible`


##### Once the above software is installed. Do the following if you're running the environment on Windows:
1. Create a separate `~/bin` directory and `cd` to it using the same PowerShell/Terminal as Administrator/Root.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Use your browser of choice and navigate to https://github.com/OpenCloudJedi/Environment, press the green “Clone or download” button then the “Download ZIP” button. Or use Github Desktop (See below).
3. Once downloaded, unzip the file and move it to the directory you created earlier, `~/bin` in the above example.
4. Use PowerShell/Terminal as Administrator/Root again and cd to the `~/bin/CyberEnvironment-main` directory then run `vagrant up` to deploy the environment. (It will take the longest to deploy the first time only, this is because the Vagrant system downloads the base image only the first time.


## Debian/Ubuntu
_NOTE - If it's been awhile since you've run apt update, do that first. Reboot if the kernel was updated._

##### Install all at once by Copy/Pasting the below command into your terminal as root.
```
sudo snap install ruby ; sudo apt install ruby-bundler git -y; wget -c https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.deb ; sudo dpkg -i vagrant_2.2.6_x86_64.deb ; wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add - ; wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add - ; sudo add-apt-repository "deb http://download.virtualbox.org/virtualbox/debian bionic contrib"; sudo apt update; sudo apt install -y virtualbox ; vagrant plugin install vagrant-guest_ansible
```
##### Also, install the Virtualbox extension pack below
- [Virtual Box Extension Pack](https://www.virtualbox.org/wiki/Downloads)

##### Once the above software is installed. Do the following if you're running the environment on Linux:
1. Create a separate `~/bin` directory and `cd` to it.  (The directory doesn't have to be ~/bin, it can be anything you want.)
2. Clone the environment repo to it with `git clone https://github.com/OpenCloudJedi/CyberEnvironment.git`
3. Change to the `Environment` directory that is now in your `~/bin` directory.
4. Run `vagrant up` to deploy the environment (If the environment has a designated repo VM it will take the longest to deploy the first time only, this is because the repo system has all the packages available to the base release but will be quicker on subsequent deployments.)

**Also, don't be spooked by any scary red font during the setup process. There are known issues that won't have a negative affect on the environment.**

_Now the deployment should be up and running!_

## (Recommended) Install Github Desktop to make pulling down changes easier
_NOTE this requires a free Github account_
1. Navigate to https://desktop.github.com/ and download Github Desktop.
2. Create or sign in to your account.
3. Click "Clone a repository from the Internet" and enter "OpenCloudJedi/CyberEnvironment" and choose a location then "Clone".
4. You are also able to easily pull changes when they're made available.

## Notable commands to control the environment:
- `vagrant up` - Boots and provisions the environment
- `vagrant destroy -f` - Shuts down and destroys all of the vms
- `vagrant destroy -f server1` - Shuts down and destroys only server1
- `vagrant destroy -f server2` - Shuts down and destroys only server2
- `vagrant up --provision` - Builds the servers that were destroyed and runs provisioning scripts again

If you want you can create a snapshot of your 2 machines that get reset and then restore that snapshot to quickly start over. This is significantly faster than a full reset.
1. First bring up the environment fully and make sure the provisioning script ran (The ansible part after all 3 machines boot up)
2. Make a snapshot of both vms
- `vagrant snapshot create server1 server1`
- `vagrant snapshot create server2 server2`
3. After completing study guide or in the case you broke them, try restoring the images back the vm's (make sure you are in the project directory before attempting this ie. ~/user/Environment )
- `vagrant snapshot restore server1 server1`
- `vagrant snapshot restore server2 server2`
