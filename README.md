# graft-git.nvim

![tests](https://github.com/tlj/graft-git.nvim/actions/workflows/tests.yml/badge.svg)
![typecheck](https://github.com/tlj/graft-git.nvim/actions/workflows/typecheck.yml/badge.svg)

An extension to [graft.nvim](https://github.com/tlj/graft.nvim) to handle automatic installation, removal and updates of plugins through git submodules.

## Installation

See [graft.nvim](https://github.com/tlj/graft.nvim) for a simple `init.lua` method which can be used to ensure 
both `graft.nvim` and other extensions like `graft-git.nvim` are automatically installed.

Or you can follow the manual installation method below.

Add graft-git.nvim as a git submodule in your Neovim configuration:

```bash
:execute '!git -C ' .. stdpath('config') .. ' submodule add https://github.com/tlj/graft-git.nvim pack/graft/start/graft-git.nvim'
```

## Usage

Basic setup in your init.lua. This will automatically install all plugins defined by graft.nvim setup,
and remove any plugins which are installed whithout being defined.

```lua
-- Use graft tools to automatically 
require("graft-git").setup({ install_plugins = true, remove_plugins = true })

-- The defined plugin will be automatically added as a submodule by graft-git.nvim
require("graft").setup({ 
  now = {
    "catppuccin/nvim", 
    { name = "catppuccin", setup = function() vim.cmd("colorscheme catppuccin-mocha") end } }
  },
})
```

## Healthcheck

In the Neovim cmdline run:

```lua
checkhealth graft-git
```
