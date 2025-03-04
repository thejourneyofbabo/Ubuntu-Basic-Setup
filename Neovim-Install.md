202401140353
Status: #linux
Tags:
### Ubuntu

[Download newest Neovim on Ubuntu](https://github.com/neovim/neovim/blob/master/BUILD.md)

```shell
1. git clone https://github.com/neovim/neovim
2. cd neovim && make CMAKE_BUILD_TYPE=RelWithDebInfo
3. git checkout stable
4. cd build && cpack -G DEB && sudo dpkg -i nvim-linux64.deb #우분투라면 이걸로 가능
5. sudo make install 

sudo apt-get install ninja-build gettext cmake unzip curl
- 이걸로 cmake 다운받기

#cargo install bob-nvim
#sudo snap install nvim --classic
```
[bob-github](https://github.com/MordechaiHadad/bob)

---
#### References
