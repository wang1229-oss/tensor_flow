tensorflow图形检测_使用Google Colab使用Tensorflow进行自定义对象检测
于 2020-11-12 11:15:48 发布

![偵測成果示意](results/洋芋片.jpeg)

在此文章中，我们将使用Tensorflow对象检测API构建自定义对象检测器。我将选择检测苹果果实。但是您可以选择要检测自己的自定义对象的任何图像。

步骤：

Installation
Gathering data
Labeling data
Generating TFRecords for training
Configuring training
Training model
Exporting inference graph
Testing object detector
一、Installation
Python 3.6或更高版本。
Ubuntu 18.04/google colab
Tensorflow/Tensorflow-gpu
克隆Tensorflow模型存储库:
搭建环境
Protobuf编译:Tensorflow对象检测API使用Protobufs配置模型和训练参数。在使用该框架之前，必须先编译Protobuf库。这应该通过从tensorflow / models / research /目录运行以下命令来完成：
将库添加到PYTHONPATH
在google colab运行时，应将TFmodels / research /和slim目录附加到PYTHONPATH。

Object Detection Installation
Testing the Installation
使用google colab的配置阅读下方即可：

好好先生：使用Google Colab配置Tensorflow对象检测API​zhuanlan.zhihu.com
94c1ce402850a210329f3519a562127f.png
二、Gathering data
2.1打开您的google chrome浏览器并安装一个名为Download All Images的扩展程序。

eb465daf3bdce63bcb331f9327a0ba94.png
2.2。现在在Google图片中搜索所需的图片选择，在我的例子中是“ Apple”。现在，单击“下载所有图像”扩展按钮，该按钮将位于浏览器的右上角。您将获得一个包含图像的zip文件。然后将其提取。

3eaf8ec3e8147b5f3bfa67201a030361.png
三、 Labeling data
打开您的终端并通过以下方式安装LabelImg

LabelImg是图形图像注释工具。

安装labelImg后，通过键入将其打开

在不同的环境中安装labelImag方法不同，可以参照如下：

zjgulai/labelImg​github.com
322723934f3bb94c26647a4b6e6caa38.png
0da1187ef218517efbc34f09c7201d78.png
上面的内容。并对所有图片执行此操作。它正在做的是，它正在生成一个XML文件，其中包含带有其标签的对象坐标。

我标记了约100张图片。

现在克隆我的存储库

zjgulai/Tensorflow-Object-Detection-API-With-Custom-Dataset​github.com
322723934f3bb94c26647a4b6e6caa38.png
克隆之后进入目录：

adaf14492fcff468fbf53d26a204cd3a.png
四、Generating TFRecords for training
现在，将图像文件的70％复制到训练文件夹图像/训练中，其余30％复制到测试文件夹中。

在标记了图像的情况下，我们需要创建TFRecords用作输入数据以训练对象检测器。为了创建TFRecords，我们将使用

datitran/raccoon_dataset​github.com
f232611ceb4e075fdb8c49dd7ecc35b1.png
两个脚本。即xml_to_csv.py和generate_tfrecord.py文件。

目录：

edd953b900e530338916f122acf59d96.png
现在在该文件夹中，我们可以通过打开命令行并键入以下内容，将XML文件转换为train_label.csv和test_label.csv：

它们在数据目录中创建两个文件。一个叫做test_labels.csv，另一个叫做train_labels.csv。

在将新创建的文件转换为TFRecords之前，我们需要更改generate_tfrecords.py文件中的几行。

如果你有多类标记：

现在，您可以通过键入以下内容来生成TFRecords：

这两个命令生成一个train.record和一个test.record文件，可用于训练我们的对象检测器。

五、Configuring training
训练之前，我们要做的最后一件事是create a label map and a training configuration file.

六、Creating a label map
The label map maps： an id to a name.

I have already created a label map file for my training. It looks like this:

编辑：object-detection.pbtxt

如果您使用多个类，请遵循此模式。

每个类别的ID号应与generate_tfrecord.py文件中指定的ID相匹配。

七、Creating a training configuration
我们将在Google Colab中训练我们的模型。

I am using “SSD_MOBILENET_V2” for training and with the batch size of 4.

You can change the number of steps, which pre-trained model to use & the batch and size.

然后，您需要运行以下单元格。将有一个Upload TF Record提示。

在此之下，您需要上传生成的

train.record
test.record
object-detection.pbtxt
八、Training model
现在，在上传所有这些文件之后，运行下面的所有单元格。它将得到训练。

九、Exporting inference graph
如果已运行所有单元，则最后将下载一个名为Frozen_inference_graph.pb的文件。

十、Testing Object Detector
现在，将Frozen_inference_graph.pb文件复制到我的GitHub克隆文件夹中。然后，您需要在该webcam_inference.py中进行一些编辑，以测试您自己的对象检测器。打开该文件并检查代码。

如果您正确执行了上述所有步骤，则可以通过网络摄像头测试模型。

十一、Conclusion
Tensorflow对象检测API允许您使用转移学习技术创建自己的对象检测器。

代码链接：

https://github.com/zjgulai/Tensorflow-Object-Detection-API-With-Custom-Dataset​github.com
参考文献和链接：

https://github.com/tensorflow/models/tree/master/research/object_detection
https://medium.com/@WuStangDan/step-by-step-tensorflow-object-detection-api-tutorial-part-1-selecting-a-model-a02b6aabe39e
https://pythonprogramming.net/introduction-use-tensorflow-object-detection-api-tutorial/
https://towardsdatascience.com/creating-your-own-object-detector-ad69dda69c85
https://medium.com/analytics-vidhya/custom-object-detection-with-tensorflow-using-google-colab-7cbc484f83d7

http://weixin.qq.com/r/5TqGnkTEZhkZrQD992-3 (二维码自动识别)

