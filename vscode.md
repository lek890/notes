### Install vscode using homebrew - so that path is added

brew cask install visual-studio-code

### vscode - selection

Copy content between tags including tag - emmet outward
Copy content between tags excluding tag - emmet inward

## Autocomplete in vscode zsh terminal

```
brew install zsh //for zsh
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.zsh/zsh-autosuggestions
# add the following in ~/.zshrc
# if there is no such file in the following directory, run make in that directory to get the following zsh file generated
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
# when opening the terminal, there could be folder permission issue asking for access everytime to fix that
run compaudit and it will give you a list of directories it thinks are unsecure
run sudo chown -R username:<group> target_directory
run sudo chmod -R 755 target_directory
for vscode: update the terminal in the settings with /bin/zsh
```
