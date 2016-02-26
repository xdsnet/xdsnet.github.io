[toc]

# HTML5视音频标签参考 #
本文将介绍HTML5中的视音频标签和对应的DOM对象。是相关资料的中文化版本，可以作为编写相关应用的简易中文参考手册。

## 一些约定
- 所有浏览器：指支持HTML5的常见桌面浏览器，包括IE9+、Firefox3.5+、Chrome3.0+、Oprae10.5+、Safari3.0+等等，以及常见的移动平台浏览器，包括Firefox3.5+、Chrome3.0+、Safari3.0+。此外也包括同这些浏览器采用相同内核的一系列再包装版本，如国内很多的浏览器发行版。
- 更新检测的浏览器版本为（2016.1.21）：Firefox43.0.4、Chrome47.0.2526、IE11.0.9600、Opera33.0、Safari5.1.7（windows）、Safari（OSX）
- 部分浏览器则给出具体的浏览器类型及版本号范围
- 对于HTML标签中系列值为布尔值的属性，只要在标签中进行了定义即表示定义为`true`值，其实这些属性，只要进行了定义，且值不为`false|0|""`均表示为真。

## 音频标签

### 基本形式示例
```html
    <audio src=”resURI.mp3” controls=“controls”>
		你的浏览器不支持audio标签
	</audio>
```
或者
```html
	<audio controls=”controls” autoplay=”autoplay” loop=”loop” preload=”preload”>
		<source src=”resURI-1.ogg” type=”audio/ogg”>
		<source src=”resURI-2.mp3” type=”audio/mpeg”>
		你的浏览器不支持audio标签
	</audio>
```
### 主要标签属性定义及子标签介绍

 * `autoplay="false|true"`:定义了则页面就绪后自动加载播放
 * `controls="false|true"`：定义了则显示用户控制条
 * `crossorigin="CORSString"`:定义下载资源时如何处理跨域问题。
 * `loop="false|true"`：定义了则一直循环播放
 * `preload="none|metadata|auto"`:定义了则页面加载时对媒体资源进行预加载来预备播放。如果定义了`autoplay`属性，则本属性被忽略
 * *`mediagroup="mediagroupString"`（一般不被支持）*:分组音频播放
 * `muted="true|false"`:定义是否静音
 * `src="URI"`:定义要播放的资源URI
 * 子标签`<source>`用于定义一个可选的播放资源，一般包含`src="URI"` 和`type="audioType"`等属性定义，其中URI是资源的URI；`audioType`的常用值一般有`audio/ogg`、`audio/mpeg`和`audio/mp4`，用来指定资源的类型以方便判断是否支持。一个`<audio>`内可以定义多个`<source>`，但只能播放一个，这样的定义形式一般用于浏览器兼容处理，浏览器会加载第一个支持的资源形式而忽略掉其他的。

### 主要桌面浏览器支持情况（移动浏览器类似）

 * Ogg Vorbis格式： Firefox3.5+、Opera10.5+、Chrome3.0+、
 * MP3格式：IE9+、Chrome3.0+、Safari3.0+
 * WAV格式：Firefox3.5+、Opera10.5+、Safari3.0+

## 视频标签

### 基本形式示例
```html
	<video src="resURI.mp4" width="320" height="240" controls="controls">
		浏览器不支持video标签
	</video>
```	
或者
```html 
	<video width="320" height="240" controls=”controls” >
		<source src=”resURI-1.ogg” type=”video/ogg”>
		<source src=”resURI-2.mp4” type=”video/mp4”>
		<track src="textTrack.vtt" kind="captions" srclang="en" label="Closed Captions" default="">
		你的浏览器不支持audio标签
	</video>
```

### 主要属性标签属性和子标签介绍

 * `autoplay="false|true"`:定义了则页面就绪后自动加载播放
 * `controls="false|true"`：定义了则显示用户控制条
 * `crossorigin="CORSString"`:定义下载资源时如何处理跨域问题。
 * `loop="false|true"`：定义了则一直循环播放
 * *`mediagroup="mediagroupString"`（一般不被支持）*:分组音频播放
 * `muted="true|false"`:定义是否静音
 * `preload="none|metadata|auto"`:定义了则页面加载时对媒体资源进行预加载来预备播放。如果定义了`autoplay`属性，则本属性被忽略
 * `poster="mediaURI"`:定义一个资源（一般是图片）显示视频封面信息
 * `src="URI"`:定义要播放的资源URI
 * `height="hxxpx"`:定义视频播放器的高
 * `width="wxxpx"`:定义视频播放器的宽
 * 子标签`<source>`用于定义一个可选的播放资源，一般包含`src="URI"` 和`type="videoType"`等属性定义，其中URI是资源的URI；`videoType`的可能值一般有`video/Ogg`、`video/mp4`和`video/WebM`，用来指定资源的类型以方便判断是否支持。一个`<video>`内可以定义多个`<source>`，但只能播放一个，这样的定义形式一般用于浏览器兼容处理，浏览器会加载第一个支持的资源形式而忽略掉其他的。
 * 子标签`<track>`用户定义一个textTrack轨道（一般用作字幕等）。一般包含`src="textTrack.vtt"`、`srclang="en"`、 `kind="captions"`、`label="Closed Captions"`以及` default=""`属性定义，其中`kind`属性定义字符串轨道的类型，主要有：
	 * subtitles ——子标题
	 * captions ——字幕
	 * descriptions ——描述
	 * chapters ——章节
	 * metadata ——元数据

### 主要桌面浏览器支持情况（移动浏览器类似）

 * Ogg:Firefox3.5+、Opera10.5+、Chrome5.0+
 * MP4:IE9.0+、Chrome5.0+、Safari3.0+、Firefox35+(开始支持H.264这一常见编码)
 * WebM:Firefox4.0+、Opera10.6+、Chrome6.0
 * 3Gpp:Safari3.0+

## 音视频DOM参考

### 方法
当前在HTML5音视频DOM对象定义中主要有`addTextTrack()`（还未正式实现）、`canPlayType()`、`load()`、`play()`和`pause()`方法。下面是各方法介绍。

#### *`addTextTrack()`* （所有浏览器都不支持）
用来向音视频添加文本轨道

 * 语法: `audio|video.addTextTrack(kind,label,language)`
 * 参数介绍：
 
	- `kind`:规定文本轨道的类型，可能值：

		- "subtitles"
		- "caption"
		- "descriptions"
		- "chapters"
		- "metadata"

	- `label`:字符串值，为文本轨道规定标签。用于对文本轨道进行标识。
	- `language`:双字母语言代码，规定文本轨道的语言。例如英语是`en`,中文是`zh`

 * 返回值：一个`TextTrack`对象，表示新的文本轨道。
 * 调用示例： 
```js 
	text1=myVid.addTextTrack("caption");
	text1.addCue(new TextTrackCue("Test text", 01.000, 04.000,"","","",true));
```
#### `canPlayType() ` （所有主流浏览器均支持）
用来检测浏览器对音视频格式支持情况

 * 语法: `audio|video.canPlayType(type)`
 * 参数介绍：
 
	- `type`:一个表示规定要检测的音频/视频类型和具体编码的字符串格式为`MIMEString；codecsSting`
		- 常用值有：
			- video/ogg
			- video/mp4
			- video/webm
			- audio/mpeg
			- audio/ogg
			- audio/mp4
		
		- 含编码器的常用值
	
			- video/ogg codecs="theora, vorbis"
			- video/mp4；codecs="avc1.4D401E, mp4a.40.2"
			- video/webm；codecs="vp8.0, vorbis"
		
			- audio/ogg；codecs="vorbis"
			- audio/mp4；codecs="mp4a.40.5"
		
		其中`MIMEString`详见具体的mime信息见
[http://www.iana.org/assignments/media-types/](http://www.iana.org/assignments/media-types/)，[https://www.w3.org/TR/html5/embedded-content-0.html#attr-source-type](https://www.w3.org/TR/html5/embedded-content-0.html#attr-source-type)
另外浏览器对各类格式兼容情况可以参考[http://www.jwplayer.com/html5/](http://www.jwplayer.com/html5/)以及[http://www.jwplayer.com/html5/formats/](http://www.jwplayer.com/html5/formats/)

 * 返回值：一个`String`对象，表示支持的级别，可能值有:
	 * "probably" - 最有可能支持
	 * "maybe" - 可能支持
	 * "" - （空字符串）不支持

 * 调用示例： 
```js 
	myVid=document.createElement('video');
	isSupp=myVid.canPlayType(vidType+';codecs="'+codType+'"');
```
#### *`load()`* （除Safari外所有主流浏览器均支持）
更改资源后重新进行加载，没有返回值。**注意：** 仅仅是加载，并不会自动播放。
* 语法: `audio|video.load()`
* 调用示例： 
```js 
	document.getElementById("mp4_src").src="movie.mp4";
	document.getElementById("ogg_src").src="movie.ogg";
	document.getElementById("video1").load();
```
#### `play()`和 `pause()` （所有主流浏览器均支持）
开始/暂停播放当前音视频，没有返回值。
- 语法：`audio|video.play()`和`audio|video.pause()`
- 调用示例：

```js    
	var myVideo=document.getElementById("video1");
	function playVid(){
  		myVideo.play();
	}
	function pauseVid() {
  		myVideo.pause();
	}
```
**注意** 并没有所谓的 *`stop()`* 方法，即没有停止方法，其效果可由`load()`代替。

### 属性 
当前在HTML5音视频DOM对象定义中主要有`audioTracks`、`autoplay`、`buffered`、`controller`、`controls`、`crossOrigin`、`currentSrc`、`currentTime`、`defaultMuted`、`defaultPlaybackRate`、`duration`、`ended`、`error`、`loop`、`mediaGroup`、`muted`、`networkState`、`paused`、`playbackRate`、`played`、`preload`、`readyState`、`seekable`、`seeking`、`src`、`startDate`、`textTracks`、`videoTracks`、`volume`，以及视频对象独有的`videoWidth`和`videoHeight`（**注意：** 一般对象的`width`和`height`被支持，但不能获取正确的值）下面是各属性介绍。

#### `videoWidth`和`videoHeight`（所有浏览器都支持）
获取当前HTML5视频的宽和高。

- 语法：`video.videoWidth`或`video.videoHeight`
- 值介绍：数值值，表征当前视频宽和高，如果视频未加载则都为0。
- 调用示例：

```js
	myVid=document.getElementById("video1");
	alert("视频"+myVid.videoWidth+",宽"+myVid.videoHeight+"高");
```
#### *`audioTracks`* (浏览器IE支持)
只读值，返回表示可用音轨的`AudioTrackList`类型对象

- 语法：`audio|video.audioTracks`
- 值介绍：一个以下标0开始的`AudioTrackList`类型对象，表示所有可用音轨。`AudioTrackList`类型对象有如下属性：
	- `audioTrackList.length`-可用音轨数量
	- `audioTracks.getTrackById(id)` - 通过`id`来获得 `AudioTrack`类型对象
	- `audioTracks[index]` - 通过 `index` 来获得 `AudioTrack` 对象

   一个`AudioTrack` 对象表示一条音轨，有如下属性：

	- `id` - 获得音轨的 `id`
	- `kind` - 获得音轨的类型（可以是 "alternative", "description", "main", "translation", "commentary", 或者 "" （空字符串））
	- `label` - 获得音轨的标签
	- `language` - 获得音轨的语言
	- `enabled` - 获得或设置音轨是否是活动的 (`true`|`false`)

- 调用示例：

```js
	myVid=document.getElementById("video1");
	alert(myVid.audioTracks.length);
```
#### `autoplay` (所有浏览器支持)
用于设置或者获取视音频对象是否加载后即开始播放的属性。
- 语法：设置时`audio|video.autoplay=true|false`、获取时`audio|video.autoplay`
- 值介绍：为`bool`类型值，可能值为`true`-表示加载后即开始播放，或`false`-表示不自动播放（默认）
- 调用示例
```js 
	myVid=document.getElementById("video1");
	myVid.autoplay=true;
	myVid.load();
```
#### `buffered` (所有浏览器支持)
只读值，用于获得视音频加载缓冲情况。
- 语法：`audio|video.buffered`
- 值介绍：值为一个`TimeRanges`对象，表示对当前资源加载的情况。一个`TimeRanges`对象可以描述资源已经缓冲的情况，它有如下属性
	- `lenght`-已经缓冲范围的数量（因为视音频数据包传递问题，可能不一定连续，所以需要分段）
	- `start(index)` - 获得某个已缓冲范围的开始位置，以秒计
	- `end(index)` - 获得某个已缓冲范围的结束位置，以秒计
	
	**注释：**`index`是缓冲范围下标，从0开始计数到`lenght-1`
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	lenght=myVid.buffered.lenght;
	out="视频有"+lenght+"段缓冲区,各段起始时间(秒)为:\n";
	for(var i=0;i<lenght;i++)
	    out=out+"第"+(i+1)+"段Start: "+myVid.buffered.start(i)+" End: "+myVid.buffered.end(0)+"\n";
	alert(out);
```
#### *`controller`* (所有主流浏览器都不支持)
只读值，检测一个视频是否有对应的媒体控制器
 - 语法：`audio|video.controller`
 - 返回值：一个`MediaController`对象，表示音视频的媒体控制器。`MediaController`对象有如下属性/方法
	 - `buffered` - 获得音视频的缓冲范围
	 - `seekable` - 或者音视频的可寻址范围
	 - `duration` - 获得音视频的时长
	 - `currentTime` - 获得或设置音视频的当前播放位置
	 - `paused` - 检测音视频是否已暂停
	 - `play()` - 播放音视频
	 - `pause()` - 暂停音视频
	 - `played` - 检测音视频是否已播放过
	 - `defaultPlaybackRate` - 获得或设置音视频的默认播放速率
	 - `playbackRate` - 获得或设置音视频的当前播放速率
	 - `volume` - 获得或设置音视频的音量
	 - `muted` - 获得或设置音视频是否已静音
- 调用示例：
```js
	myVid=document.getElementById("video1");
	alert("Controller: " + myVid.controller);
```
#### `controls` (所有浏览器支持)
为音视频设置/获取对应的控件（用于控制播放，每种浏览器的样式不同）状态
 
- 语法：
	- 设置：`audio|video.controls=true|false`
	- 获取：`audio|video.controls`
- 值介绍：`controls`属性值是布尔值，为`true`表示显示控件，为`false`表示不显示控件
- 关于控件的介绍：一个标准的音视频控件包括如下按钮
	- 播放
	- 暂停
	- 进度条
	- 音量
	- 全屏切换（仅视频）
	- 字幕（当可用时）
	- 轨道（当可用时）
- 调用示例：
```js
	myVid=document.getElementById("video1");
	myVid.controls=true;
```
#### *`crossOrigin`* (除IE和Safari外所有浏览器支持)
设置/返回 音视频对象的`CORS`（跨站共享）设置

- 语法：
	- 设置：`audio|video.crossOrigin="CORS-String"`
	- 获取：`audio|video.crossOrigin`
- 值介绍：`crossOrigin`属性值为`CORS-String`字符串，主要有4种情况
	- 空值即`""`:等效于`anonymous`模式，且
	- `anonymous`:`anonymous`状态
	- 没有定义（默认值）:**`No CORS`**状态，**注意** 与`anonymous`状态的区别，表示忽略掉默认状态的一种特殊状态
	- `use-credentials`：对应`Use Credentials`状态
- `CORS`（跨站共享）状态对资源获取影响：
	- 请求的URL与定义媒体资源页面同源、或者URL为`data:URL`、或者URL为`about:blank`则执行如下步骤：
	1. 去获取URL，并且带有`manual redirect flag`（手动重定向）标记
	2. 循环：利用获取算法判断获取结果是否需要重定向
	3. 在下面情况中选取一种恰当的步骤执行：
		- 如果获取为一个重定向，且重定向的目标和源不同源（简单讲就不在同一域名下），则设置URL为重定向URL，返回一个`
		- potentially CORS-enabled fetch`消息（此时，之后的行为会根据这里的处理进行响应——包括禁止/允许）等待交互处理（一般为浏览器展示一个提醒）
		- 如果为一个重定向，且目标同源，则直接重定向，跳到循环步骤
		- 不是重定向（指向具体资源），资源同源且有效，则获取解析展示

	- `No CORS`模式，且默认值被污染（可能根据前面的交互），而URL不同源：获取URL，即允许跨域
	- `No CORS`模式，且默认值为禁止（可能根据前面的交互），而URL不同源，则不获取URL，即不允许跨域
	-  `Anonymous`或者`Use Credentials`状态，如果URL不同源，按下面步骤执行：
		1. 以URL执行一次`cross-origin request`跨域请求（向当前源），其中`request URL`设置为URL目标值，`CORS referrer source`部分设置为`referrer source`，`source origin`设置为当前源信息， `omit credentials flag`设置为`Anonymous`或者省略掉
		2. 等待`cross-origin request status`返回
		3. 根据返回值情况处理见：
			- 如果返回为`not success`(不成功)，则禁止后续跨站获取，对于浏览器相当于获取不到相应资源
			- 如果返回为`success`(成功)，则继续获取（即允许跨站访问）

- 调用示例：
```js
	myVid=document.getElementById("video1");
	myVid.crossOrigin=`anonymous`;
```
#### `currentSrc` (所有浏览器支持)
只读，取得当前实际播放资源URL，如果未设置则返回空字符串
- 语法：`audio|video.currentSrc`
- 返回值：为表示当前实际播放资源的URL，为空表示没播放
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	alert("Controller:"+myVid.currentSrc);
```
#### `currentTime` (所有浏览器支持)
设置/取得当前播放资源时间位置数值（以秒计），
- 语法：
	- 设置：`audio|video.currentTime=5`
	- 获取：`audio|video.currentTime`
- 值介绍：为表示当前实际播放的位置数值（以秒计）
- 调用示例：
```js
	myVid=document.getElementById("video1");
	cuT=myVid.currentTime;
	myVid.currentTime=cut+10;//向后跳10秒
```
#### *`defaultMuted`* (只有浏览器Chrome、Firefox、Oprae支持)
设置/获取音视频是否默认静音。**注意**，这个属性仅仅改变默认静音状态，而不是当前状态，要改变当前是否静音，需要使用`muted`属性。
- 语法:
 	- 设置：`audio|video.defaultMuted=true`
	- 获取：`audio|video.defaultMuted`
- 值介绍：布尔值，为`true`表示音视频默认静音，为`false`（默认值）表示默认不静音
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	cuT=myVid.defaultMuted;
	myVid.defaultMuted=!cuT;//反置defaultMuted属性
```
#### *`defaultPlaybackRate`* (只有浏览器Chrome、Firefox、Oprae支持)
设置/获取音视频默认播放速度。**注意**，这个属性仅仅改变默认播放速度，而不是当前的播放速度，要改变当前是播放速度，需要使用`playbackRate`属性。
- 语法:
 	- 设置：`audio|video.defaultPlaybackRate =playbackspeed`
	- 获取：`audio|video.defaultPlaybackRate `
- 值介绍：数值，为一般为`-2.0-2.0`，默认为`1`（表示正常速度），为负值则为后退播放。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	playbackspeed=myVid.defaultPlaybackRate ;
	myVid.defaultPlaybackRate =(playbackspeed>1)?1:playbackspeed;//如果速度比1大（是快速）就恢复为1（标准速度）
```
#### `duration` (所有浏览器支持)
获取音视频长度值（以秒为单位）。**注意**因为媒体资源长度可能是根据数据包计算，也可能是写入`metadata`中，所以在加载中，对于写入`metadata`的，加载后就不会变化，对根据获取数据包计算的，可能这个值会不断发生改变（特别是对于较大的音频资源）
- 语法:`audio|video.duration`
- 值介绍：只读数值，如果获取为`NaN`表示还未设置音视频（没有初始化加载）。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	myDur=myVid.duration ;
	alert（"当前媒体长度为"+myDur+"秒"）;
```
#### `ended` (所有浏览器支持)
获取音视频播放是否结束状态
- 语法:`audio|video.ended`
- 值介绍：只读布尔值，如果获取为`true`表示还播放已结束，`fasle`表示还未结束。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	if(myVid.ended)
		alert（"当前媒体播放已结束"）;
```
#### `error` (所有浏览器支持)
获取音视频播放是否结束状态
- 语法:`audio|video.error`一般用`audio|video.error.code`
- 值介绍：只读值，返回一个`MediaError`对象值，`MediaError`的`code`属性（一个数值属性）标识了错误类型。`code`值有：
	- 1 = MEDIA_ERR_ABORTED - 取回过程被用户中止
	- 2 = MEDIA_ERR_NETWORK - 当下载时发生错误
	- 3 = MEDIA_ERR_DECODE - 当解码时发生错误
	- 4 = MEDIA_ERR_SRC_NOT_SUPPORTED - 不支持音频/视频

- 调用示例：
```js 
	myVid=document.getElementById("video1");
	alert(myVid.error.code);
```
#### `loop` (所有浏览器支持)
设置/获取音视频播放是否结束后循环播放
- 语法:
	- 获取：`audio|video.loop`
	- 设置:`audio|video.loop=true`
- 值介绍：布尔值，为`true`表示要循环播放，`fasle`（默认值）表示不循环播放。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	if(myVid.loop)
		alert（"当前媒体播放会循环播放"）;
```
#### *`mediaGroup`* (所有浏览器都不支持)
设置/获取多个音视频播放是组成一个组（从而同步播放）
- 语法:
	- 获取：`audio|video.mediaGroup`
	- 设置:`audio|video.mediaGroup="test"`
- 值介绍：字符串值,在一个页面中所有同组（`mediaGroup`值相同的）媒体会同步播放。
- 调用示例：
```js
	myVid1=document.getElementById("video1");
	myVid2=document.getElementById("video2");
	myVid1.mediaGroup="test";
	myVid2.mediaGroup="test";
	//至此，两个媒体就会同步播放啦
```
#### `muted` (所有浏览器支持)
设置/获取当前音视频是否静音。
- 语法:
 	- 设置：`audio|video.muted=true`
	- 获取：`audio|video.muted`
- 值介绍：布尔值，为`true`表示音视频静音，为`false`（默认值）表示不静音
- 调用示例：
```js
	myVid=document.getElementById("video1");
	cuT=myVid.muted;
	myVid.muted=!cuT;//反置muted属性——即静音开关
```
#### `networkState` (所有浏览器支持)
获取音视频播放是否结束状态
- 语法:`audio|video.networkState`一般用`audio|video.error.code`
- 值介绍：只读值，返回返回音频/视频的当前网络状态（activity）：
	- 0 = NETWORK_EMPTY - 音频/视频尚未初始化
    - 1 = NETWORK_IDLE - 音频/视频是活动的且已选取资源，但并未使用网络
    - 2 = NETWORK_LOADING - 浏览器正在下载数据
    - 3 = NETWORK_NO_SOURCE - 未找到音频/视频来源


- 调用示例：
```js
	myVid=document.getElementById("video1");
	alert(myVid.networkState);
```
#### `paused` (所有浏览器支持)
设置/获取当前音视频是暂停。
- 语法:
 	- 设置：`audio|video.paused=true`
	- 获取：`audio|video.paused`
- 值介绍：布尔值，为`true`表示音视频暂停播放，为`false`表示没有暂停
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	cuT=myVid.paused;
	myVid.paused=!cuT;//反置paused属性——即暂停开关
```
#### `playbackRate` (所有浏览器支持)
设置/获取当前音视频默认播放速度。
- 语法:
 	- 设置：`audio|video.playbackRate =playbackspeed`
	- 获取：`audio|video.playbackRate `
- 值介绍：数值，为一般为`-2.0-2.0`，默认为`1`（表示正常速度），为负值则为后退播放。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	playbackspeed=myVid.playbackRate ;
	myVid.playbackRate =(playbackspeed>1)?1:playbackspeed;//如果速度比1大（是快速）就恢复为1（标准速度）
```
#### `played` (所有浏览器支持)
获取当前音视频默认播放速度。
- 语法:`audio|video.played`常用`audio|video.played.start(0)`和 `audio|video.played.end(0)`	
- 值介绍：只读对象值，返回`TimeRanges`对象。一个`TimeRanges`对象标记了当前已经播放的范围，一个`TimeRanges`对象有如下属性：
    - length - 获得音频/视频中已播范围的数量
    - start(index) - 获得某个已播范围的开始位置（秒计，index<length）
    - end(index) - 获得某个已播范围的结束位置（秒计,index<length）
    
 **注释：** 首段已播放范围的下标是0。
- 调用示例：
```js
	myVid=document.getElementById("video1");
	alert("已经播放: " + myVid.played.start(0) + " 到: " + myVid.played.end(0));
```
#### `preload` (所有浏览器支持)
设置/获取音视频是否在页面加载后自动进行加载。
- 语法:
 	- 设置：`audio|video.preload="auto|metadata|none"`
	- 获取：`audio|video.preload`
- 值介绍：字符串值，为`auto`表示音视频自动加载，为`metadata`表示仅加载元数据，为`none`表示不自动加载
- 调用示例：
```js
	myVid=document.getElementById("video1");
	alert(myVid.preload);//显示当前视音频预加载设置
	myVid.preload="auto";//将当前视音频设置为自动加载——后面进行切换源属性后也会自动加载
```
#### `readyState` (所有浏览器支持)
只读获取音视频就绪状态。
- 语法:`audio|video.readyState`
- 值介绍：数值值，各值描述如下：
    - 0 = HAVE_NOTHING - 没有关于音频/视频是否就绪的信息
    - 1 = HAVE_METADATA - 关于音频/视频就绪的元数据
    - 2 = HAVE_CURRENT_DATA - 关于当前播放位置的数据是可用的，但没有足够的数据来播放下一帧/毫秒
    - 3 = HAVE_FUTURE_DATA - 当前及至少下一帧的数据是可用的
    - 4 = HAVE_ENOUGH_DATA - 可用数据足以开始播放

- 调用示例：
```js 
	myVid=document.getElementById("video1");
	if(myVid.readyState=4){//如果就绪
		myVid.play();//开始播放
	}
```	
#### `seekable` (所有浏览器支持)
只读获取音视频可寻址范围
- 语法:`audio|video.seekable`
- 值介绍：返回 `TimeRanges` 对象。`TimeRanges` 对象表示音频/视频中用户可寻址的范围。可寻址范围指的是用户在音频/视频中可寻址（可直接移动播放的位置）的时间范围。对于流视频，通常可以寻址到视频中的任何位置，即使其尚未完成缓冲`TimeRanges` 对象有如下属性：
	- length - 获得音频/视频中可寻址范围的数量
    - start(index) - 获得可寻址范围的开始位置
    - end(index) - 获得可寻址范围的结束位置

	**注释：** 第一个可寻址范围的下标是 index 0。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	alert("开始: " + myVid.seekable.start(0) + " 结束: " + myVid.seekable.end(0));
```
#### `seeking` (所有浏览器支持)
只读获取音视频是否真正寻址定位
- 语法:`audio|video.seeking`
- 值介绍：返回布尔值，`true`表示正在寻址，`false`表示没有寻址。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	document.getElementById("span1").innerHTML=("定位中: " + myVid.seeking);
```
#### `src` (所有浏览器支持)
设置（一般不用做获取）音视频资源URL，要获取请用`currentSrc`属性
- 语法:
	- 设置：`audio|video.src=URL`
- 值介绍：URL字符串，指示资源URL，可以采用相对或者绝对路径。
- 调用示例：
```js
	myVid=document.getElementById("video1");
	myVid.src="movie.ogg";
```
#### *`textTracks`*(除Safari（windows下的）外所有浏览器支持)
只读获取音视频中可用的文本轨道
- 语法:`audio|video.textTracks`
- 值介绍：`TextTrackList`对象，表示当前视音频中所有可用的文本轨道。`TextTrackList`对象有如下属性：
	- length：获得音频/视频中可用的文本轨道的数量
	- [index] - 根据下标来获得 `TextTrack`对象（即一条文本轨道信息——包含一系列字符串信息，如字幕信息），从0开始下标。一个`TextTrack`对象又包含如下属性（方法）： 
    	- kind - 获得文本轨道的类型（可以是 "subtitles", "caption", "descriptions", "chapters" 或者 "metadata")
    	- label - 获得文本轨道的标签
    	- language - 获得文本轨道的语言
    	- mode - 获得或设置该轨道是否是活动的 ("disabled"|"hidden"|"showing")
    	- cues - 获得 TextTrackCueList 对象的 cues 列表
    	- activeCues - 获得 TextTrackCueList 对象形式的当前活动文本轨道 cues
    	- addCue(cue) - 向 cues 列表添加一个 cue
    	- removeCue(cue) - 从 cues 列表删除一个 cue

- 调用示例：
```js
	myVid=document.getElementById("video1");
	alert(myVid.textTracks.length+"条文本轨道");
```
#### *`videoTracks`* (所有浏览器都不支持)
只读获取音视频时间线偏移
- 语法:`video.videoTracks`(**注意：** 只有`video`对象才可能有这个属性)
- 值介绍：返回`VideoTrackList`对象值，表示当前表示视频的可用视频轨道。`VideoTrackList`对象有如下属性：
	- length - 获得视频中可用视频轨道的数量
    - getTrackById(id) - 通过 id 获得 VideoTrack 对象
    - [index] - 通过下标获得 `VideoTrack` 对象
    - selectedIndex - 获得当前 `VideoTrack` 对象的下标

	**注释：**第一个可用 VideoTrack 对象的下标是 0。
	
	一个`VideoTrack` 对象有如下属性：
		- id - 获得视频轨道的 id
    	- kind - 获得视频轨道的类型（可以是 "alternative", "captions", "main", "sign", "subtitles", "commentary", 或 "" （空字符串））
    	- label - 获得视频轨道的标签
    	- language - 获得视频轨道的语言
    	- selected - 获得或设置视频轨道是否是活动的 (true|false)

- 调用示例：
```js
	myVid=document.getElementById("video1");
	alert(myVid.videoTracks.length+"条视频轨");
```
#### `volume` (所有浏览器支持)
设置/获取音视频音量
- 语法:
	- 获取：`audio|video.volume`
	- 设置：`audio|video.volume=volumevalue`
- 值介绍：数值值，范围为`0.0-1.0`，`1.0`（默认）是最大音量，`0.0`是静音。
- 调用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.volume=0.2;//设置为20%音量
```
### 事件
当前在HTML5音视频DOM对象定义中主要有`abort`、`canplay`、`canplaythrough`、`durationchange`、`emptied`、`ended`、`error`、`loadeddata`、`loadedmetadata`、`loadstart`、`pause`、`play`、`playing`、`progress`、`ratechange`、`seeked`、`seeking`、`stalled`、`suspend`、`timeupdate`、`volumechange`、`waiting`等事件可以侦测使用。下面是各事件介绍。

#### `abort`(所有浏览器支持)
当视音频在加载中被用户放弃时触发。`error`属性有`MEDIA_ERR_ABORTED`错误码，`networkState`属性为`NETWORK_EMPTY`或者`NETWORK_IDLE`状态。

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onabort=alert("视频加载被终止！");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onabort="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("abort", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```

#### `canplay` (所有浏览器支持)
当浏览器能够开始播放指定的音频/视频时，发生 `canplay` 事件。当音频/视频处于加载播放过程中时（能正常播放情况下），会依次发生以下事件：
	
1. `loadstart`	
1. `durationchange`
1. `loadedmetadata`
1. `loadeddata`
1. `progress`
1. `canplay`
1. `canplaythrough`

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.oncanplay=alert("可以开始播放视频啦");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video oncanplay="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("canplay", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `canplaythrough` (所有浏览器支持)
当浏览器预计能够在不停下来进行缓冲的情况下持续播放指定的音频/视频时，会发生 `canplaythrough` 事件。可以用来提示状态。`redyState`属性变得大于等于`HAVE_FUTURE_DATA`。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.oncanplaythrough=alert("视频可一直播放");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video oncanplaythrough="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("canplaythrough", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```

#### `durationchange` (所有浏览器支持)
当指定音频/视频的时长数据发生变化时，发生 `durationchange` 事件。

当音频/视频加载后，时长将由 "NaN" 变为音频/视频的实际时长。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.ondurationchange=alert("视频持续时间已经变化");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video ondurationchange="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("durationchange", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `emptied` (所有浏览器支持)
当指定音频/视频目前的播放列表为空时，发生 `emptied` 事件。`networkState`属性值变为`NETWORK_EMPTY`。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onemptied=alert("播放列表为空");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onemptied="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("emptied", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `ended` (所有浏览器支持)
当指定音频/视频目前的播放列表已结束时，发生 `ended` 事件。此时`currentTime`值等于媒体资源最大值，且`ended`属性值为`true`。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onended=alert("播放列表已结束");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onended="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("ended", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `error` (所有浏览器支持)
当指定音频/视频目前的播放列表已结束时，发生 `error` 事件。`error`属性对象有`MEDIA_ERR_NETWORK`以上的错误码，`networkState`属性为`NETWORK_EMPTY`或者`NETWORK_IDLE`状态。

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onerror=alert("发生错误");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onerror="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("error", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `loadeddata` (所有浏览器支持)
当前帧的数据已加载，但没有足够的数据来播放指定音频/视频的下一帧时，会发生 `loadeddata` 事件。`readyState`属性变为大于等于`HAVE_CURRENT_DATA`

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onloadeddata=alert("当前帧加载完毕");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onloadeddata="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("loadeddata", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `loadedmetadata` (所有浏览器支持)
当指定的音频/视频的元数据已加载时，会发生 `loadedmetadata` 事件。`readyState`属性变为大于等于` HAVE_METADATA`

音频/视频的元数据包括：时长、尺寸（仅视频）以及文本轨道。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onloadedmetadata=alert("元数据信息加载完毕");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onloadedmetadata="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("loadedmetadata", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `loadstart` (所有浏览器支持)
当浏览器开始寻找指定的音频/视频时，会发生 `loadstart` 事件。即当加载过程开始时。`networkState`属性等于`NETWORK_LOADING`。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onloadstart=alert("开始加载播放");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onloadstart="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("loadstart", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `pause` (所有浏览器支持)
当音频/视频已暂停时时，会发生 `pause` 事件。此时`paused`属性会变成`true`

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onpause=alert("播放暂停");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onpause="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("pause", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `play` (所有浏览器支持)
当音频/视频已开始或不再暂停时，会发生 `play` 事件。此时`paused`属性会变成`false`

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onplay=alert("播放中");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onplay="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("play", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `playing` (所有浏览器支持)
当音频/视频在已因缓冲而暂停或停止后已就绪时，会发生 `playing` 事件。此时`readyState`值要变得等于或者大于`HAVE_FUTURE_DATA`，且`paused`属性值为`false`；或者`readyState`值要等于或者大于`HAVE_FUTURE_DATA`，而`paused`属性值变为`false`。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onplaying=alert("播放恢复");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onplaying="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("playing", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `progress` (所有浏览器支持)
当浏览器正在下载指定的音频/视频时，会发生 `progress` 事件。`networkState`属性等于`NETWORK_LOADING`。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onprogress=alert("数据加载中");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onprogress="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("progress", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `ratechange` (所有浏览器支持)
当音频/视频的播放速度已更改时，会发生 `ratechange` 事件。

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onratechange=alert("播放速度调整了");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onratechange="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("ratechange", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```

#### *`resize`* (浏览器Chrome支持)
视频的播放区域大小更改时（`videoWidth`或`videoHeight`属性发生变化时），会发生 `resize` 事件。但`readyState`属性值不会是`HAVE_NOTHING`值

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onresize=alert("播放大小变化了");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onresize="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("resize", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```

#### `seeked` (所有浏览器支持)
当用户已移动/跳跃到音频/视频中的新位置时，会发生 `seeked` 事件。

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onseeked=alert("已经重新定位");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onseeked="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("seeked", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `seeking` (所有浏览器支持)
当用户开始移动/跳跃到音频/视频中的新位置时，会发生 `seeking` 事件。

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onseeking=alert("重新定位中");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onseeking="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("seeking", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `stalled` (所有浏览器支持)
当浏览器尝试获取媒体数据，但数据不可用时，会发生 `stalled` 事件。`networkState`属性值为 `NETWORK_LOADING`。 

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.onstalled=alert("数据不可用");
```
此外还可以在标签中定义使用，例如：
```html
	<audio|video onstalled="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("stalled", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `suspend` (所有浏览器支持)
当浏览器刻意不获取媒体数据时（权限、跨域等等问题），会发生 `suspend` 事件。`networkState`属性等于`NETWORK_IDLE`

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onsuspend=alert("不允许获取数据");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onsuspend="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js
	audio|video.addEventListener("suspend", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `timeupdate` (所有浏览器支持)
当目前的播放位置已更改时，会发生 `timeupdate` 事件，一般用来更新指示器，也可以用于同步。

应用示例：
```js 
	myVid=document.getElementById("video1");
	myVid.ontimeupdate=alert("播放头已移动");
```
此外还可以在标签中定义使用，例如：
```html
	<audio|video ontimeupdate="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("timeupdate", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `volumechange` (所有浏览器支持)
当音量已更改时，会发生 `volumechange` 事件，一般用来更新指示器。

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onvolumechange=alert("音量已变化");
```
此外还可以在标签中定义使用，例如：
```html 
	<audio|video onvolumechange="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("volumechange", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
#### `waiting` (所有浏览器支持)
当视频由于需要缓冲下一帧而停止，会发生 `waiting` 事件。此时`readyState`属性要小于等于`HAVE_CURRENT_DATA`,`paused`属性为`false`。

应用示例：
```js
	myVid=document.getElementById("video1");
	myVid.onwaiting=alert("等待接下来的数据");
```
此外还可以在标签中定义使用，例如：
```html
	<audio|video onwaiting="SomeJavaScriptCode">
```
采用`addEventListener()`添加事件处理方式：
```js 
	audio|video.addEventListener("waiting", 	function(){
  			//SomeJavaScriptCode
  		}
	);
```
