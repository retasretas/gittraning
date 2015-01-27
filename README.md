# gtitraning
Git traning

(1)と(2)が設定してあればSourceTreeのほうの設定はマージ時のリベース以外デフォルトのままで特に気にしなくてOK.

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
