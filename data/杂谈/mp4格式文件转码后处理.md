# mp4格式文件转码后处理（qt-faststart工具介绍）
当前很多工具能提供mp4格式的转换输出，但有时输出的格式拿到网络上后发现需要完整下载后才能开始播放，而不能像网上的很多视频那样一开始就能播放（边下边放），造成这个问题的原因是一些描述mp4文件信息的`moov atom`元数据默认放置在了视频文件的最后，而所有的播放器（包括独立的、网络化的——如浏览器）都需要这些信息来正确构建播放（比如视频分辨率到底是多少，视频到底有多长......）由此需要把这些信息想办法移动到mp4文件的前部，这样读取到这些信息后客户端播放器就可以搭起播放环境，后续只需要播放数据即可。能完成这项工作的工具有很多，这里介绍`qt-faststart`这个小程序。

## `qt-faststart`简介
qt-faststart是一个由Mike Melanson (melanson@pcisys.net)写的开源程序，是一个命令行工具。你可能可以在很多地方找到它的源码，我一般是在`FFmpeg`的源码中拿，它通常放在`FFmpeg`源码的`tools`目录下，比如`github`仓库中的位置为[https://github.com/FFmpeg/FFmpeg/blob/master/tools/qt-faststart.c](https://github.com/FFmpeg/FFmpeg/blob/master/tools/qt-faststart.c)。该程序只有一个源码文件，很小（不到13KB）。

## `qt-faststart`编译与使用
要使用它需要先编译,这个程序能利用大多数编译工具实现编译，因为我一般在`linux`下使用，所以直接`make tools/qt-faststart.c` 即可在`tools`目录下产生出名为`qt-faststart`的可执行文件，然后把编译输出结果放置到系统搜索路径中即可以`qt-faststart`来进行调用使用了。

`qt-faststart`的使用十分简单，其调用格式为
```cmd
    qt-faststart <inMp4FilePath>  <outMp4FilePath>
```
 - `<inMp4FilePath>`:表示调整前的mp4文件路径
 - `<outMp4FilePath>`:表示调整后的输出mp4文件路径

mp4文件路径可以是绝对或者相对路径。

**补充说明**：
 1. mp4文件也可以替换为mov文件，因为这个工具其实最开始是为QuickTime格式视频文件编写的
 2. mp4/mov 文件中的`moov atom`数据必须是非压缩的才能利用这个工具。
