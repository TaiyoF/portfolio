# 誤差逆伝播法
数値微分では無駄な計算が多かったが、誤差逆伝播法では出力層から順に微分し、前の層・前の層へと伝搬させる。
最小限の計算で各パラメータでの微分値を解析的に計算する手法。

計算結果（誤差E）から微分を逆算することで、不要な再帰的計算を避けて微分を算出できる。

![スクリーンショット 2021-11-02 5 08 37](https://user-images.githubusercontent.com/85814165/139734898-8b495a52-04bb-4390-b2dd-1d95ca2cb00b.png)

重みに関して

![gif latex-86](https://user-images.githubusercontent.com/85814165/139734725-9f806b50-e83f-4de7-9750-b87289cea6ba.gif)

バイアスに関して

![gif latex-87](https://user-images.githubusercontent.com/85814165/139734768-17ef4f04-f42d-4520-95aa-7cf3cc7aa713.gif)

## 求め方

誤差関数

![gif latex-88](https://user-images.githubusercontent.com/85814165/139736027-c181b04c-e3a5-437b-8fbd-edb48aafb7ae.gif)

出力層の活性化関数＝恒等写像

![gif latex-89](https://user-images.githubusercontent.com/85814165/139736145-c557b93e-4812-43cd-bc38-37fa39f16c4e.gif)

総入力の計算

![gif latex-90](https://user-images.githubusercontent.com/85814165/139736285-34db5085-42f0-4544-8933-e083cd426ee4.gif)

Eをy,yをu,uをwで微分する。

![gif latex-91](https://user-images.githubusercontent.com/85814165/139736480-518e2ed3-7b43-4146-8c7c-b2dec374f92b.gif)

![gif latex-92](https://user-images.githubusercontent.com/85814165/139736574-dc4bece4-45bb-44a7-b21c-6ec941ab1c01.gif)

![gif latex-93](https://user-images.githubusercontent.com/85814165/139737858-d393e5cd-e7cb-4703-b4e4-ce299ed29741.gif)
![gif latex-94](https://user-images.githubusercontent.com/85814165/139737873-5818afae-3924-4064-8d62-b9c645c82d53.gif)

![gif latex-95](https://user-images.githubusercontent.com/85814165/139738125-5dfa5db8-ae12-4639-a2df-eb721cfb366d.gif)の１箇所以外は定数扱いのため微分で0になる。

さらに、![gif latex-97](https://user-images.githubusercontent.com/85814165/139738260-8ea1fcb3-2e42-4908-b2a1-f4198b515104.gif)は1次の関数で微分すると1なので、残るのは![gif latex-96](https://user-images.githubusercontent.com/85814165/139738203-2920fb9b-225b-428f-a1a8-72e467daef43.gif)となる。

![gif latex-98](https://user-images.githubusercontent.com/85814165/139738846-5e736080-4521-4954-91a6-6be26d95ccd6.gif)

# 確認テスト
Q.誤差逆伝播法では不要な再帰的処理を避けることができる。すでに行った計算結果を保持しているソースコードを抽出せよ

![スクリーンショット 2021-11-02 5 11 47](https://user-images.githubusercontent.com/85814165/139735293-da7d9bf6-c041-4b92-aa48-4fba1b32d083.png)

Q.２つの空欄に該当するソースコードを探せ

![gif latex-99](https://user-images.githubusercontent.com/85814165/139739558-36649065-6e43-46f4-ae94-271fcfbcde74.gif)

![スクリーンショット 2021-11-02 5 45 01](https://user-images.githubusercontent.com/85814165/139739632-c17d4a2d-33a2-4393-b460-53ca61166329.png)

![gif latex-100](https://user-images.githubusercontent.com/85814165/139739753-b61e11b3-309c-4569-9d81-bcd795ace377.gif)

![スクリーンショット 2021-11-02 5 46 33](https://user-images.githubusercontent.com/85814165/139739844-0c8bcdd9-d3bf-4756-8bac-ecb9af96f2de.png)


# 実装
1_3_stochastic_gradient_descent.ipynbより

![スクリーンショット 2021-11-03 21 45 19](https://user-images.githubusercontent.com/85814165/140062391-939b2395-c1a1-4173-84cc-3558a67687fb.png)
![スクリーンショット 2021-11-03 21 45 37](https://user-images.githubusercontent.com/85814165/140062401-6517bd48-0455-46cf-8d48-d843001be486.png)

