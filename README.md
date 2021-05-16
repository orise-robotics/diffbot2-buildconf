## Autoproj buildconf for diffbot2

## How to setup on a clean ubuntu environment:

### Acquire needed deps
```bash
sudo apt install ruby ruby-dev build-essential cmake git
```
### Get autoproj installer
```bash
wget https://raw.githubusercontent.com/rock-core/autoproj/master/bin/autoproj_install
```
To be able to use latest autoproj version it is good to use a custom gemfile. So create a file called `autoproj.gemfile`, and put the following contents
```ruby
source "https://rubygems.org"
gem "autoproj", github: 'rock-core/autoproj'
gem "autobuild", github: 'rock-core/autobuild'
```
Then, just execute

```bash
ruby autoproj_install --gemfile=autoproj.gemfile
```

### Set your configuration
To make life easier, this buildconf has preseted configurations located on `config.yml`, so on your workspace root folder, create a .autoproj file if does not exists and !(MUST BE DONE BEFORE BOOTSTRAP):

```bash
mkdir -p .autoproj
wget https://raw.githubusercontent.com/orise-robotics/diffbot2-buildconf/first-version/config.yml -O .autoproj/config.yml
```
### Run autoproj

Now just run autoproj
```bash
source env.bash
autoproj bootstrap git ${BUILDCONF GIT}
aup
amake
```

You should now have everything updated and running
