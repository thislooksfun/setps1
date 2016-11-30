# setps1
An easy, native way to set the bash PS1 on the fly


## Setup
To install, simply add the 'setps1' file to any folder on your PATH (~/bin/ is recommended).   
**WARNING: If you stop here, you will have to run either* `source setps1` or `. setps1` (both are identical) every time. See item #1 in the [Advanced](#advanced-setup) section.**

## Commands
`setps1 --help` or `setps1 -h` (or mis-typing any other parameter) will display the help.  
`setps1 d` or `setps1 default` will set the PS1 back to whatever it was before `setps1` was run the first time in the current session.  
`setps1 b` or `setps1 basic` will set the PS1 to a basic prompt which displays just the name of the parent folder.
`setps1 v` or `setps1 verbose` will set the PS1 to a verbose output which displays the full filepath.  
`setps1 vm` or `setps1 verbose-multiline` will set the PS1 to a verbose output which displays the full filepath, and places the prompt on the next line. Useful for very long working directories.  
`setps1 f` or `setps1 fancy` will enable a fancy prompt which utilizes [powerline](http://powerline.readthedocs.io). If powerline is not installed, this defaults to the `verbose` prompt. **NOTE**: if using powerline on linux, or if it's just not working, read item #4 in the [Advanced](#advanced-setup) section.

## Advanced Setup
These are some more advanced options you can choose to (or not to) add

1. **(RECOMMENDED)** Stop typing `source`:  
   Simply add `alias setps1=". setps1"` to your `.bash_profile` file
1. Auto-run on startup:  
   Add the following to your `.bash_profile` file:
   
   ```bash
   if [ -f ~/bin/setps1 ]; then
      . ~/bin/setps1 verbose -tlf-set-ps1-shell-start-flag
   else
     # This part is optional, either set it to be whatever default prompt you want, or just remove it entirely
     export PS1="\w => "
   fi
   ```
1. Autocompletion:  
   1. Make sure you have bash autocompletion installed/enabled (on macOS you might have to run `brew install bash-completion`)
   2. Add the `completions/setps1` file to the bash completions folder. (With brew bash-completion, it's located at `$(brew --prefix)/etc/bash_completion.d/`)
1. Set powerline install location:
   If your powerline install is somewhere other than `~/Library/Python/2.7/lib/python/site-packages/powerline/bindings/bash/powerline.sh`, you will need to set the `POWERLINE_SHELL` variable before calling `setps1`. This can be done by adding the line `export POWERLINE_SHELL="[path to powerline.sh]"` in your `.bash_profile`. You only need to place it before trying to call `setps1 fancy`.
