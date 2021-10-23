# 記録（コンペ・学習など）
### 2021/6/25
- Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
  - 目的変数は0,1,2の値を取るが、不均衡さがあり、大半が0を示している。
  - そのため、不均衡さの訂正のために、smoteが有効ではないかと考える。

### 2021/6/26
- Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
  - k-NN(k近傍法)を初めて試す。 学習用データをtrain:test=8:2に分割し、それぞれのaccuracyの差が低いkで検証をする。
  - k=26 の場合、score = 0.6522132
  - k=6 の場合、score = 0.6331277 #  testのaccuracyがk=6以降一定だったので試しにsubmit
  - weighted kNNという方法があるようだ。距離で重みをつけるそう。knn = KNeighborsClassifier(n_neighbors=k, weights="distance") (https://qiita.com/fujin/items/128ed7188f7e7df74f2c)</br>
    →score = 0.6290278 (k=4,weighted)うーん。。

### 2021/6/27
- Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
  - Google colab でstome+lightgbm+optunaを実行してみる。データの上げ方、保存方法を調べる。 # ローカルのmacでの実行時にスタックしてしまうため</br>
  → colab proへ課金、途中で止まってしまう。
  - 米国データサイエンティストがやさしく教えるデータサイエンスのためのPython講座を購入、勉強スタート</br>
  → セクション１〜１４まで完了！ショートカットなど意外と知らないことが多くて、かなり勉強になる。

### Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
- 実行したこと一覧
  - Decidision tree
  - Random forest 
  - lightGBM (weight_columnの重み付けを調べる）
  - k-NN
  - stome
  - optuna
  - target encoding
  - dummies
