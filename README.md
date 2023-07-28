# git-challenge

## 1. ブランチ作成、コミットをしてみよう

`step1` というブランチを作成しましょう。

```sh
$ git switch -c step1
```

以下のコマンドでファイルを作成してください。

```sh
$ make init/step1
```

この状態で、`work/answer.txt` を `git add` し、`git commit` でコミットしましょう。
その後 `git push` し、GitHub 上で PullRequest を作ってみましょう。

`gh` コマンドが入っている場合は

```sh
$ gh pr create --title "step1の回答"
```

で PullRequest を作成することも出来ます。

GitHub Actionsのテストが通ったらmergeしましょう。
