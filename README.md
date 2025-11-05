# 南華大學人工智慧期中作業：TensorFlow 物件偵測實作

本專案依據課堂指定文章「使用 Google Colab 使用 TensorFlow 進行自定義物件偵測」製作，
並以我們實際執行的程式與截圖替換原文中的範例圖片與程式碼。

---

## Tensorflow Object Detection – Using Google Colab to Train a Custom Detector

This article introduces how to use the TensorFlow Object Detection API to create a custom object detector.
Detailed steps include installation setup, data collection, image labeling, generating TFRecords, and training/testing configurations.

---

## 1. Installation

Python 3.6 or higher
Ubuntu 18.04 / Google Colab
TensorFlow / TensorFlow-gpu

Clone the TensorFlow models repository and set up the environment.

![](results/1.png)

---

## 2. Gathering Data

Open your Google Chrome browser and install the extension **Download All Images**.
Search for your target object images (e.g., “Apple”) and download them.

![](results/2.png)
![](results/3.png)

---

## 3. Labeling Data

Use **LabelImg** to annotate your images.
This tool generates XML files containing object coordinates and labels for each image.

![](results/4.png)

---

## 4. Generating TFRecords for Training

Split your dataset: 70% for training and 30% for testing.
We use two scripts: `xml_to_csv.py` and `generate_tfrecord.py`.

Convert XML files to CSV, then to TFRecord files.

![](results/5.png)
![](results/6.png)

---

## 5. Creating TFRecord Files

After generating CSVs, run the TFRecord generation scripts.

![](results/7.png)
![](results/8_1.png)
![](results/8_2.png)

---

## 6. Verifying Dataset Files

Check your directory to confirm these files exist:

* `train_labels.csv`
* `test_labels.csv`
* `train.record`
* `test.record`

![](results/9.png)

---

## 7. Configuring Training

Before training, create:

* **Label map file** (`object-detection.pbtxt`)
* **Training configuration file**

Each class ID in the label map must match the IDs in `generate_tfrecord.py`.

---

## 8. Training Model

Use Google Colab to train your model with **SSD_MOBILENET_V2** or another pre-trained model.
You may adjust steps, batch size, and pretrained weights according to your dataset.

---

## 9. Exporting Inference Graph

After training, export `frozen_inference_graph.pb`.
This file contains your trained model and can be used for inference or webcam testing.

---

## 10. Testing Object Detector

Copy the exported graph to your working directory, modify `webcam_inference.py`, and test detection on your own dataset.
If all steps were followed correctly, the detector should successfully recognize your custom object.

---

## 11. Conclusion

The TensorFlow Object Detection API allows you to build your own detector easily using transfer learning.
Our implementation replaces all code blocks and structure screenshots from the tutorial with our **actual execution results** from Google Colab.

---

## References

* Original tutorial: [CSDN Blog – 使用 Google Colab 使用 Tensorflow 进行自定义对象检测](https://blog.csdn.net/weixin_39884078/article/details/110385105)
* Reference code: [kevin945290/AI_report](https://github.com/kevin945290/AI_report)
* TensorFlow Models: [https://github.com/tensorflow/models](https://github.com/tensorflow/models)

> 本報告僅作為南華大學人工智慧課程之期中作業使用，
> 所有程式碼與截圖皆為我們組在 Google Colab 實際執行所得結果。
