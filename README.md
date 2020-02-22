# SimplePlayer
跨平台音视频流媒体播放器

更新地址：

https://github.com/bluesky1982/SimplePlayer.git


c++实现，linux、windows系统，vs、Qt Creator调试。ffmpeg、Qt、SDL三方库。

读线程读取到AVPacket后push到视频/音频/字幕Packet队列。

视频线程从视频Packet队列取Packet并解码，然后将视频帧数据push到视频帧信息队列。

音频线程从音频Packet队列取Packet并解码，声音增益，然后送往声音设备外放。 

字幕线程从字幕Packet队列取Packet并解码，然后将字幕数据push到字幕信息队列。目前只支持ass字幕流。

UI主线程定时从视频帧信息队列中取视频帧信息，然后渲染到窗口。从字幕信息队列取字幕信息，然后渲染到窗口。

以音频为参照，通过pts和系统时间实现音视频同步。

从各种渠道获取大量的各种格式的音视频，进行了长期的本地播放测试。

获取YUV和PCM数据、编写代码、调整参数、编码封装后，进行了播放测试。

用一些公开的流媒体直播/点播地址进行了长期测试。

使用LVS、Keepalived、nginx搭建了流媒体服务端，进行了播放测试。

