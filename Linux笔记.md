# Linux笔记

[toc]



## 1. 图形界面相关

### 1.1 桌面快捷方式（优麒麟下测试）

配置文件后缀**.desktop**

开始菜单文件目录`/usr/share/applications/`

偶然发现用户家目录下`.local/share/applications`也存在desktop文件，可以直接复制过去，但需要注意需要有读权限，可以通过`chmod 644 *.desktop`配置。

下面粘贴麒麟影音的配置文件可供参考

```desktop
[Desktop Entry]
Name=Kylin Video
Name[zh_CN]=麒麟影音
Comment=A great MPlayer front-end
Comment[zh_CN]=麒麟影音
GenericName=Kylin Video
GenericName[zh_CN]=麒麟影音
Exec=kylin-video %U
Icon=kylin-video
MimeType=audio/ac3;audio/mp4;audio/mpeg;audio/vnd.rn-realaudio;audio/vorbis;audio/x-adpcm;audio/x-matroska;audio/x-mp2;audio/x-mp3;audio/x-ms-wma;audio/x-vorbis;audio/x-wav;audio/mpegurl;audio/x-mpegurl;audio/x-pn-realaudio;audio/x-scpls;audio/aac;audio/flac;audio/ogg;video/avi;video/mp4;video/flv;video/mpeg;video/quicktime;video/vnd.rn-realvideo;video/x-matroska;video/x-ms-asf;video/x-msvideo;video/x-ms-wmv;video/x-ogm;video/x-theora;video/webm;
Type=Application
Categories=Qt;KDE;AudioVideo;Player;Video;
Keywords=movie;player;media;kde;qt;
X-Ayatana-Desktop-Shortcuts=Screen;Window

```



## 2. 命令行相关

### 2.1 LInux Shell输出重定向到剪切板

```bash
# 安装工具
sudo apt-get install xclip

# 添加别名配置
# zsh
sudo echo alias x="xclip -selection c" >> ~/.zshrc
source ~/.zshrc
# bash
# 注：实验中引号会被去除，需要添加转义字符
sudo echo alias x=\"xclip -selection c\" >> ~/.bashrc
source ~/.bashrc

# 输出到剪切板
ls | x

# 剪切板保存到文件
x FILENAME
# 管道输出
cat FILENAME | x

# 直接打印在终端
x -o
# 重定向入文件
x -o >> FILENAME
```



### 2.2 SSH 配置文件

在**.ssh**目录下新建**config**文件

```
Host ali
	HostName 39.103.138.119
	User root
	IdentityFile ~/.ssh/alitest.pem
```

* Host 指定服务器别名（可以使用形如`ssh ali`的方式快速连接到服务器）

* IdentityFile 配置秘钥文件的位置，推荐使用绝对路径