# Attention Mechanism

Seq2seqの課題：長い文章への対応が難しい。2単語でも100単語でも固定次元ベクトルに入力しないといけない。

解決策：文章が長くなるほどそのシーケンスの内部表現の次元数も大きくなる。

Attention Mechanism：入力と出力のどの単語が関連しているか、の関連度を学習する仕組み

# 確認テスト

Q.RNNとword2vec,Seq2seq,attentionの違いを簡潔に述べよ

A.

RNN:時系列データを学習するのに適したNN

word2vec:単語の分散表現ベクトルを得る表現

seq2seq:一つの時系列データから別の時系列データを得るNN

AttentionMechanism:時系列データの中身の関連性に重みをつける手法


Q.seq2seqとHRED,HREDとVHREDの違いを簡潔に述べよ

A.

seq2seq：1文の一問一答に対して処理ができるある時系列データからある時系列データを作り出すネットワーク

HRED:このseq2seqの機構に、その文脈の意味を汲み取った文の変換ができるようにしたもの。

VHRED:HREDが文脈に対して当たり障りのない回答しかできなくなった解決策。





