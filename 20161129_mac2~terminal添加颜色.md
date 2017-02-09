**2016.11.29**

1. 修改.bash_profile
  ```vi ~/.bash_profile```
1. 增加颜色代码，最后是用了iterm的xterm-color
  ```
  #enables colorin the terminal bash shell export
  export CLICOLOR=1

  #sets up thecolor scheme for list export
  export LSCOLORS=gxfxcxdxbxegedabagacad

  #sets up theprompt color (currently a green similar to linux terminal)
  export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;36m\]\w\[\033[00m\]\$ '

  #enables colorfor iTerm
  export TERM=xterm-color
  ```

1. .bash_profile生效
  ```source ~/.bash_profile```