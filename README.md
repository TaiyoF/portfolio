# portfolio
my portfolio

### 2021/6/25
-目的変数に不均衡さがあることが見受けられる。大半が0を示している。
 -そのため、不均衡さの訂正のために、smoteが有効ではないかと考える。

### 2021/6/26
-Signateの【第11回_Beginner限定コンペ】医療保険の費用帯予測にチャレンジ中
 -k-NNを初めて試す。 学習用データをtrain:test=8:2に分割し、それぞれのaccuracyの差が低いkで検証をする。
  -k=26 の場合、score = 0.6522132
  -k=6 の場合、score = 0.6331277 #testのaccuracyがk=6以降一定だったので試しにsubmit
