# Stream Video và Gửi qua RTMP

```
gst-launch-1.0 videotestsrc !  'video/x-raw, format=(string)I420, width=(int)640,  height=(int)480' ! omxvp8enc ! matroskamux !  filesink location=test.mkv -e
```

lấy video từ camera

```bash
gst-launch-1.0 nvarguscamerasrc ! 'video/x-raw(memory:NVMM), width=1920, height=1080, format=NV12, framerate=30/1' ! nvoverlaysink
```

Stream tại jetson nano:

Gửi cả video

```bash
gst-launch-1.0 -v videotestsrc ! 'video/x-raw, width=1920, height=1080, framerate=30/1' ! omxh265enc ! 'video/x-h265, profile=baseline' ! flvmux ! rtmpsink location='rtmp://192.168.1.3:1935/live/test110 live=1'
```  


https://github.com/q191201771/lal/blob/master/app/demo/pushrtmp/pushrtmp.go


```
gst-launch-1.0 nvarguscamerasrc ! 'video/x-raw(memory:NVMM), width=1280, height=720, framerate=30/1, format=NV12' ! nvvidconv ! 'video/x-raw, width=640, height=480' ! nvvidconv ! omxh264enc control-rate=2 bitrate=4000000 ! 'video/x-h264, stream-format=(string)byte-stream' ! h264parse ! flvmux ! rtmpsink location="" ```