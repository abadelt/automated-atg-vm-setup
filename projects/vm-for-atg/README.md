Description
===========
Use this to setup a VM for Commerce Reference Store, including all the basis (Oracle XE DB, Java, JBoss).

WARNING
=======


Requirements
============
- Installed VirtualBox (https://www.virtualbox.org/) - The build was done with version 4.2.8 
- Installed Vagrant (http://docs.vagrantup.com/v2/installation/index.html)
- Binaries for Java, Oracle Commerce, Oracle XE, and JBoss Server, plus a pre-build bento CentOS box 
  (see attributes/default.rb in each cookbook, and the Vagrantfile under projects/vm-for-atg, for the configuration of expected file locations)


Usage
=====

Follow the below instructions in order to able spin off a VM running CentOs (Guest OS) on it, running on the below Host OSes.

### Linux / MacOS

 1) Download least version of Virtualbox 4.3.xx (or higher) for your Host OS.

 2) Download least version of Vagrant 1.4.xx (or higher) for your Host OS.


 4) Install chef as vagrant's plugin by running the below command:

    sudo vagrant plugin install vagrant-chef-apply
    [sudo] password for xxxxxxx: 
    Installing the 'vagrant-chef-apply' plugin. This can take a few minutes...
    Installed the plugin 'vagrant-chef-apply (0.0.1)'!

 5) Check contents of the cookbooks folders and subfolders, both apt and openjdk-build should be populated with files.
    

 6) Bring up the box (first time) by running the below command, which should create and install necessary components:
    
    vagrant up	
    
   And you should see the below, give it some time (an hour or so)....
   
    ###################################################
    Bringing machine 'default' up with 'virtualbox' provider...
    .
    .
    .

    Running chef-solo...
    stdin: is not a tty
    [2014-01-06T21:28:54+00:00] INFO: *** Chef 11.4.0 ***

    [2014-01-06T23:05:45+00:00] INFO: Chef Run complete in 5810.238662085 seconds
    [2014-01-06T23:05:45+00:00] INFO: Running report handlers
    [2014-01-06T23:05:45+00:00] INFO: Report handlers complete
    [2014-01-06T23:05:45+00:00] DEBUG: Exiting
    ###################################################

 7) Now you can ssh to the VM by running:

    vagrant ssh

 8) Update the VM by running the below command:

    sudo apt-get update

 9) Shutdown the box using the below command (from the host):

    vagrant halt

10) To start all over again, destroy the box created and restart by starting vagrant again

    vagrant destroy
    vagrant up


Once the box is ready to use in future you can start up the VM with vagrant using:

``'vagrant up'``

In case a process has been abruptly terminated or wish to continuing a executing recipes on an active vagrant machine, do the below:

``'vagrant provision'``



Additional resources
====================
Ready to use vagrant boxes: http://www.vagrantbox.es/

License and Authors
-------------------
Authors: 
abadelt@web.de