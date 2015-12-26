# lf.swift
iOS向けライブ配信用のライブラリーです。現在、RTMPでの配信をサポートしています。映像および音声の再生についてはサポートしていません。

## ライセンス
修正BSDで公開しています。

## 簡単な説明
### RTMP
api自体はAS3のNetConnectionとNetStreamに似せています。
* flash.net.SharedObject → RTMPSharedObject
* flash.net.Responder → Responder
* flash.net.NetConnection → RTMPConnection
* flash.net.NetStream → RTMPStream
* AMF0をサポート、AMF3はこれからサポート予定
```swift
var rtmpConnection:RTMPConnection = RTMPConnection()
var rtmpStream = RTMPStream(rtmpConnection: rtmpConnection)
rtmpStream.videoGravity = AVLayerVideoGravityResizeAspectFill
rtmpStream.attachAudio(AVCaptureDevice.defaultDeviceWithMediaType(AVMediaTypeAudio))
rtmpStream.attachCamera(AVCaptureDevice.defaultDeviceWithMediaType(AVMediaTypeVideo))

view.addSubview(rtmpStream.view)
rtmpConnection.connect("rtmp://localhost/appName/instanceName")
rtmpStream.publish("streamName")
```

## 参考文献
* Adobe’s Real Time Messaging Protocol
 * http://www.adobe.com/content/dam/Adobe/en/devnet/rtmp/pdf/rtmp_specification_1.0.pdf
* Action Message Format -- AMF 0
 * http://wwwimages.adobe.com/content/dam/Adobe/en/devnet/amf/pdf/amf0-file-format-specification.pdf
* Action Message Format -- AMF 3 
 * http://wwwimages.adobe.com/www.adobe.com/content/dam/Adobe/en/devnet/amf/pdf/amf-file-format-spec.pdf
