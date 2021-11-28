# 双方向RNN

過去の情報だけでなく未来の情報を加味することで精度を向上させる。

実用例：文章の推敲や機械翻訳

![スクリーンショット 2021-11-28 19 40 53](https://user-images.githubusercontent.com/85814165/143764511-3fa76926-3ff7-4cf9-8e09-1956c6f4e885.png)

# 演習チャレンジ

![スクリーンショット 2021-11-28 19 42 27](https://user-images.githubusercontent.com/85814165/143764550-276fe6b2-8002-493a-a0e7-27ac669936e4.png)

Q.4 np.concatenate([h_f,h_b[::-1]],axis=1)
