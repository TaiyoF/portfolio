# 軽量化・高速化技術

## 分散深層学習

・深層学習は多くのデータの使用やパラメータ調整に多くの時間がかかるため、高速な計算が求められる

・複数の計算資源を使用し、並列的にNNを構成することで、効率の良い学習を行う

・データ並列化やモデル並列化、GPUによる高速技術

# 3-1 モデル並列

・親モデルを各ワーカーに分割し、それぞれのモデルを学習させる。全てのデータで学習が終わった後で、１つのモデルに復元。

・モデルが大きいときはモデルを並列化、データが大きい時はデータ並列化をすると良い。

・モデルのパラメータ数が多いほど、スピードアップの効果を得られやすく、効率が向上する。

# 3-2 データ並列

・親モデルを各ワーカーに子モデルとしてコピー

・データを分割し、各ワーカーごとに計算される

![スクリーンショット 2021-12-04 19 50 29](https://user-images.githubusercontent.com/85814165/144706782-307b62d2-ce00-4959-819c-79cbec24a302.png)

## 同期型

各ワーカーの計算が終わるのをまち、全ワーカーの勾配が出たところで勾配の平均を計算し、親モデルのパラメータを更新する。

パラメータ更新後のモデルを子モデルとして学習させる、ことを繰り返す。

## 非同期型

各ワーカーは互いの計算を持たず、各々のモデル毎に更新を行う。

学習が終わった子モデルはパラメータサーバにPushされる。新たに学習を始める時はパラメータサーバからPopしたモデルに対して学習をする。

## 同期型と非同期型

・処理スピードは非同期型のが早い。

・精度は同期型のが良いことが多い。

# 3-3 GPU

・GPGPU（General-Purpose on GPU）　元々の使用用途であるグラフィック以外の用途で利用されるGPUの総称。

- CUDA GPU上で並列コンピューティングを行うためのプラットフォーム

- OpenCL　オープンな並列コンピューティングのプラットフォーム

・CPU 高性能なコアが少数、複雑で連続的な処理が得意

・GPU 比較的低性能なコアが多数、簡単な並列処理が得意、NNの学習は単純な行列演算が多いため高速化ができる

# 3-4 量子化

ネットワークが大きくなると大量のパラメータが必要となり学習や推論に多くのメモリと演算処理が必要

→通常のパラメータの64bit浮動小数点を32bitなど下位の精度に落とすことでメモリと演算処理の削減を行う

## 量子化のメリットとデメリット

- メリット・・・計算の高速化、省メモリ化
- デメリット・・・精度の低下

## 計算の高速化
計算時間は単精度演算は倍精度演算の２倍の速度。

- 倍精度演算(64bit)
- 単精度演算(32bit)

# 3-5 蒸留

精度の高いモデルはニューロンの規模が大きなモデルになっている。そのため、多くのメモリと演算処理が必要。

→規模の大きなモデルの知識を使い、軽量なモデルを作成すること。

## 教師モデルと生徒モデル

- 教師モデル・・予測精度の高い複雑なモデルやアンサンブルされるモデル
- 生徒モデル・・教師モデルをもとに作られる軽量なモデル

教師モデルの重みを固定し、生徒モデルの重みを更新していく。誤差は教師モデルと生徒モデルのそれぞれの誤差を使い、重みを更新する。

## 蒸留のメリット

少ない学習回数でより精度の高いモデルを作成することができる。

# 3-6 プルーニング

ネットワークが巨大になると大量のパラメータがある。しかし、全てのニューロンの計算が精度に寄与しているわけではない。

→不要なニューロンを削除することでモデルの軽量化や高速化が見込まれる。

- ニューロンの削減・・重みが閾値以下の場合ニューロンを削除し、再学習を行う。

# まとめ

- 量子化・・重みの精度を下げることで計算の高速化と省メモリ化をする
- 蒸留・・複雑で精度の高い教師モデルから軽量な生徒モデルを作る
- プルーニング・・寄与の少ないニューロンをモデルから削除し、高速化と省メモリ化する。
