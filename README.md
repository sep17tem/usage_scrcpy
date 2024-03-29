scrcpy的使用方法

1.将文件夹路径添加到系统环境变量的Path中

2.无论有线还是无线链接方法：创建一个.bat文件，然后输入表示自动打开cmd然后键入scrcpy命令并执行

3.指令：

3.1禁用音频：scrcpy --no-audio

3.2无线连接：先用usb连接，然后scrcpy –tcpip可以自动找到设备的IP地址和adb端口并连接到设备
或者是
在文件夹按shift+右键打开powershell或cmd，然后依次输入下列指令即可
![输入图片说明](%E5%9B%BE%E7%89%872.jpg)
其中TCPIP和端口不一定是5555，可以查看手机知道端口号

3.3只读：scrcpy --no-control或scrcpy -n

3.4复制粘贴：ctrl+c复制/+x剪切/+v复制。任何Android程序都可以读取该内容

3.5模拟缩放：crtl+鼠标左键

3.6默认鼠标右键返回，中键主页面，禁用两项功能可选scrcpy --forward-all-clicks

3.7安装apk：直接拖入窗口就行

3.8传输文件默认放在/download文件夹内，修改拖拽文件保存位置：scrcpy --push-target=/sdcard/Movies/

3.9防止休眠：scrcpy -w，无线连接无效

3.10连接后关闭屏幕：-S

3.11打开虚拟键盘，方便打字：Android14不起作用

--keyboard=sdk 

--keyboard=uhid 

--keyboard=aoa  

3.12镜像时录制音频和视频：

scrcpy --record=file.mp4

scrcpy -r file.mkv

3.12.1只录制视频：scrcpy --no-audio --record=file.mp4

3.12.2只录制音频：

scrcpy --no-video --record=file.opus

scrcpy --no-video --audio-codec=aac --record=file.aac

scrcpy --no-video --audio-codec=flac --record=file.flac

scrcpy --no-video --audio-codec=raw --record=file.wav

# .m4a/.mp4 and .mka/.mkv are also supported for opus, aac and flac

3.13快捷键：默认是左Alt或左Super

切换全屏：f

屏幕左/右转：←/→

窗口调整为1:1：g

解锁屏幕：m

调节音量;↑/↓

关闭屏幕但保持镜像：o，Android14不起作用

打开：shift+o

修改快捷键：scrcpy --shortcut-mod=rctrl

3.14调节分辨率：默认是手机分辨率

scrcpy -m 1024/1920


3.15视频比特率：默认8M

scrcpy -b 2M

3.16帧率：

scrcpy --max-fps=15

3.17选择视频解码器：默认h264，延迟低，h265质量好但延迟高，av1不常见

scrcpy --video-codec=h265或av1

3.18指定镜像窗口出现的位置和大小:

scrcpy --window-x=0 --window-y=100 --window-width=400 --window-height=900

这个位置和尺寸比较好

--window-x=-1050 --window-y=700 --window-width=400 --window-height=900

这个位置出现在左侧竖屏的左下角

--window-x=-1050 --window-y=0 --window-width=400 --window-height=900

这个则是左上角

3.19让镜像窗口永远在顶部：

scrcpy --window-borderless

3.20选择usb(-d)或tcpip(-e)：scrcpy -d/-e
3.21关闭无线tcpip连接：adb disconnect
