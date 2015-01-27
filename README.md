# gtitraning

## Git全体の設定

以下のコマンドをターミナル（コマンドプロンプト）で打ちます。

### (1)マージ時のファストフォワードマージ（以下ff）を無効にする。

```python
git config --global merge.ff false
```

`ff`を無効にすると、ブランチを合流した時に`マージコミット`が残るようになります。

参考：[図で分かるgit-mergeの--ff, --no-ff, --squashの違い - アジャイルSEを目指すブログ](http://d.hatena.ne.jp/sinsoku/20111025/1319497900)

### (2)プル時にはマージではなくリベースを行う

```python
git config --global pull.rebase preserve
```

そもそも`pull`は内部で`merge`を行っています。`pull`の動作を分解すると`fetch`&`merge`を順に行っています。

そして(1)の設定をしているので、`no-ff`マージをすることになります。

`pull`時に`no-ff`マージをすると、同一ブランチの最新を取り込むだけでも枝分かれしてマージされ、コミットメッセージのみの空っぽの余計なマージコミットが残ってしまうため、頻繁にプルを行う運用環境だと、それが大量に発生しログが非常に汚くなります。

それを回避するためにプルでは`rebase(git pull --rebase)`を使用こととします。**（プル以外でのrebaseは厳禁。）**

参考：[[Git] 使い分けできていますか？マージ（merge）&リベース（rebase）再入門 - The Powerful Code](http://powerful-code.com/blog/2012/11/merge-or-rebase/)

### (3)設定の確認

```python
git config --global --list
```

ちゃんと設定できているか、上記のコマンドで確認してください。  
きちんと設定できている場合、以下の記述があります。

```python
merge.ff=false
pull.rebase=preserve
```

## 画像でみる推奨設定

(1)と(2)が設定してあればSourceTreeのほうの設定は、**白文字で記述した部分以外（マージ時のリベース以外）**デフォルトのままで特に気にしなくてOKです。  
**白文字で指摘してある部分は厳守をよろしくお願いします。**

- [ ] 画像1
- [ ] 画像2
- [ ] 画像3

## まとめ

```python
# Reference by http://qiita.com/ponko2/items/9446b45d79cc78d7662d
# (1)git merge するときは常に --no-ff(1.7.6以降)
git config --global merge.ff false
# (2)git pull するときは常に rebase(1.8.5以降)
git config --global pull.rebase preserve

# もしくは以下で編集
git config --global --edit
# 一覧
git config --global --list
```
