#hmtl5教程
##1.音频/视频 audio/video
    <audio src="新品资源路径" controls="controls" id="player"></audio>

controls="controls"属性：显示添加播放、暂停和音量按钮

autoplay="autoplay"属性：音频就绪后马上播放

loop="loop"属性：每当音频结束时，就会重新开始播放

preload属性：音频在页面加载时就会进行加载，并预备播放，如果使用了autoplay属，则忽略该属性。

播放器的dom对象获取方法
	
	var player = document.getElementById("player");
	或者
	var player = $("#player")[0]

css属性：

	animation-play-state：paused/running规定动画是正在运行还是停止
	tabindex:使用tab键时，元素选中的顺序由该属性的值指定的（1是第一个）
	duration:audio的属性 返回单钱音频/视频的长度，以秒计，如果为设置
				  则返回NaN  获取方式：audio|videodom对象.duration
	currentTime:设置或者返回音频/视频播放的当前位置（以s计）
	paused:返回audio/video的播放状态， true：暂停 false :播放

audio/video的方法

   	play():开始播放当前的音频或者视频（播放器的dom对象方法）
	pause():停止当前的音频或者视频
	load():重新加载音频/视频元素
	canPlayType():检测浏览器是都能播放不同类型的视频，返回为空则是不支持

思路：

1.点击播放按钮的时候，图片开始转动，进度条开始滑动

*  1-1 通过animation transtorm图片转动的效果
*  1-2 通过调用uijs的slider方法，来设置进度条的位置
*  1-3定义个定时器setInterval，每个0.5s，重设获取audio的进度，来设置进度条的位置
*  1-4. 通过audio的currentTime获取当前音频的播放位置

2.点击停止的时候，图片停止转动，进度条停止滑动

* 2-1 通过animation-play-state：paused停止图片的动画效果
* 2-2 clearInterval() 停止定时器

3.停止播放：

*  3-1通过设置图片元素的animation-play-state属性为paused停止转动，
*  3-2通过设置audio的currentTime属性将音频的播放位置还原，
*  3-3通过silder设置进度条的位置为0
