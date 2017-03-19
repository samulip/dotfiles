# dotfiles

My preferred settings
- Vim
- i3wm
- Dark colors from Solarize, ref ...
- Source Code Pro font from Adobe, ref ..
- Bash

# Usage

This all from [Nicola Paolucci / Atlassian](https://developer.atlassian.com/blog/2016/02/best-way-to-store-dotfiles-git-bare-repo/) 
```sh

git clone --bare https://github.com/samulip/dotfiles.git $HOME/.cfg
function config {
  /usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME $@
}
mkdir -p .cfg-backup
config checkout
if [ $? = 0 ]; then
  echo "Checked out config.";
  else
    echo "Backing up pre-existing dot files";
    config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | xargs -I{} mv {} .cfg-backup/{}
fi;
config checkout
config config status.showUntrackedFiles no
    
```
