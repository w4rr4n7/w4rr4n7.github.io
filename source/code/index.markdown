---
layout: page
title: "code"
comments: true
sharing: true
footer: true
---

Crunch Bang 11 Post Post Install Script
============

Crunchbang Comes with its own script to update && upgrade, install Libre, printers, etc. This is what I usually run after that. Right now, don't expect this to work at all. In the future I hope to get everything automated from stock to work ready. Installing dependencies and the various programs I like is easy. Node and Ruby is another story but right now c/p the commands manually is good enough.

I believe this is also what I use on Ubuntu 14.04 but I don't remember if this is what I did on my desktop.
### Dependencies ###
```
	# Update
	$ sudo apt-get update && sudo apt-get upgrade
	# Basics plus Node dependencies
	$ sudo apt-get install vlc gimp inkscape gparted curl build-essential openssl libssl-dev git python
```

### Node ###
```
	# NVM
	$ git clone git://github.com/creationix/nvm.git ~/.nvm
	$ printf "\n\n# NVM\nif [ -s ~/.nvm/nvm.sh ]; then\n\tNVM_DIR=~/.nvm\n\tsource ~/.nvm/nvm.sh\nfi" >> ~/.bashrc
	$ NVM_DIR=~/.nvm
	$ source ~/.nvm/nvm.sh
	# install node
	$ nvm install v0.10.28
	$ nvm alias default 0.10
	$ nvm use 0.10
	# update
	$ npm install -g npm
```

### Stuff that needs Node while we are here ###
```
	# bower, grunt, yo, bootstrap
	$ npm install -g yo
	$ mkdir dev
	$ cd dev
	$ bower install bootstrap
```
### Ruby ###
I have the least confidence in this part. I used to use RVM. On a whim I tried out rbenv. Now, I aint some fancy pants rubydev that needs to manage multiple Ruby environments but I've found that manually initiating ruby locally within the project's directory to be a more elegant method.

I had some issues with getting terminator to play nice with both NPM and Ruby. I think what I have below works, but I'm not entirely sure. Your mileage may vary.
```
	# ruby via rbenv
	$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
	$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
	# ruby-build so you can rbenv install
	$ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
	# install ruby version 2.1.2 (can be other versions)
	$ rbenv install 2.1.2
	$ rbend rehash
	# enable command line
	$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
	$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
```