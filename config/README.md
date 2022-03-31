## Git

### Set alias for commands
Reference the file `.gitconfig`.
Add the alias section to `~/.gitconfig`.

### Store the credential token
Use the command below to store the credential.
`git config --global credential.helper store`
> Attention: This method saves the credentials in *plaintext* on your PC's disk. Everyone on your computer can access it, e.g. malicious NPM modules.

### Show the branch name in bash
Reference the file `.bashrc`.
Replace the part `"$color_prompt" = yes`
```
show_git_branch() {
   git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}
if [ "$color_prompt" = yes ]; then
    PS1="${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\] \[\033[31m\]\$(show_git_branch)\[\033[00m\]$ "
else
    PS1="${debian_chroot:+($debian_chroot)}\u@\h:\w \$(show_git_branch)\$ "
fi
```

> Remember to uncomment `ls` aliases in `.bashrc`.
