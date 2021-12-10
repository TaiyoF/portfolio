# 応用技術

# 4-1 MobileNet

- ディープラーニングモデルの軽量化・高速化・高精度化を実現（モバイルできるようなネットワーク）
- DepthWise ConvとPointWise Convにより畳み込みの演算を工夫してる。

## Depthwise Convolution
カーネルのフィルタ数を1枚とすることで、計算を軽くする。

H x W x C x K x K

## Pointwise Convolution
カーネルサイズを1x1と固定し、フィルタはM枚

H x W x C x M

# 4-2 DenseNet

Dense Blockが特徴で、出力層に前の層の入力を足し合わせる。k層倍のチャンネル数になる。スキップコネクションの一種。

Transition LayerではConvとプーリングの処理を行い、元の層に戻す。（特徴マップのサイズを変更し、ダウンサンプリングを行う）

DenseNetで使われるDenseBlockでは、成長率（Growth Rate）というハイパーパラメータがある。

## DenseNetとResNetの違い

- DenseBlockでは前の層の出力全てが後方の層の入力
- RessidualBlockでは、前1層の入力のみ後方の層へ入力

# 4-3 Layer正規化/Instance正規化



# 4-4 Wavenet
