# facerecognize

[參考影片](https://www.youtube.com/watch?v=qWXXHjV3JHI&list=PLeo1K3hjS3uvaRHZLl-jLovIjBP14QTXc)

## 流程

### data collect

工具 : [Fatkun Batch Download Image](https://chrome.google.com/webstore/detail/fatkun-batch-download-ima/nnjjahlikiabnchcpehcpkdeckfgnohf/related?hl=en)

> 檔案所在 <br>
> facerecognize/model/dataset/jonghyun <br>
> facerecognize/model/dataset/key <br>
> facerecognize/model/dataset/minho <br>
> facerecognize/model/dataset/onew <br>
> facerecognize/model/dataset/taemin

## data cleaning

> 檔案所在 <br>
> facerecognize/model/data_cleaning.ipynb

臉部辨識 model : opencv/haarcascade_frontalface_default.xml
眼部辨識 model : opencv/haarcascade_eye.xml

function
get_cropped_image_if_2_eyes : 若偵測的到雙眼，則返回臉部區塊 <br>
將這些偵測的到雙眼的臉部區塊存到 facerecognize/model/dataset/cropped/ 資料夾

## data process

> 檔案所在 <br>
> facerecognize/model/classification.ipynb

將 data clean 後的 face 照片，用 w2d 處理後拚在彩色 face 下面

## data training

> 檔案所在 <br>
> facerecognize/model/classification.ipynb

Pipeline : Standard Scaler + SVC

GridSearch CV : SVM, Random Forest, Logistic Regression<br>
best score 為 SVM 的 0.632 (training data) 0.653 (testing data)<br>
儲存此 model : facerecognize/model/saved_model.pkl<br>
confusion matrix :<br>
![](https://i.imgur.com/YiPfGAe.png)

## 使用此 model

> 檔案所在 <br>
> facerecognize/server/util.py
