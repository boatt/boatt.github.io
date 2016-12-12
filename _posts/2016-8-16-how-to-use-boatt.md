---
layout: post
title: 二维码相关
tags:
- android
categories: boatt
description: 二维码相关.
---
### 二维码相关



<!-- more -->
## 日志详情

先说生成

` ``public` `Bitmap createQRImage(String url) {`

`        ``try` `{`

`            ``// 判断URL合法性`

`            ``if` `(url == ``null` `|| ``""``.equals(url) || url.length() < ``1``) {`

`                ``return` `null``;`

`            ``}`

`            ``Hashtable hints = ``new` `Hashtable();`

`            ``hints.put(EncodeHintType.CHARACTER_SET, ``"utf-8"``);`

`            ``// 图像数据转换，使用了矩阵转换`

`//            BitMatrix bitMatrix = new MultiFormatWriter().encode(new String(url.getBytes("GBK"),"ISO-8859-1"),BarcodeFormat.QR_CODE, 300, 300);`

`            ``BitMatrix bitMatrix = ``new` `QRCodeWriter().encode(url,BarcodeFormat.QR_CODE, QR_WIDTH, QR_HEIGHT);`

`            ``int``[] pixels = ``new` `int``[QR_WIDTH * QR_HEIGHT];`

`            ``// 下面这里按照二维码的算法，逐个生成二维码的图片，`

`            ``// 两个for循环是图片横列扫描的结果`

`            ``for` `(``int` `y = ``0``; y < QR_HEIGHT; y++) {`

`                ``for` `(``int` `x = ``0``; x < QR_WIDTH; x++) {`

`                    ``if` `(bitMatrix.get(x, y)) {`

`                        ``pixels[y * QR_WIDTH + x] = ``0xff000000``;`

`                    ``} ``else` `{`

`                        ``pixels[y * QR_WIDTH + x] = ``0xffffffff``;`

`                    ``}`

`                ``}`

`            ``}`

`            ``// 生成二维码图片的格式，使用ARGB_8888`

`            ``Bitmap bitmap = Bitmap.createBitmap(QR_WIDTH, QR_HEIGHT,Bitmap.Config.ARGB_8888);`

`            ``bitmap.setPixels(pixels, ``0``, QR_WIDTH, ``0``, ``0``, QR_WIDTH, QR_HEIGHT);`

`            ``return` `bitmap;`

`        ``} ``catch` `(Exception e) {`

`            ``e.printStackTrace();`

`        ``}`

`        ``return` `null``;`

`    ``}`

根据上面的方法就能生成一个对应的二维码bitmap

再说说修改二维码的边框

`修改com.zxing.camera.CameraManager的getFramingRect()方法`

 

 

 

 

`public` `Rect getFramingRect() {`

`    ``Point screenResolution = configManager.getScreenResolution();`

`    ``if` `(framingRect == ``null``) {`

`      ``if` `(camera == ``null``) {`

`        ``return` `null``;`

`      ``}`

`      ``//修改二维码边框大小`

`      ``int` `width = screenResolution.x * ``3``/``4``;`

`//      if (width < MIN_FRAME_WIDTH) {`

`//        width = MIN_FRAME_WIDTH;`

`//      } `

`//      else if (width > MAX_FRAME_WIDTH) {`

`//        width = MAX_FRAME_WIDTH;`

`//      }`

`      ``int` `height = screenResolution.y * ``3``/``4``;`

`      ` 

`//      if (height < MIN_FRAME_HEIGHT) {`

`//        height = MIN_FRAME_HEIGHT;`

`//      } `

`//      else if (height > MAX_FRAME_HEIGHT) {`

`//        height = MAX_FRAME_HEIGHT;`

`//      }`

`      ` 

`      ``if``(width > height){`

`          ``width = height;`

`      ``}`

`      ``if``(height > width){`

`          ``height = width;`

`      ``}`

`      ` 

`      ``//修改二维码扫面边框大小`

`      ``int` `leftOffset = (screenResolution.x - width) / ``2``;`

`      ``int` `topOffset = (screenResolution.y - height) / ``2``;`

`      ``framingRect = ``new` `Rect(leftOffset, topOffset, leftOffset + width, topOffset + height);`

`      ``Log.d(TAG, ``"Calculated framing rect: "` `+ framingRect);`

`    ``}`

`    ``return` `framingRect;`

`  ``}`

在就是修改二维码的边框

修改 zxing.view.ViewfinderView这个类里面onDraw()方法

接下来就是扫描二维码了,其实就是调用

 `// 扫码操作`

`        ``Intent intent = ``new` `Intent(``this``, CaptureActivity.``class``);`

`        ``startActivityForResult(intent, ``0``);`

`        ` 

`        ` 

`    ``@Override`

`    ``protected` `void` `onActivityResult(``int` `requestCode, ``int` `resultCode, Intent data) {`

`        ``super``.onActivityResult(requestCode, resultCode, data);`

`        ``if` `(resultCode == Activity.RESULT_OK) {`

`            ``String randnumber = data.getExtras().getString(``"result"``);`

`            ``String username = etUsername.getText().toString();`

`            ``String url = WEB_URL + ``"saveUsername.php?randnumber="` `+ randnumber`

`                    ``+ ``"&username="` `+ username;`

`            ``//访问url`

`            ``HttpUtils.login(url);`

`        ``}`

`    ``}`

资源地址

http://b3a4a.com/zb_users/upload/2015/08/201508031438587753810341.rar


