scrcpy的使用方法

（源代码见https://github.com/Genymobile/scrcpy ）

1.无论有线还是无线链接方法：将目录内名为‘scrcpy-console’的bat文件复制一下，在新的bat文件中键入（快捷指令）
scrcpy --video-codec=h265 --max-size=1920 --max-fps=60 --no-audio --keyboard=uhid --window-x=0 --window-y=100 --window-width=400 --window-height=900
![输入图片说明](图片1.png)，表示自动打开cmd然后键入scrcpy命令并执行，这串快捷指令代表‘关闭音频转换’、‘将镜像放在主显示屏最左侧’等

2.在Android的开发人员选项中打开‘USB调试’并关闭‘通过USB验证应用’，然后将‘USB连接方式’调整为‘传输文件’，再启动bat文件，等待一段时间激活安全验证。有时候不提示激活，还需要将‘选择USB配置’切换为‘音频来源’以激活验证。

3.指令：

3.1禁用音频：scrcpy --no-audio

3.2无线连接：打开手机端的无线调试功能，先用usb连接，然后在.bat文件键入![输入图片说明](Picture2.png)即可，主要是修改手机IP地址就行,此外务必确保USB调试是开启的，最好打开"仅充电"，否则USB调试容易自动关闭。还有一种可能是无论如何都不能无线连接，那么就老老实实地用USB有线连接。
  
3.3只读：scrcpy --no-control或scrcpy -n

3.4复制粘贴：ctrl+c复制/+x剪切/+v复制。任何Android程序都可以读取该内容

3.5模拟缩放：crtl+鼠标左键

3.6默认鼠标右键返回，中键主页面，禁用两项功能可选scrcpy --forward-all-clicks

3.7安装apk：直接拖入窗口就行

3.8传输文件默认放在/download文件夹内，修改文件保存位置可以使用命令：scrcpy --push-target=/sdcard/Movies/

3.9防止休眠：scrcpy -w 或 scrcpy --stay-awake，无线连接无效

3.10连接后关闭屏幕：-S 或--turn-screen-off , 目前Android14用不了。可以直接用快捷键【alt+o】，重新打开则是【alt+shift+o】

3.11打开虚拟键盘，方便打字：Android14不起作用。有一种可能可行的解决方法：每次连接时复制粘贴一段文本到手机上，可以尝试打开虚拟键盘。

--keyboard=sdk 

--keyboard=uhid ，可以在ADB和OTG模式中使用

--keyboard=aoa ，在Windows中只能在OTG模式中使用

3.12镜像时录制音频和视频：

scrcpy --record=file.mp4

scrcpy -r file.mkv

3.12.1只录制视频：scrcpy --no-audio --record=file.mp4

3.12.2只录制音频：

scrcpy --no-video --record=file.opus

scrcpy --no-video --audio-codec=aac --record=file.aac

scrcpy --no-video --audio-codec=flac --record=file.flac

scrcpy --no-video --audio-codec=raw --record=file.wav


3.13快捷键：下面指令全部需要加上控制键，默认是左Alt或左Super ，修改快捷键--shortcut-mod=rctrl或lctrl+lalt ，可行的快捷键包括lctrl, rctrl, lalt, ralt, lsuper and rsuper

切换全屏：f

屏幕左/右转：←/→

窗口调整为1:1：g ，不要随意使用

解锁屏幕：m

调节音量：↑/↓

关闭屏幕但保持镜像：o，Android14不起作用

打开：shift+o ， Android14无效

修改快捷键：scrcpy --shortcut-mod=rctrl

模拟电源键：p ， 按一下代表锁屏

3.14调节分辨率：默认是手机分辨率

scrcpy -m 1024/1920


3.15视频比特率：默认8M

scrcpy -b 2M

3.16帧率：

scrcpy --max-fps=15

3.17选择视频解码器：默认h264，延迟低，h265质量好但延迟高，av1不常见

scrcpy --video-codec=h265或av1

3.18指定镜像窗口出现的位置和大小:以主显示器的左上角为坐标原点设置镜像窗口的位置，右侧为正X轴，下侧为正Y轴

例如：scrcpy --window-x=0 --window-y=100 --window-width=400 --window-height=900 若觉得宽高不合适可以用鼠标拖动镜像窗口或者将参数值进行等比例缩放即可


3.19让镜像窗口永远在顶部：

scrcpy --window-borderless

3.20改变拖拽文件保存位置：

scrcpy --push-target=/sdcard/Movies/

3.21关闭scrcpy的同时关闭手机屏幕： scrcpy --power-off-on-close

4. scrcpy --otg: 打开OTG模式，连接电脑的鼠标和键盘直接映射到手机上，此时不需要adb

