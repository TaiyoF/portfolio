# 活性化関数

## 中間層用
- ReLU関数
現在最も使われる活性化関数。勾配消失問題の回避とスパース化に貢献。
x<=0ではf(x)=0, x>0ではf(x)=x

- シグモイド関数（ロジスティック関数）
大きな値では、出力の変化が微小なため、勾配消失問題を起こすことがある。

- ステップ関数
今はあまり使われない。出力は0 or 1のみ。なので、線形分離可能なものしか学習できなかった。

## 出力層用



# 確認テスト

Q.線形と非線形の違いを図にかいて簡易に説明せよ
線形・・直線、y = ax + bなどで表される式
非線形・・曲線、y = ax^2 + bx + cなど　2乗以上の式

・線形

![スクリーンショット 2021-11-01 8 18 39](https://user-images.githubusercontent.com/85814165/139604563-3be4d589-6dc4-4211-956b-d45cc825083c.png)

・非線形

![スクリーンショット 2021-11-01 8 18 57](https://user-images.githubusercontent.com/85814165/139604567-5ffd3cc1-8e7b-40ec-9959-d1fa7720d496.png)


Q.配布されたソースコードより該当する箇所を抜き出せ

![スクリーンショット 2021-11-01 8 31 46](https://user-images.githubusercontent.com/85814165/139604885-7a1ff4cc-86d8-48d4-810a-8c2a616078af.png)

# 実装
1_1_forward_propagation_after.ipynbより

![スクリーンショット 2021-11-03 20 38 21](https://user-images.githubusercontent.com/85814165/140053681-d0f27d3b-6d6c-4d44-a914-1c246536ff61.png)
![スクリーンショット 2021-11-03 20 38 32](https://user-images.githubusercontent.com/85814165/140053697-9fbdbdc7-1fa2-4247-b576-94086cec1d8d.png)


