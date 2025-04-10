202401140353
Status: #linux
Tags:
### Ubuntu

[Download newest Neovim on Ubuntu](https://github.com/neovim/neovim/blob/master/BUILD.md)

```shell
1. git clone https://github.com/neovim/neovim
2. cd neovim && make CMAKE_BUILD_TYPE=RelWithDebInfo
3. git checkout stable
4. sudo make install 

---
** Extra **
cd build && cpack -G DEB && sudo dpkg -i nvim-linux64.deb # 오류날 경우, 우분투라면 이걸로도 가능

sudo apt-get install ninja-build gettext cmake unzip curl
- 이걸로 cmake 다운받기

#cargo install bob-nvim
#sudo snap install nvim --classic
```
[bob-github](https://github.com/MordechaiHadad/bob)

---
#### References
