# portfolio
fkubotaさんのkaggle日記という戦い方(https://zenn.dev/fkubota/articles/3d8afb0e919b555ef068) を参考にメモを記載しています。</br>
学習・取り組みについてまとめています。途中からの記載になりますが、ご了承ください。

# 学習環境
- Macbook Pro (13-inch, 2017, Two Thunderbolt 3 ports)
  - CPU 2.3 GHz デュアルコアIntel Core i5
  - Memory 8 GB 2133 MHz LPDDR3
  - GPU Intel Iris Plus Graphics 640 1536 MB
  - 外部モニター LG製 34WL750-B
  - Jupyter/Docker/Google colab

- 書籍
  - PythonではじめるKaggleスタートブック
  - Python 1年生
  - Python 2年生 スクレイピングのしくみ 

- Udemy
  - 【ゼロから始めるデータ分析】ビジネスケースで学ぶPythonデータサイエンス入門（1週目完了）
  - 米国AI開発者がゼロから教えるPython入門講座（学習中）
  - 米国データサイエンティストがやさしく教えるデータサイエンスのためのPython講座（学習中）

- Slack
  - DataScienceHub参加中
  - データラーニングギルド参加中
  - 現役DSメンターにメンティを依頼（MENTAにて2021年6月〜）

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
    - esc +m markdown, esc+Y セル
    - shift + クリック　→　shift + m でセルのマージができる
    - esc + A　セルの上に新規のセルを追加　
    - esc + B　セルの下に新規のセルを追加
    - esc + D + D (Dを2回) セルを削除
    - esc + Z　戻る
    - shift + Z　進む
    - command + B　左のナビゲーションを閉じる
    - command + / コメントアウト　複数選択も可能
    - command + ]    インデント
    - command + [    アンインデント
    - command + Z undo
    - command + Y 次に進む
    - 行のコピーは行を選択しているだけで良い。行をすべて選択する必要はないということ。
    - command + ←　→　行の先頭や末に移動できる
    - optin + ←　→　単語の前後に移動できる
    - optin + enter
    - shift + tab 関数のReferenceが見れる
    - 0.1 = 1e-1     0.001 =1e-3
    -  "hello {}".format("world")
    - "key is {}, value is {}".format("KEY", "VALUE")
    - "key is {k}, value is {v}".format(k="KEY", v="VALUE")
    - filename = "{}_{}".format(patient_id, number)
    - "hello world".split(" ")
    - " ".join(["hello", "world"])
    - list2.append(list1)
    - dict = {"key1":"value1", "key2":"value2"}
    - dict["key2"]
    - dict["key4"] = "value4" # dictにkey4を追加
    - tuple = (1, 2, 3) 関数の戻り値、メタデータ
    - set(list) = データの重複を取り除きたいとき
    - // 商のみ算出
    - % 余りのみ算出
    - != ノットイコール
    - "h" in "hello" / "h" in ["h", "e", "l", "l", "o" ]→True
    - is / is not
    - a is None
    - for loop    for 要素 in リスト:
    - range(x, y, step)

for idx,color in enumerate(colors):
    favorite_color = "blue"
    if color == favorite_color:
        print("{}:{} is my favorite".format(idx, color))
    else:
        print("{}:{} is not my favorite".format(idx, color))

リスト内包表記(List Comprehensions)
colors = ["red", "blue", "green", "yellow", "white"]
→colors_png = ["red.png", "blue.png", "green.png", "yellow.png", "white.png"]
colors_png = []
for color in colors:
    color_png = color +".png"
    colors_png.append(color_png)
print(colors_png)
→
リスト内包表記
[color + ".ping" for color in colors]

while
i = 0
while i < 5:
    print("{} is less than 5".format(i))
    i += 1

break:中断
continue:飛ばし

Iterable: string, list, tuple, set, dict
Not iterable: integer, float, boolean
Iterable: iter()関数でiteratorを返すオブジェクト
Iterator:next()関数でIterationできるオブジェクト

_(under score):最後に実行したコードの戻り値が入っている

mutable:変更可能オブジェクト:list, dict, set
Immutable:変更不可オブジェクト:integer, float, bool, string, tuple

Lambda関数
def func(a):
    return a +1
→x = lambda a: a +1

"/home/user/Desktop/image1.jpg"
→x = lambda path: path.split("/")[-1].split(".")[0]

### 2021/6/28
- Udemy続きをやる。Numpyまで完了したいな。

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
