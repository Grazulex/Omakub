#Ubuntu Development Installation

1.  Install fresh version of Ubuntu 24.04+ (I have only tested on 24.04)
2.  Get & Install Amakud:
```
get -qO- https://omakub.org/install | bash`
```

3. Install Composer:
```
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer
```

4. Add Path of composer bin in your .bashrc file:
```
nvim ~/.bashrc
```
add this line at the end of the file:
```
export PATH="$PATH:$HOME/.config/composer/vendor/bin"
```

5. Install Laravel installer:*
```
composer global require laravel/installer
```

6. Config Git config:
```
git config --global user.email "jms@grazulex.be"
git config --global user.name "Jean-Marc Strauven"
git config --global init.defaultBranch main
```

