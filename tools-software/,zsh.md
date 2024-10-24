---
type: MT tool
alias: 
---
 
[[MT tool]]
[[LX linux MOC]]
[[IT macos]]

a better linux terminal than the default [[LX bash]]

````
sudo apt install zsh git fonts-font-awesome
````

install the oh my zsh add on 

````
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
````

some useful plug ins

auto suggestions:

````
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
````

syntax highlighting

````
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
````

powerlevel10K

```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

