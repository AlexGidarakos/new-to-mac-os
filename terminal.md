# Terminal enhancements
## iTerm2
You really want to stop using macOS's built-in Terminal app and start using the free iTerm2 utility as it's infinitely more customisable.

Install it with:

```shell
# Install from command line using Homebrew
brew install --cask iterm2
```

## ohmyzsh

In recent versions of macOS, the default shell changed from Bash to zsh. There is an amazing project that aims to supercharge your zsh experience with all sorts of customisations and plugins, from fancy prompts to Git-specific aliases and autocompletion rules to adding key bindings for the Home and End keys when using an external PC keyboard.

Visit the project's GitHub repo

<https://github.com/ohmyzsh/ohmyzsh>

and follow the instructions to install. There is no need for lengthy initial customisations; just by keeping the default options, your zsh experience will be markedly improved. But these are some plugins that you'll probably want to add immediately in **`~/.zshrc`**:

```shell
# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git terraform aws azure docker)
```

These give you custom prompts, aliases, helper functions  and Tab autocompletion functionality for the commands and subcommands of the respective CLI clients/binaries.