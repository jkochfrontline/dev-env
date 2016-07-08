# Description

Sets up a local dev env for ui development

# Prerequisites
 - VirtualBox
 - Vagrant
 - Ruby w/ Rake (Optional)

Optional
 - Ruby w/ Rake => This is optional to install all the various vagrant plugins that we rely on.  If you do not wish to install be sure to install all the required Vagrant plugins

# Usage
After install prerequisites, utilize the following commands to get started!

### Vagrant Setup
Optional Vagrant Plugins:
- vagrant-vbguest  
- vagrant-butcher
- vagrant-vbox-snapshot
- vagrant-share
- vagrant-cachier

#### Install Vagrant Dependencies
If you have Ruby w/ Rake you can run:
```
rake install:all			# installs all the vagrant plugins necessary
```

Otherwise, you will have to run the following command for each vagrant plugin listed within the Rakefile.
```
vagrant plugin install pluginName

```

#### Login to VM
To login to the box run the following:
```
vagrant builder up		# brings your builder box up 
vagrant builder ssh 	# login to your builder box, password is "vagrant"
```

**NOTE** - After logging into vagrant, all commands should be 
		run from within the vagrants home directory

# License and Author

- Author:: Jason Koch (<jkoch@frontlinetechnologies.com>)

- Copyright:: 2016
