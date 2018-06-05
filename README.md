# control_repo

Git:

For setting up Git in order to use with Puppet:
Made a new branch called 'production' and set it to default.
Next, delete the 'master' branch on git so that it will not interfere with Puppet's 'master' server.

Installing Puppet:
Use the commands : 
$ vagrant up              - to boot up CentOS 7
$ vagrant ssh             - to log into CentOS 7
$ sudo su -
$ rpm -Uvh https://yum.puppetlabs.com/puppet5/puppet5-release-el-7.noarch.rpm
$ yum install -y puppetserver
$ vim /etc/sysconfig/puppetserver 
          : Change the memory of JVM from 2G to 512m for both (min and max). (Done only since we are learning)

To start the server:
$ systemctl start puppetserver    

To enable it on bootup:
$ systemctl enable puppetserver

Add the master to this agent(self in this case) by:
$ vim /etc/puppetlabs/puppet/puppet.conf
Edit the last line as:

+ [agent]
+ server = master.puppet.vm               -(master.puppet.vm is the name of the VM on which the server is running)

Add necessary environment variables to the bash_profile by:

$ vim .bash_profile
+ PATH = $PATH:/opt/puppetlabs/puppet/bin:$HOME/bin

Make the changes immediate:
$ source .bash_profile

$ gem install r10k

$ puppet agent -t               - To check everything is running smmothly


