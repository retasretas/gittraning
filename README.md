# gtitraning
Git traning

# Reference by http://qiita.com/ponko2/items/9446b45d79cc78d7662d
# git merge するときは常に --no-ff(1.7.6以降)
git config --global merge.ff false
# git pull するときは常に rebase(1.8.5以降)
git config --global pull.rebase preserve
# もしくは以下で編集
git config --global --edit
# 一覧
git config --global --list
