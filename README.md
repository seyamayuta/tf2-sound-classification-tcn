# tf2-sound-classification-tcn

TensorFlow 2でTCN(Temporal Convolutional Network)を使って音を分類するNotebook集です。  
以下のように、大きく2部構成に分けています。

## 概要

### モデルの作成と評価

教育と評価に使う音声データを作成し、TensorFlowで扱いやすいデータ形式に編集し、TCNモデルの教育と検証を行っています。
![構成１](https://user-images.githubusercontent.com/8535627/117147208-fdb1a980-adef-11eb-8583-dcb5fe92402e.png)

### 音の聞き分け対決

ランダムに作成した音に対する、人間（私）と学習済みモデルとの聞き分け対決です。  
私の予測結果は、事前にテキストファイルで作成しています。
![構成２](https://user-images.githubusercontent.com/8535627/117147222-01453080-adf0-11eb-93f9-afa9c744447c.png)

## 参考情報

動作環境はDocker（Docker Compose）で作成できるようにしています。（GPUの使用を前提）  
また、各Notebookでは乱数シードを固定して可能な限り同じ結果になるようにしていますが、TensorFlowの仕様により、GPUを利用している部分については同じ結果にはなりません。そのため、学習時の各エポック単位の結果が異なる点はご了承ください。
