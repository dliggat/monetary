## Monetary

Documentation goes here.

### Setup (OSX)

* Clone the repo: `git clone https://github.com/dliggat/monetary.git`
  * Install ruby `2.1.2`: `rbenv install 2.1.2`
  * Install bundler: `gem install bundler`
* Install gems: `bundle install`
* Install Bower assets: `bower install` (install `npm` and `bower` first if necessary)

### Setup (Ubuntu 14.04 VirtualBox guest)

#### VM configuration
* Set networking to `bridged`
* Configure a shared folder for git directory
  * call it `git`
  * set `automount`
  * set `permanent`
  * once vm boots, you will see it mounted as `/media/sf_git`
  * add user to vboxsf group: `sudo adduser $USER vboxsf`
  * make a handy symbolic link: `ln -s /media/sf_git ~/git`

#### Install initial dependencies

    sudo apt-get update
    sudo apt-get install git vim libssl-dev g++ libsqlite3-dev libreadline-dev

#### Setup rbenv/ruby
* `DO NOT` install ruby or rbenv with apt-get
* clone repos:

        git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
        git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

* add stuff to `~/.bashrc`:

        echo '' >> ~/.bashrc;
        echo '' >> ~/.bashrc;
        echo '# rbenv crap' >> ~/.bashrc;
        echo 'export PATH="$PATH:$HOME/.rbenv/bin"' >> ~/.bashrc;
        echo 'eval "$(rbenv init -)"' >> ~/.bashrc;
        exec bash

* update repos (not needed if just cloned):

        cd ~/.rbenv
        git pull
        cd plugins/ruby-build
        git pull
        cd plugins/* # (whatever else is there)
        git pull

* install ruby

        rbenv install 2.1.2
        rbenv global 2.1.2

#### Install ruby gems
* update gems: `gem update --system`
* install bundler: `gem install bundler`
* install packaged gems (from `~/git/monetary`): `bundle install`

#### Install nvm
* clone repo: `git clone git://github.com/creationix/nvm.git ~/.nvm`
* add stuff to `~/.bashrc`:

        echo '' >> ~/.bashrc
        echo '' >> ~/.bashrc
        echo '# nvm crap' >> ~/.bashrc
        echo '. $HOME/.nvm/nvm.sh' >> ~/.bashrc
        exec bash

#### Install node/bower and front end packages
* install node: `nvm install 0.10.35`
* add stuff to `~/.bashrc`:

        echo '' >> ~/.bashrc
        echo '' >> ~/.bashrc
        echo '# node crap' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.nvm/v0.10.35/bin' >> ~/.bashrc

* install bower: `npm install -g bower`
* install front end packages (from `~/git/monetary`): `bower install`


### Running
* Run the unit tests: `bundle exec rspec -b -c spec/`
* Launch the app: `bundle exec rails server`
