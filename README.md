# Midjourney Imagine API 申请及使用

Midjourney 是一款非常强大的 AI 绘图工具，只要输入关键字，就能在短短一两分钟生成十分精美的图像。Midjourney 以其出色的绘图能力在业界独树一帜，如今，Midjourney 早已在各个行业和领域广泛应用，其影响力愈发显著。

本文档主要介绍 Midjourney API 中 Imagine 操作的使用流程，利用它我们可以轻松通过文本生成所需要的图像。

## 申请流程

要使用 Midjourney Imagine API，首先可以到 [Midjourney Imagine API](https://platform.acedata.cloud/documents/e52c028d-897a-4d51-b110-60fccbe6118d "Midjourney Imagine API") 页面点击「Acquire」按钮，获取请求所需要的凭证：

![](https://cdn.acedata.cloud/nyq0xz.png)

如果你尚未登录或注册，会自动跳转到登录页面邀请您来注册和登录，登录注册之后会自动返回当前页面。

在首次申请时会有免费额度赠送，可以免费使用该 API。

## 基本使用

接下来就可以在界面上填写对应的内容，如图所示：

![](https://cdn.acedata.cloud/d01h9f.png)

在第一次使用该接口时，我们至少需要填写两个内容，一个是 `authorization`，直接在下拉列表里面选择即可。另一个参数是 `prompt`， `prompt` 就是我们想生成的图片描述内容，建议用英文描述，画的图会更准确效果更好，这里我们用了示例内容 `Lamborghini speeds inside a volcano`，代表要画一个兰博基尼在火山飞驰。

同时您可以注意到右侧有对应的调用代码生成，您可以复制代码直接运行，也可以直接点击「Try」按钮进行测试。

![](https://cdn.acedata.cloud/zv3db5.png)

调用之后，我们发现返回结果如下：

```json
{
  "image_url": "https://midjourney.cdn.acedata.cloud/attachments/1233387694839697411/1234197197067915365/36rgqit64j90qptsxnyq_Lamborghini_speeds_inside_a_volcano_id0494_f47263b6-ff92-44a3-88ee-51cf0e706aae.png?ex=662fdb36&is=662e89b6&hm=ca9be54907726937ed02517a13466bef2afb2825b7cda4b313de56a3c3310d0d&width=1024&height=1024",
  "image_width": 1024,
  "image_height": 1024,
  "image_id": "1234197197067915365",
  "raw_image_url": "https://midjourney.cdn.acedata.cloud/attachments/1233387694839697411/1234197197067915365/36rgqit64j90qptsxnyq_Lamborghini_speeds_inside_a_volcano_id0494_f47263b6-ff92-44a3-88ee-51cf0e706aae.png?ex=662fdb36&is=662e89b6&hm=ca9be54907726937ed02517a13466bef2afb2825b7cda4b313de56a3c3310d0d&",
  "raw_image_width": 2048,
  "raw_image_height": 2048,
  "progress": 100,
  "actions": [
    "upscale1",
    "upscale2",
    "upscale3",
    "upscale4",
    "reroll",
    "variation1",
    "variation2",
    "variation3",
    "variation4"
  ],
  "task_id": "1bae3bec-3ac4-4180-a148-74ee6cb68b98",
  "success": true
}
```

返回结果一共有多个字段，介绍如下：

- `task_id`，生成此图像任务的 ID，用于唯一标识此次图像生成任务。
- `image_id`，图片的唯一标识，在下次需要对图片进行变换操作时需要传此参数。
- `image_url`，缩略图的 URL，直接打开即可查看生成的效果。
- `image_width`：缩略图的像素宽度。
- `image_height`：缩略图的像素高度。
- `raw_image_url`：原图的 URL，和缩略图内容一样，但相比缩略图更加高清，加载速度会更慢一些。
- `raw_image_width`：原图的像素宽度。
- `raw_image_height`：原图的像素高度。
- `actions`，可以对生成的图片进行的进一步操作列表。这里一共列了 8 个，其中 `upscale` 代表放大，`variation` 代表变换。所以 `upscale1` 代表的就是对左上角第一张图片进行放大操作，`variation3` 就是代表根据左下角第三张图片进行变换操作。

打开 `image_url` 或者 `raw_image_url` 所对应的链接，可以发现如图所示。

![](https://cdn.acedata.cloud/qr2iyj.png)

可以看到，这里生成了一张 2x2 的预览图。到现在为止，第一次 API 调用就完成了。

## 图像放大与变换

下面我们尝试针对当前生成的照片进行进一步的操作，比如我们觉得右上角第二张的图片还不错，但我们想进行一些变换微调，那么就可以进一步将 `action` 填写为 `variation2`，同时将 `image_id` 传递即可：

![](https://cdn.acedata.cloud/ia7vpw.png)

这时候得到的结果如下：

```json
{
  "image_url": "https://midjourney.cdn.acedata.cloud/attachments/1233387694839697411/1234201336543969401/36rgqit64j90qptsxnyq_Lamborghini_speeds_inside_a_volcano_id0494_10dc56a7-ec16-4bac-878e-2338f2ae5f5d.png?ex=662fdf10&is=662e8d90&hm=9aec96bca35ae20b6f9ab536101b9c4ea255eb6216cbf7000ac554937da071f3&width=1024&height=1024",
  "image_width": 1024,
  "image_height": 1024,
  "image_id": "1234201336543969401",
  "raw_image_url": "https://midjourney.cdn.acedata.cloud/attachments/1233387694839697411/1234201336543969401/36rgqit64j90qptsxnyq_Lamborghini_speeds_inside_a_volcano_id0494_10dc56a7-ec16-4bac-878e-2338f2ae5f5d.png?ex=662fdf10&is=662e8d90&hm=9aec96bca35ae20b6f9ab536101b9c4ea255eb6216cbf7000ac554937da071f3&",
  "raw_image_width": 2048,
  "raw_image_height": 2048,
  "progress": 100,
  "actions": [
    "upscale1",
    "upscale2",
    "upscale3",
    "upscale4",
    "reroll",
    "variation1",
    "variation2",
    "variation3",
    "variation4"
  ],
  "task_id": "f4961620-1104-409f-9dc1-ba3ed15c2f4d",
  "success": true
}
```

打开 `image_url`，新生成的图片如下所示：

![](https://cdn.acedata.cloud/4g6r09.png)

可以看到，针对上一张右上角的图片，我们再次得到了四张类似的照片。

这时候我们可以挑选其中一张进行精细化地放大操作，比如选第四张，那就可以 `action` 传入 `upscale4`，通过 `image_id` 再次传入当前图像的 ID 即可。

![](https://cdn.acedata.cloud/jk9ohl.png)

> 注意： `upscale` 操作相比 `variation` 来说，Midjourney 的耗时会更短一些。

返回结果如下：

```json
{
  "image_url": "https://midjourney.cdn.acedata.cloud/attachments/1233387694839697411/1234202545208033400/36rgqit64j90qptsxnyq_Lamborghini_speeds_inside_a_volcano_id0494_34edc3f5-2bd0-4f5b-a372-03270b02289b.png?ex=662fe031&is=662e8eb1&hm=f8006c4d33a03dfd027dffe4eb46ab0d113a4910aef07497f0b335c8998b7858&width=512&height=512",
  "image_width": 512,
  "image_height": 512,
  "image_id": "1234202545208033400",
  "raw_image_url": "https://midjourney.cdn.acedata.cloud/attachments/1233387694839697411/1234202545208033400/36rgqit64j90qptsxnyq_Lamborghini_speeds_inside_a_volcano_id0494_34edc3f5-2bd0-4f5b-a372-03270b02289b.png?ex=662fe031&is=662e8eb1&hm=f8006c4d33a03dfd027dffe4eb46ab0d113a4910aef07497f0b335c8998b7858&",
  "raw_image_width": 1024,
  "raw_image_height": 1024,
  "progress": 100,
  "actions": [
    "upscale_2x",
    "upscale_4x",
    "variation_subtle",
    "variation_strong",
    "zoom_out_2x",
    "zoom_out_1_5x",
    "pan_left",
    "pan_right",
    "pan_up",
    "pan_down"
  ],
  "task_id": "03f62b17-a6f1-4c8e-9b4d-1fc7bd5b1180",
  "success": true
}
```

其中 `image_url` 如图所示：

![](https://cdn.acedata.cloud/jfndfo.png)

这样我们就成功得到了一张兰博基尼的照片。

同时注意到 `actions` 里面又包含了几个可进行的操作，介绍如下：

- `upscale_2x`：对画面放大 2 倍，得到 2 倍高清图。
- `upscale_4x`：对画面放大 4 倍，得到 4 倍高清图。
- `zoom_out_2x`：对画面进行缩小两倍操作（周围区域填充）。
- `zoom_out_1_5x`：对画面进行缩小 1.5 倍操作（周围区域填充）。
- `pan_left`：对画面进行左偏移操作。
- `pan_right`：对画面进行右便宜操作。
- `pan_up`：对画面进行上偏移操作。
- `pan_down`：对画面进行下偏移操作。

可以继续按照上述流程传入对应的变换指令进行连续生图操作。

## 图像改写（垫图）

该 API 也支持图像改写，俗称垫图，我们可以输入一张图片 URL 以及需要改写的描述文字，该 API 就可以返回改写后的图片。

> 注意：输入的图片 URL 需要是一张纯图片，不能是一个网页里面展示一张图片，否则无法进行图像改写。建议使用图床来上传获取图片的 URL。

例如，我们这里有一张公路落日的图片，公路旁边有一些树木和楼房，如图所示：

![](https://cdn.acedata.cloud/mq335u.png)

现在我们想在它的基础上改写成海滩旁边，同时放一辆汽车停在路边。我们就可以构造如下的 prompt：

```bash
https://cdn.acedata.cloud/v014oc.png an illustration of a car parked on the beach --iw 2
```

可以看到，我们的 prompt 的最开头是一个 HTTPS 开头的图片链接，然后接着加一个空格，后面跟上 prompt 文字的内容。这里我们还用了额外的一些高级参数，如 `—iw 2` 来调整图片的权重。

我们可以将如上内容作为一个整体，传递给 `prompt` 字段，如图所示：

![](https://cdn.acedata.cloud/pfcoy1.png)

输出结果如下：

```bash
{
  "image_url": "https://midjourney.cdn.acedata.cloud/attachments/1234427310434947145/1234539663515975690/atmateosa5693_An_illustration_of_a_car_parked_on_the_beach_id26_cc8650ec-7e4b-4685-8911-78172430d8a7.png?ex=66311a28&is=662fc8a8&hm=c39707a1f22bc7f12874060ea6ed58ba37c188139ccc9a13c61ed9f37e66ea74&width=1456&height=816",
  "image_width": 1456,
  "image_height": 816,
  "image_id": "1234539663515975690",
  "raw_image_url": "https://midjourney.cdn.acedata.cloud/attachments/1234427310434947145/1234539663515975690/atmateosa5693_An_illustration_of_a_car_parked_on_the_beach_id26_cc8650ec-7e4b-4685-8911-78172430d8a7.png?ex=66311a28&is=662fc8a8&hm=c39707a1f22bc7f12874060ea6ed58ba37c188139ccc9a13c61ed9f37e66ea74&",
  "raw_image_width": 2912,
  "raw_image_height": 1632,
  "progress": 100,
  "actions": [
    "upscale1",
    "upscale2",
    "upscale3",
    "upscale4",
    "reroll",
    "variation1",
    "variation2",
    "variation3",
    "variation4"
  ],
  "task_id": "24a79e8b-a79d-471a-aef7-089dc0627ee8",
  "success": true
}

```

这时候我们就得到了如下生成的图片：

![](https://cdn.acedata.cloud/1vwkuv.png)

可以看到，在原来的图片整体风格和构图不变的前提下，整个场景变成了海滩旁边，同时公路上还出现了汽车，这就是 Prompt with Image。

## 图像融合

该 API 也支持图像融合，我们可以传入多张图片，以实现不同的图片融合效果。

比如说这里我们一共有两张图片，一张是一只玩具熊，另一张是一个电锯，分别如图所示：

<p><img src="https://cdn.acedata.cloud/8fapzl.png" width="300" class="m-auto"></p>

<p><img src="https://cdn.acedata.cloud/c1igbw.png" width="300" class="m-auto"></p>

现在我们想把二者融合起来，让这只熊拿着这个电锯，怎么做呢？

我们可以构造如下的 prompt：

```bash
https://cdn.acedata.cloud/8fapzl.png https://cdn.acedata.cloud/c1igbw.png The bear is holding the chainsaw --iw 2
```

可以发现，和 Image with Prompt 类似，我们这里将多张图片 URL 放在了 prompt 开头，并以空格分隔，最后再加上文字 prompt，将如上内容作为一个整体传递给 `prompt` 参数，运行效果如下：

```bash
{
  "image_url": "https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234547236830973972/kcisok_The_bear_is_holding_the_chainsaw_id8873344_ad605bc4-ba19-4807-b94f-367dab672f7a.png?ex=66312136&is=662fcfb6&hm=0fb1e2261c9a30b04de9da9b23b7562eb73677f1bbda1fae52c7243b12d25aac&width=1024&height=1024",
  "image_width": 1024,
  "image_height": 1024,
  "image_id": "1234547236830973972",
  "raw_image_url": "https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234547236830973972/kcisok_The_bear_is_holding_the_chainsaw_id8873344_ad605bc4-ba19-4807-b94f-367dab672f7a.png?ex=66312136&is=662fcfb6&hm=0fb1e2261c9a30b04de9da9b23b7562eb73677f1bbda1fae52c7243b12d25aac&",
  "raw_image_width": 2048,
  "raw_image_height": 2048,
  "progress": 100,
  "actions": [
    "upscale1",
    "upscale2",
    "upscale3",
    "upscale4",
    "reroll",
    "variation1",
    "variation2",
    "variation3",
    "variation4"
  ],
  "task_id": "891f2645-ee15-4c7b-ac24-d98163c8e57e",
  "success": true
}

```

我们就得到了如下结果：

![](https://cdn.acedata.cloud/vjtzdo.png)

可以看到，我们就成功实现了图片融合。

> 注意：图片融合最多可以支持 5 个图片 URL 作为输入，也就是最多支持 5 张图片融合，输入格式同上。

## 局部变换

该 API 也支持图像的局部绘图功能，但只支持在上文内容下生成的图片，我们可以传入一张生成图片的的唯一ID，局部重绘的行为参数 `action` 以及需要重绘区域的掩码mask，以实现在改掩码区域进行重绘。

比如说这里我们有一张生成关于猫的图片：

<p><img src="https://platform.cdn.acedata.cloud/midjourney/487c5e16-0ad5-4d7e-9e64-3122e366317e.png?imageMogr2/thumbnail/!50p" width="300" class="m-auto"></p>


现在我们想对这个猫脸进行重绘，怎么做呢？

首先我们需要获取该区域的掩码mask，此mask是通过灰度图片进行Base64编码得来的，下面提供一些获取掩码的工具代码：

Python获取掩码示例代码：

```python
import sys
import os
from PySide6.QtWidgets import *
from PySide6.QtGui import QPainter, QMouseEvent, QPen, QColor, QImage
from PySide6.QtCore import Qt, QPoint

class DrawingWidget(QWidget):
    def __init__(self, imagePath):
        super().__init__()
        self.setAttribute(Qt.WA_StaticContents)
        self.background_image = QImage(imagePath)
        imageSize = self.background_image.size()*0.8
        self.setFixedSize(imageSize)
        self.foreground_image = QImage(self.size(), QImage.Format_ARGB32)
        self.foreground_image.fill(Qt.transparent)
        self.drawing = False
        self.lastPoint = QPoint()
        self.pen_color = QColor(255, 255, 255, 255)
        self.pen_size = 50

    def set_pen_size(self, size):
        self.pen_size = size

    def mousePressEvent(self, event: QMouseEvent):
        if event.button() == Qt.LeftButton:
            self.drawing = True
            self.lastPoint = event.pos()

    def mouseMoveEvent(self, event: QMouseEvent):
        if event.buttons() & Qt.LeftButton and self.drawing:
            painter = QPainter(self.foreground_image)
            painter.setRenderHint(QPainter.Antialiasing, True)
            pen = QPen(self.pen_color, self.pen_size,
                       Qt.SolidLine, Qt.RoundCap, Qt.RoundJoin)
            painter.setPen(pen)
            painter.drawLine(self.lastPoint, event.pos())
            self.lastPoint = event.pos()
            self.update()

    def mouseReleaseEvent(self, event: QMouseEvent):
        if event.button() == Qt.LeftButton and self.drawing:
            self.drawing = False

    def paintEvent(self, event):
        canvasPainter = QPainter(self)
        canvasPainter.drawImage(
            self.rect(), self.background_image, self.background_image.rect())
        canvasPainter.drawImage(
            self.rect(), self.foreground_image, self.foreground_image.rect())

    def save_image(self, path):
        self.foreground_image.save(path)

class MainWindow(QDialog):
    def __init__(self, imagePath):
        super().__init__()
        self.setWindowTitle("mask tool")
        self.drawing_widget = DrawingWidget(imagePath)
        self.currentPath = os.getcwd().replace("\\", "/")
        self.tempPath = self.currentPath + "/temp.jpg"
        self.projectPath = ""
        self.setDone = False

    def init_ui(self):
        layout = QVBoxLayout()
        layout.addWidget(self.drawing_widget)
        controls_layout = QHBoxLayout()
        size_label = QLabel("pen size:")
        controls_layout.addWidget(size_label)
        self.size_slider = QSlider(Qt.Horizontal)
        self.size_slider.setMinimum(100)
        self.size_slider.setMaximum(400)
        self.size_slider.setValue(400)
        self.size_slider.valueChanged.connect(self.update_pen_size)
        controls_layout.addWidget(self.size_slider)
        self.lineEdit_addPromp = QLineEdit()
        layout.addWidget(self.lineEdit_addPromp)
        save_button = QPushButton("   Start partial redrawing   ")
        save_button.clicked.connect(self.save_image)
        controls_layout.addWidget(save_button)
        dont_button = QPushButton("   Cancel partial redraw   ")
        dont_button.clicked.connect(self.dont_image)
        controls_layout.addWidget(dont_button)
        layout.addLayout(controls_layout)
        self.setLayout(layout)

    def update_pen_size(self):
        size = self.size_slider.value()
        self.drawing_widget.set_pen_size(size)

    def save_image(self):
        tempImage = self.currentPath + "/temp.jpg"
        self.drawing_widget.save_image(self.tempPath)
        self.prompt = self.lineEdit_addPromp.text()
        self.setDone = True
        self.close()

    def dont_image(self):
        self.setDone = False
        self.close()

    def closeEvent(self, event):
        if self.setDone:
            pass
        else:
            self.setDone = False
        event.accept()


if __name__ == '__main__':
    imagePath = "test.png"
    app = QApplication(sys.argv)
    mainWindow = MainWindow(imagePath)
    mainWindow.init_ui()
    mainWindow.exec()
```

通过以上代码可以获得掩码图片，在这个过程中我们需要注意掩码图片必须与原图片一样的尺寸，然后掩码图片中白色的区域就是需要重绘的区域，下面展示猫图片需要重绘的掩码图片与原图的对比：

原图片：
<p><img src="https://cdn.acedata.cloud/t1tdf9.png" width="300" class="m-auto"></p>

掩码图片：
<p><img src="https://cdn.acedata.cloud/bjnrra.png" width="300" class="m-auto"></p>

最后我们还需要将掩码图片转换为基于Base64的编码，接下来提供转换Base64编码的代码：

Python转换Base64示例代码：

```python
import cv2
import base64

image_path = 'temp.jpg'
gray_image = cv2.imread(image_path)
_, buffer = cv2.imencode('.jpg', gray_image)
base64_encoded = base64.b64encode(buffer).decode('utf-8')
with open('grayscale_image_base64.txt', 'w') as f:
    f.write(base64_encoded)

print("success!")
```

> 注意：上述 Python 代码描述了 mask 的生成过程，如果您要将其对接到您的产品中，请根据其原理编写对应语言的代码。


通过以上代码，我们获得了需要重绘的掩码 `mask` ，下面我们还需要需要将参数 `action` 设置为 `variation_region` ，生成图片的ID `image_id` （获取该参数参考上文的内容），以及传入对应的掩码 `mask` ，其它参数信息如下：

- `action`：对图片进行操作的行为，此处为 `variation_region` ，表示对图片进行局部重绘。
- `prompt`：对图像进行局部重绘的描述词（可选参数）。
- `image_id`：图片的唯一标识，方便对图像进行局部重绘。
- `mask`：图片对应的掩码区域的base64编码（图片是上面image_id指定的）。

因此根据以上规则我们需要设置正确的的参数，参数 `prompt` 是一个非必填参数，这里为了方便对比将掩码区域的 `prompt` 设置为 `A  cute cat` ，具体的参数设置如下图所示：

![](https://cdn.acedata.cloud/p0hwrf.png)

### 代码示例

可以发现，在页面右侧已经自动生成了各种语言的代码，如图所示：

![](https://cdn.acedata.cloud/1ttiuk.png)

部分代码示例如下：

#### CURL

```bash
curl -X POST 'https://api.acedata.cloud/midjourney/imagine' \
-H 'accept: application/json' \
-H 'authorization: Bearer {token}' \
-H 'content-type: application/json' \
-d '{
  "prompt": "A cute cat ",
  "action": "variation_region",
  "image_id": "1265875488702726144",
  "mask": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAGaAZoDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD+f+iiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKK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/GlvIP8ASbeP7T/on7yK7luDLH+//wAI/i58MPjn4Asfij8G/iVoPi/w3qjTf2f4h8M6vFqFhdGKaSKXybmEmKURyxyR5BPMZzzX8GFeu/sxftp/tX/sX+JD4v8A2Vv2iPFngS7mv7K91KLQdbkgtdSmtpDJa/bLb/U30cZeQeVcxyxYklGCJSCAf3P0V/Nn+zF/weiftb+APDh0H9qf9lLwn8S7uDTLGDT9a8Pa7L4cuZ5Yoitzc3o8m7hlkl/dy4toraKIiQeXiQCL03/iOaP/AEi9/wDM1/8A3loA/f8Aor8AP+I5o/8ASL3/AMzX/wDeWj/iOaP/AEi9/wDM1/8A3loA/f8Aor8AP+I5o/8ASL3/AMzX/wDeWj/iOaP/AEi9/wDM1/8A3loA/f8Aor8AP+I5o/8ASL3/AMzX/wDeWvlv9p3/AIO6P+Crnxj8U/b/AIFa74Q+EOiWmoXz2lh4d8MW2qXNxbSv/o0V9c6rHcxzSwxx4822itRKZJCY8eWIwD+qOiv5BP8AiKL/AOC6P/R8v/mM/DH/AMq6P+Iov/guj/0fL/5jPwx/8q6AP6+65L4ufFz4YfAzwBf/ABR+MnxK0Hwh4b0tof7Q8Q+JtXi0+wtTLNHFF51zMRFEJJZI48kjmQY5r+TH/iKL/wCC6P8A0fL/AOYz8Mf/ACrr5b/ad/bT/av/AG0PEg8X/tU/tEeLPHd3Df3t7psWva3JPa6bNcyCS6+x23+psY5CkY8q2jiixHEMARAAA/TT/g4F/wCDkbwr/wAFAvhvd/sSfsT6RqNr8ML2+Wbxz4u8SaSkdz4na0vvNtYbKNiZLWxMkFtc+bII7qUiKMx2wiljufxuoooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKAP/Z"
}'
```

#### Python

```python
import requests

url = "https://api.acedata.cloud/midjourney/imagine"

headers = {
    "accept": "application/json",
    "authorization": "Bearer {token}",
    "content-type": "application/json"
}

payload = {
    "prompt": "A  cute cat ",
    "action": "variation_region",
    "image_id": "1265875488702726144",
    "mask": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAIBAQEBAQIBAQECAgICAgQDAgICAgUEBAMEBgUGBgYFBgYGBwkIBgcJBwYGCAsICQoKCgoKBggLDAsKDAkKCgr/2wBDAQICAgICAgUDAwUKBwYHCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgoKCgr/wAARCAGaAZoDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD+f+iiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKK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/GlvIP8ASbeP7T/on7yK7luDLH+//wAI/i58MPjn4Asfij8G/iVoPi/w3qjTf2f4h8M6vFqFhdGKaSKXybmEmKURyxyR5BPMZzzX8GFeu/sxftp/tX/sX+JD4v8A2Vv2iPFngS7mv7K91KLQdbkgtdSmtpDJa/bLb/U30cZeQeVcxyxYklGCJSCAf3P0V/Nn+zF/weiftb+APDh0H9qf9lLwn8S7uDTLGDT9a8Pa7L4cuZ5Yoitzc3o8m7hlkl/dy4toraKIiQeXiQCL03/iOaP/AEi9/wDM1/8A3loA/f8Aor8AP+I5o/8ASL3/AMzX/wDeWj/iOaP/AEi9/wDM1/8A3loA/f8Aor8AP+I5o/8ASL3/AMzX/wDeWj/iOaP/AEi9/wDM1/8A3loA/f8Aor8AP+I5o/8ASL3/AMzX/wDeWvlv9p3/AIO6P+Crnxj8U/b/AIFa74Q+EOiWmoXz2lh4d8MW2qXNxbSv/o0V9c6rHcxzSwxx4822itRKZJCY8eWIwD+qOiv5BP8AiKL/AOC6P/R8v/mM/DH/AMq6P+Iov/guj/0fL/5jPwx/8q6AP6+65L4ufFz4YfAzwBf/ABR+MnxK0Hwh4b0tof7Q8Q+JtXi0+wtTLNHFF51zMRFEJJZI48kjmQY5r+TH/iKL/wCC6P8A0fL/AOYz8Mf/ACrr5b/ad/bT/av/AG0PEg8X/tU/tEeLPHd3Df3t7psWva3JPa6bNcyCS6+x23+psY5CkY8q2jiixHEMARAAA/TT/g4F/wCDkbwr/wAFAvhvd/sSfsT6RqNr8ML2+Wbxz4u8SaSkdz4na0vvNtYbKNiZLWxMkFtc+bII7qUiKMx2wiljufxuoooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKACiiigAooooAKKKKAP/Z"
}

response = requests.post(url, json=payload, headers=headers)
print(response.text)
```

### 响应示例

请求成功后，API 将返回换脸后端图片结果信息。例如：

```json
{
  "image_url": "https://platform.cdn.acedata.cloud/midjourney/6c9450d8-1c22-4f85-a527-e7a7bfb4a61b.png?imageMogr2/thumbnail/!50p",
  "image_width": 1024,
  "image_height": 1024,
  "actions": [
    "upscale1",
    "upscale2",
    "upscale3",
    "upscale4",
    "reroll",
    "variation1",
    "variation2",
    "variation3",
    "variation4"
  ],
  "raw_image_url": "https://platform.cdn.acedata.cloud/midjourney/6c9450d8-1c22-4f85-a527-e7a7bfb4a61b.png",
  "raw_image_width": 2048,
  "raw_image_height": 2048,
  "progress": 100,
  "image_id": "1265876571323891712",
  "task_id": "6c9450d8-1c22-4f85-a527-e7a7bfb4a61b",
  "success": true
}
```

可以发现这是对掩码区域的图像进行了重绘操作，返回的结果与上文的是一致的，结果如下图所示：

![](https://cdn.acedata.cloud/8vslhq.png)

可以看到，我们就成功实现了对生成的图片的自定义区域进行局部重绘。

## 异步回调

由于 Midjourney 生成图片需要等待一段时间，所以本 API 也默认设计为了长等待模式。但在部分场景下，长等待可能会带来一些额外的资源开销，因此本 API 也提供了异步 Webhook 回调的方式，当图片生成成功或失败时，其结果都会通过 HTTP 请求的方式发送到指定的 Webhook 回调 URL。回调 URL 接收到结果之后可以进行进一步的处理。

下面演示具体的调用流程。

首先，Webhook 回调是一个可以接收 HTTP 请求的服务，开发者应该替换为自己搭建的 HTTP 服务器的 URL。此处为了方便演示，使用一个公开的 Webhook 样例网站 [https://webhook.site/](https://webhook.site/ "https://webhook.site/")，打开该网站即可得到一个 Webhook URL，如图所示：

![](https://cdn.acedata.cloud/srf3tq.png)

将此 URL 复制下来，就可以作为 Webhook 来使用，此处的样例为 [https://webhook.site/995d0a91-d737-40a7-a3b9-5baf68ed924c](https://webhook.site/995d0a91-d737-40a7-a3b9-5baf68ed924c "https://webhook.site/995d0a91-d737-40a7-a3b9-5baf68ed924c")。

接下来，我们可以设置字段 `callback_url` 为上述 Webhook URL，同时填入 `prompt`，如图所示：

![](https://cdn.acedata.cloud/hclosy.png)

点击测试之后会立即得到一个 `task_id` 的响应，用于标识当前生成任务的 ID，如图所示：

<p><img src="https://cdn.acedata.cloud/vkr32a.png" width="300" class="m-auto"></p>

稍等片刻，等图片生成结束，可以发发现 Webhook URL 收到了一个 HTTP 请求，如图所示：

![](https://cdn.acedata.cloud/6znvgq.png)

其结果就是当前任务的结果，内容如下：

```json
{
  "success": true,
  "task_id": "f6e39eaf-652a-4bf5-a15c-79d8b143b80a",
  "image_url": "https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234551030549839932/kcisok_A_cat_sitting_on_a_table_id2724480_591c5c85-ec80-42ab-9fe5-9adfbed192e4.png?ex=663124be&is=662fd33e&hm=da725eb74aae375d60beec38b4cd26c5a7b373b1662f222ff838a8ea6fd5e798&width=1024&height=1024",
  "image_width": 1024,
  "image_height": 1024,
  "image_id": "1234551030549839932",
  "raw_image_url": "https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234551030549839932/kcisok_A_cat_sitting_on_a_table_id2724480_591c5c85-ec80-42ab-9fe5-9adfbed192e4.png?ex=663124be&is=662fd33e&hm=da725eb74aae375d60beec38b4cd26c5a7b373b1662f222ff838a8ea6fd5e798&",
  "raw_image_width": 2048,
  "raw_image_height": 2048,
  "progress": 100,
  "actions": [
    "upscale1",
    "upscale2",
    "upscale3",
    "upscale4",
    "reroll",
    "variation1",
    "variation2",
    "variation3",
    "variation4"
  ]
}
```

其中 `success` 字段标识了该任务是否执行成功，如果执行成功，还会有同样的 `actions`, `image_id`, `image_url` 字段，和上文介绍的返回结果是一样的，另外还有 `task_id` 用于标识任务，以实现 Webhook 结果和最初 API 请求的关联。

如果图片生成失败，Webhook URL 则会收到类似如下内容：

```json
{
  "success": false,
  "task_id": "7ba0feaf-d20b-4c22-a35a-31ec30fc7715",
  "error": {
    "code": "bad_request",
    "message": "Unrecognized argument(s): `-c`, `x`"
  }
}
```

这里的 `success` 字段会是 `false`，同时还会有 `error.code` 和 `error.message` 字段描述了任务错误的详情信息，Webhook 服务器根据对应的结果进行处理即可。

## 流式输出

Midjourney 官方在生成图片的时候是有进度的，在最开始是一张模糊的照片，然后经过几次迭代之后，图片逐渐变得清晰，最后得到完整的图片。

所以，一张图片的生成过程大约可以分为「发送命令」->「开始生图（多次迭代逐渐清晰）」->「生图完毕」的阶段。

在没开启流式输出的情况下，本 API 从发起请求到返回结果，实际上是从上述「发送命令」->「生图完毕」的全过程，中间生图的过程也全被包含在里面，由于 Midjourney 本身生成图片速度较慢，整个过程大约需要等待一分钟或更久。

所以为了更好的用户体验，本 API 支持流式输出，即当「开始生图」的时候就开始返回结果，每当绘制进度有变化，就会流式将结果输出，直至生图结束。

如果想流式返回响应，可以更改请求头里面的 `accept` 参数，修改为 `application/x-ndjson`，不过调用代码需要有对应的更改才能支持流式响应。

Python 样例代码：

```python
import requests

url = 'https://api.acedata.cloud/midjourney/imagine'
headers = {
    'content-type': 'application/json',
    'accept': 'application/x-ndjson',
    'authorization': 'Bearer {token}'
}
body = {
    "prompt": "a beautiful cat --v 6"
}
r = requests.post(url, headers=headers, json=body, stream=True)
for line in r.iter_lines():
    print(line.decode())
```

运行结果：

```json
{"image_url":"https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234558451443699803/eae94f0f-0ba5-4b3c-9bad-59fb33ac2cbc_grid_0.webp?ex=66312ba7&is=662fda27&hm=4625d5f12158bffc07c4faaf6ce75af6f1396122f148b33b91f3e20b48fecc8b&width=256&height=256","image_width":256,"image_height":256,"image_id":"1234558451443699803","raw_image_url":"https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234558451443699803/eae94f0f-0ba5-4b3c-9bad-59fb33ac2cbc_grid_0.webp?ex=66312ba7&is=662fda27&hm=4625d5f12158bffc07c4faaf6ce75af6f1396122f148b33b91f3e20b48fecc8b&","raw_image_width":512,"raw_image_height":512,"progress":35,"actions":[],"task_id":"49589d2c-b6b3-4fbf-9f82-93068509c76f","success":true}
{"image_url":"https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234558458595115149/eae94f0f-0ba5-4b3c-9bad-59fb33ac2cbc_grid_0.webp?ex=66312ba9&is=662fda29&hm=9af53fa645127131a88dfbb3930add7abda710c12a3d6c30c457d6a067b36bab&width=256&height=256","image_width":256,"image_height":256,"image_id":"1234558458595115149","raw_image_url":"https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234558458595115149/eae94f0f-0ba5-4b3c-9bad-59fb33ac2cbc_grid_0.webp?ex=66312ba9&is=662fda29&hm=9af53fa645127131a88dfbb3930add7abda710c12a3d6c30c457d6a067b36bab&","raw_image_width":512,"raw_image_height":512,"progress":75,"actions":[],"task_id":"49589d2c-b6b3-4fbf-9f82-93068509c76f","success":true}
{"image_url":"https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234558483408490566/kcisok_A_landscape_painting_of_a_beautiful_sunset_id5963392_eae94f0f-0ba5-4b3c-9bad-59fb33ac2cbc.png?ex=66312baf&is=662fda2f&hm=185ea8f130806bf8bd96911bd251808455fd65596edcdb459f9b3cfd7860387c&width=1024&height=1024","image_width":1024,"image_height":1024,"image_id":"1234558483408490566","raw_image_url":"https://midjourney.cdn.acedata.cloud/attachments/1234291876639674388/1234558483408490566/kcisok_A_landscape_painting_of_a_beautiful_sunset_id5963392_eae94f0f-0ba5-4b3c-9bad-59fb33ac2cbc.png?ex=66312baf&is=662fda2f&hm=185ea8f130806bf8bd96911bd251808455fd65596edcdb459f9b3cfd7860387c&","raw_image_width":2048,"raw_image_height":2048,"progress":100,"actions":["upscale1","upscale2","upscale3","upscale4","reroll","variation1","variation2","variation3","variation4"],"task_id":"49589d2c-b6b3-4fbf-9f82-93068509c76f","success":true}
```

可以看到，启用流式输出之后，返回结果就是逐行的 JSON 了。

在 Node.js 环境中，实现代码可写为如下：

```javascript
const axios = require("axios");

const url = "https://api.acedata.cloud/midjourney/imagine";
const headers = {
  "content-type": "application/json",
  accept: "application/x-ndjson",
  authorization: "Bearer {token}",
};
const body = {
  prompt: "a beautiful cat --v 6",
  action: "generate",
};

axios
  .post(url, body, { headers: headers, responseType: "stream" })
  .then((response) => {
    console.log(response.status);
    response.data.on("data", (chunk) => {
      console.log(chunk.toString());
    });
  })
  .catch((error) => {
    console.error(error);
  });
```

这些示例运行的结果都是相似的。

请注意，流式输出结果中有一个称为 progress 的字段，表示生成进度，范围从 0 到 100。如果需要，您可以在页面上显示这些信息。

> 注意：当生成未完全完成时，`actions` 字段为空，表示无法对中间图像执行进一步处理操作。生成完成后，在生成过程中生成的 image_url 将被销毁。

此外，您可以通过指定 `accept=application/x-ndjson` 的请求头和 callback_url 的请求体，将流式结果与异步回调结合起来，然后 callback_url 可以接收到多个流式结果的 POST 请求。
