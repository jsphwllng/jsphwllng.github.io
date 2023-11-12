---
layout: default
title: useful NVIM addons and remaps
description: Remember to spend more time customising your NVIM environment than the time you save using NVIM
order: 17
---

Remember to spend more time customising your NVIM environment than the time you save using NVIM.

## Addons

### General
* [LaztVim](https://www.lazyvim.org/)
* nvim-cmp
* mason
* lualine
* telescope
* neotree
* nvim-autopairs
* barbar

### Git stuff
* vim-fugitive
* vim-rhubarb
* openingh

## Remaps

```sh
-- delete on 'd' instead of cut (we have x for cut)
vim.cmd([[nnoremap d "_d]])
vim.cmd([[vnoremap d "_d]])

-- reveal neotree on <leader>t
vim.keymap.set('n', '<leader>t', ':Neotree current reveal_force_cwd position=right toggle<CR>',
  { desc = '[T]oggle NeoTree' })

-- Tabs 
vim.keymap.set('n', '<leader><Left>', '<Cmd>BufferPrevious<CR>', { desc = 'Tab <-' })
vim.keymap.set('n', '<leader><Right>', '<Cmd>BufferNext<CR>', { desc = 'Tab ->' })
vim.keymap.set('n', '<leader><Down>', '<Cmd>BufferClose<CR>', { desc = 'Tab Close' })
```