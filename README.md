##터미널 꾸미기
Mac OS에서 터미널을 조금 더 예쁘고 효율적으로 꾸미기입니다.

###iterm2 설치
기존 설치되어 있는 터미널보다 편의성 + 효율성을 높인 터미널 에뮬레이터입니다.

[설치링크](https://www.iterm2.com)

설치한 후 아래에 모든 과정은 iterm2를 실행해서 따라하면 됩니다.

###Homebrew 패키지 설치
터미널에서 `brew`로 시작하는 방대한 명령어를 입력하기 위해 설치합니다. 아래 명령어를 터미널에 입력합니다.

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
Homebrew를 설치했으면 이제 최신 상태로 업데이트를 해야합니다. 아래 명령어를 순차적으로 터미널에 입력합니다.

```
brew update
```
``` 
brew upgrade
```

###zsh 설치
Mac 터미널의 기본 shell은 `bash`이지만, 자동완성기능이나 수많은 플러그인 및 테마를 지원하는 `zsh`를 많이 사용합니다.

```
brew install zsh
```
`zsh`를 설치를 해주었으니, 이제 기본 shell을 `bash`에서 `zsh` 로 바꿔줍니다.


```
which zsh
```
우선 위의 명령어를 터미널에 입력하면 아래와 같은 경로가 나옵니다.(개인 마다 다를 수 있습니다.)

`/usr/local/bin/zsh
`

이 경로를 통째로 복사하고 아래 명령어를 터미널에 입력합니다.

```
sudo vi /etc/shells
```

사용자 암호를 입력하고, i를 눌러 insert 모드에 들어가서 마지막에 위에서 복사한 경로를 붙여 넣습니다. esc를 한번 누르고 `:wq`를 입력해 저장하고 나옵니다.

그 후 아래 명령어를 입력합니다.

```
chsh -s `which zsh` 
```

터미널을 완전히 종료 후 재시작해서 `echo $SHELL`을 입력하면 `zsh` 로 바뀐 것을 확인할 수 있을 것입니다.

###oh-my-zsh 설치
사실 `zsh`를 사용하는 가장 큰 이유는 이 `oh-my-zsh`라고 해도 과언이 아닙니다.(수많은 플러그인과 테마를 지원하기 때문..)아래 명령어를 터미널에 입력해서 설치합니다.

```
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

###agnoster 테마 사용하기
이 부분은 많은 사람들이 사용하고 있는 `oh-my-zsh`의 `agnoster` 테마로 바꾸는 법이며, 개인 취향대로 다른 테마로 변경하면 됩니다.

```
vi ~/.zshrc
```

위의 명령어를 입력하면 중간에`ZSH_THEME="~~~"` 부분이 보일겁니다. 이 부분을 `ZSH_THEME="agnoster"`로 바꾸시고 esc를 누르고 `:wq`를 입력해 저장하시면 됩니다. 

저장을 하고 나오면 테마가 바로 바뀌는 경우도 있지만 안바뀌는 경우도 있습니다. 안바뀌었을 때는 터미널을 완전히 종료 후 재시작 하시면 됩니다.

테마를 바뀐 후에 글자도 깨지고, 디자인도 훨씬 이상해졌나요? 네, 정상입니다. 이제부터 `agnoster` 테마를 잘 사용하기 위해 아래 테마 파일과 폰트를 설치한 후 세팅을 해줘야합니다.

[테마 다운받기](http://ethanschoonover.com/solarized/files/solarized.zip)

[폰트 다운받기](https://github.com/powerline/fonts/blob/master/Meslo/Meslo%20LG%20M%20DZ%20Regular%20for%20Powerline.otf)

테마는 받으신 후 적당한 곳에 압축을 풀면 되고, 폰트는 실행해 설치를 하면 됩니다.

그 후, 터미널로 돌아와서 

1. `cmd + ,` -> `Profiles` -> `Colors` -> `Color Presets` -> `Import` -> `다운 받은 폴더 중 iterm2-colors-solarized/Solarized Dark.itermcolors 를 선택` -> `import된 Solarized Dark를 선택`

2. `cmd + ,` -> `Profiles` -> `Text` -> `Change Font` -> `All Fonts` -> `Meslo LG M DZ...for Powerline 을 선택` 

그러면 깔끔해진 터미널 화면을 볼 수 있을 것입니다.

###vim에서도 테마 적용
사실 vi로 파일을 열게 되면 문장도 잘 안보이고 한 눈에 안들어오는데 여기도 테마를 적용시키면 알록달록 한눈에 잘 들어옵니다.

우선 아래 명령어를 순차적으로 터미널에 입력해주세요.

```
cd
mkdir .vim
cd .vim
mkdir bundle
cd bundle
```
```
git clone https://github.com/altercation/vim-colors-solarized.git
```
```
vi ~/.vimrc
```
그 후 아래 문구를 복사 및 붙여 넣고 저장

```
vim ~/.vimrc
 
set rtp+=~/.vim/bundle/vim-colors-solarized/
 
syntax enable
set bg=dark
set t_Co=256
colorscheme solarized
set tabstop=4
set shiftwidth=4
set softtabstop=4
set expandtab
set enc=utf8
set nu
set et ts=4
ret 4
```

그 후 아래 명령어로 `vimrc` 파일 새로고침

```
source ~/.vimrc
```

그럼 vi 로 파일을 편집할 때 알록달록 화면을 볼 수 있습니다.

###@뒤에 문구 삭제
테마를 설치 후 어느정도 깔끔해졌지만, 눈에 거슬리는 것이 보일 겁니다. 바로 `사용자명@Macbook-pro~~` 이런식으로 시작하는 부분입니다. 물론 눈에 안 거슬릴수도 있는 부분이지만 저처럼 거슬리시는 분들은 없애봅시다.

```
cd ~/.oh-my-zsh/themes
```
```
vi agnoster.zsh-theme
```

여시고 중간 부분에 `prompt_context()`라고 되어 있는 부분을 찾아 아래처럼 변경한 뒤 저장하면 됩니다. 


`$USER@m` -> `$USER`


그 후 `.zshrc` 파일 새로고침을 하면 적용이 됩니다.

```
source ~/.zshrc
```

###Powerline 설치
평소 git을 사용하거나 vim 에디터를 많이 사용하면 현재 상황을 바로 알아채야 하는데, 한 눈에 볼 수 있게 해주는 일종의 `상태바`가 `powerline` 입니다.

먼저 `python` 을 설치해줍니다. `python` 설치시 `pip` 도 자동으로 설치됩니다.

```
brew install python
```

그 후 `powerline`을 설치해줍니다.

```
pip install git+git://github.com/Lokaltog/powerline
```
```
vi ~/.vimrc
```
아래 문구 추가 후 저장합니다.

```python
set laststatus=2
set noshowmode
python from powerline.vim import setup as powerline_setup
python powerline_setup()
python del powerline_setup
```
```
source ~/.vimrc
```
에러가 나오긴 하지만 일단 무시해주세요.

###zsh-syntax-highlighting 설치
zsh에서 명령어를 입력할 때도 단어별로 알록달록 한 눈에 알아보기 쉽게 나타내고 싶다면 `syntax-highlighting`을 설치해주시면 됩니다.

```
brew install zsh-syntax-highlighting
```
설치를 해주시고 `.zshrc` 파일에 추가를 해줘야 합니다.

```
vi ~/.zshrc
```

아래 문구 추가 후 저장

`source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh`

그 후 `.zshrc` 새로고침

```
source ~/.zshrc
```



