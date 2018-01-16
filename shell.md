# Shell(셸) 설정

## 기본 셸을 zsh로 변경

### zsh

<http://theyearlyprophet.com/love-your-terminal.html>  
bash와 비슷하게 동작하는 셸로, 사용성이 좋다.

#### 설치

**Ubuntu**

```
sudo apt-get install zsh
curl -L http://install.ohmyz.sh | sh
chsh -s `which zsh`
```

**macOS**

```
brew install zsh zsh-completions zsh-syntax-highlighting zsh-autosuggestions
curl -L http://install.ohmyz.sh | sh
```

> **확인법**  
> echo $SHELL

**필수적으로 추가되어야 할 부분**

**Ubuntu**

```
# pyenv
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

**macOS**

```
# pyenv
export PYENV_ROOT=/usr/local/var/pyenv
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi

# zsh-autosuggestions
source /usr/local/share/zsh-autosuggestions/zsh-autosuggestions.zsh

# zsh-completions
fpath=(/usr/local/share/zsh-completions $fpath)
autoload -Uz compinit && compinit -i

# zsh-syntax-highlighting
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```


## 자주 사용하는 명령어 별칭 (alias)지정하기

### alias

```shell
alias <사용할 명령어>="<명령어 내용>"

# Pycharm 실행
alias py="open -a /Applications/PyCharm\ CE.app/Contents/MacOS/pycharm"
```


## Pycharm 터미널에서 UnicodeEncodeError날 때

**~/.zshrc**

```
export PYTHONIOENCODING=UTF-8
```
