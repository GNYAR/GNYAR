## Node.js

- ### WSL
  [nodejs-on-wsl - Microsoft](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl)

  1. `sudo apt update && sudo apt upgrade`
  2. `sudo apt-get install curl`
  3. `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`
  4. `command -v nvm` (to verify installation. If the command failed, reopen the terminal and try again.)
  5. `nvm ls` to list versions of Node are currently installed
  6. `nvm install --lts`

## Git

- ### Set alias for commands
  Reference the file `.gitconfig`.
  Add the alias section to `~/.gitconfig`.

- ### Store the credential token
  Use the command below to store the credential.
  `git config --global credential.helper store`
  > Attention: This method saves the credentials in *plaintext* on your PC's disk. Everyone on your computer can access it, e.g. malicious NPM modules.

- ### Show the branch name in bash
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

- ### Installing Commitizen
  [commitizen/cz-cli - Github](https://github.com/commitizen/cz-cli)

  > Required: npm ([wsl](#nodejs))

  Install globally

  1. `npm install -g commitizen`
  2. `npm install -g cz-conventional-changelog`
  3. `echo '{ "path": "cz-conventional-changelog" }' > ~/.czrc`
