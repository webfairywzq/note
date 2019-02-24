HTML5————视频和音频

1. 参考网址：

   - http://caniuse.com
   - http://developer.mozilla.org

2. 属性：

   - autoplay：  chrome不能自动播放

     在chrome浏览器中输入chrome：//flags/#autoplay-policy。然后在高亮的选项中，将default换成“No user gesture is required”

   - preload：起作用的前提是不能有 autoplay  ，有三个属性值：

     1. none：不会提前加载任何信息
     2. ==meta==：预先加载视频的元信息，如：时长，但是视频本身的播放资源信息并没有加载（推荐使用）
     3. auto：会自动的提前加载视频的所有信息（元信息，本身资源信息）

3. 自定义播放控件相关API：

   - video.webkitRequestFullScreen() : 全屏
   - video.paused : 布尔值，是否暂停
   - video.play() : 播放
   - video.pause() : 暂停
   - 事件：timeupdata : 当前播放位置发生改变时产生该事件
   - video.currentTime : 当前播放的时间，单位：秒
   - video.duration : 返回总时间，单位：秒
   - video.muted : 布尔值，是否静音
   - video.volume : 设置音量

4. 标签：

   - 视频标签：

     <video width="320" height="240" controls="controls">
         <source src="movie.ogg" type="video.ogg">
     </video>

     - 音频标签

       <audio src="好久不见.mp3" autoplay controls>
           
       </audio>
