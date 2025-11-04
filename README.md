# tensor_flow
南華大學人工智慧期中作業－TensorFlow 環境建置與物件偵測

# 南華大學人工智慧期中作業：TensorFlow 物件偵測實作

本專案依照課堂範例與指定網站內容進行 TensorFlow Object Detection API 的實作。
**所有圖片均為我們實際在 Google Colab 執行所截取的成果畫面。**

---

## 一、環境建置與安裝

首先在 Colab 安裝 TensorFlow 及相關依賴，並下載官方 Models 專案。

![環境建置](results/1.png)

---

## 二、建立必要資料夾與下載腳本

建立 `images/train`, `images/test`, `annotations` 等資料夾，並下載 XML 轉換與 TFRecord 產生腳本。

![建立資料夾與下載腳本](results/2.png)
![執行下載結果](results/3.png)

---

## 三、建立 Label Map 檔案

建立 `object-detection.pbtxt` 或 `label_map.pbtxt` 作為標籤定義。

![Label map 建立成功](results/4.png)

---

## 四、XML → CSV 轉換

將標註檔案（Pascal VOC XML）轉換為 CSV 格式，產生訓練與測試集標籤。

![執行 xml\_to\_csv.py](results/5.png)
![轉換結果顯示](results/6.png)

---

## 五、產生 TFRecord

使用 `generate_tfrecord.py` 產生 `train.record` 與 `test.record` 檔案。

![generate\_tfrecord.py 程式碼](results/7.png)
![執行 TFRecord 產生程式 (1)](results/8_1.png)
![執行 TFRecord 產生程式 (2)](results/8_2.png)

---

## 六、最終檔案確認

最終輸出包含：

* `/content/annotations/train_labels.csv`
* `/content/annotations/test_labels.csv`
* `/content/train.record`
* `/content/test.record`

![最終執行成果](results/9.png)

---

## 七、環境資訊

* 執行平台：Google Colab (Python 3.12)
* TensorFlow 版本：2.19.1
* 套件：opencv-python, pillow, lxml, Cython, tf_slim, matplotlib, protobuf, pandas

---

## 八、參考來源

* 課堂指定網站：[https://www.cnblogs.com/huiwei13/p/11797142.html](https://www.cnblogs.com/huiwei13/p/11797142.html)
* 參考程式碼：[https://github.com/kevin945290/AI_report](https://github.com/kevin945290/AI_report)

> 本報告僅作為課堂期中作業使用，所有截圖為本人實際執行成果。
