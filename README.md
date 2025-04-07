# Ubuntu Development Installation

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

7. Create a SSH key
```
ssh-keygen -t ed25519 -C "jms@grazulex.be"
```
and copy this in your GitHub Account

8. Active Intelephense in VIM Options. 
```
cd ~/.config/nvim/lua/config
```
add this line in the options.lua file:
```
vim.g.lazyvim_php_lsp = "intelephense"
```

9.  Disable Phpactor in Vim:
```
Space+c+m
Choice Phpaction + Enter + C (capital)
```

10.  Active Pint.
Create a PHP config file :
```
touch ~/.config/nvim/lua/plugins/php.lua
```
With this content :
```
return {
  {
    -- Set Laravel Pint as the default PHP formatter with PHP CS Fixer as a fall back.
    "stevearc/conform.nvim",
    optional = true,
    opts = {
      formatters_by_ft = {
        php = { "pint", "php_cs_fixer" },
      },
    },
  },
  {
    -- Remove phpcs linter.
    "mfussenegger/nvim-lint",
    optional = true,
    opts = {
      linters_by_ft = {
        php = {},
      },
    },
  },
  {
    -- Add neotest-pest plugin for running PHP tests.
    -- A package is also available for PHPUnit if needed.
    "nvim-neotest/neotest",
    dependencies = { "V13Axel/neotest-pest" },
    opts = { adapters = { "neotest-pest" } },
  },
}
```

11.  From now, when you save a file, Pint will clean your file.
In a test file, you can run the test via the command:
```
Space + t + (choice your option)
```
