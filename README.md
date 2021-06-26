# portfolio
fkubotaさんのkaggle日記という戦い方(https://zenn.dev/fkubota/articles/3d8afb0e919b555ef068)を参考にメモを記載しています。</br>
学習・取り組み途中からの記載になりますが、ご了承ください。

# 学習環境
- Macbook Pro (13-inch, 2017, Two Thunderbolt 3 ports)
  - CPU 2.3 GHz デュアルコアIntel Core i5
  - Memory 8 GB 2133 MHz LPDDR3
  - GPU Intel Iris Plus Graphics 640 1536 MB
  - 外部モニター LG製 34WL750-B

- 書籍
  - PythonではじめるKaggleスタートブック
  - Python 1年生
  - Python 2年生 スクレイピングのしくみ 

- Udemy
  - 【ゼロから始めるデータ分析】ビジネスケースで学ぶPythonデータサイエンス入門（1週目完了）
  - 米国AI開発者がゼロから教えるPython入門講座（進めているところ）

- Slack
  - DataScienceHub参加中
  - データラーニングギルド参加中
  - 現役DSメンターにメンティを依頼（MENTAにて2021年6月〜）

# 記録（コンペ・学習など）
### 2021/6/25
- Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
  - 目的変数に不均衡さがあることが見受けられる。大半が0を示している。
  - そのため、不均衡さの訂正のために、smoteが有効ではないかと考える。

### 2021/6/26
- Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
  - k-NN(k近傍法)を初めて試す。 学習用データをtrain:test=8:2に分割し、それぞれのaccuracyの差が低いkで検証をする。
  - k=26 の場合、score = 0.6522132
  - k=6 の場合、score = 0.6331277 #  testのaccuracyがk=6以降一定だったので試しにsubmit

### 2021/6/27
- Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
  - Google colab でstome+lightgbm+optunaを実行してみる。データの上げ方、保存方法を調べる。 # ローカルのmacでの実行時にスタックしてしまうため

# Signate 【第11回_Beginner限定コンペ】医療保険の費用帯予測
- 実行したこと一覧
  - Decidision tree
  - Random forest 
  - lightGBM
  - k-NN
  - stome
  - optuna
  - target encoding
  - dummies
