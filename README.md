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

## 2. コンフリクトを起こして、解消してみよう

`git switch main` で main ブランチに戻って、`git pull` で main ブランチを最新にしましょう。
その後、`step2a` というブランチを作成しましょう。

以下のコマンドでファイルを更新します。

```sh
$ make init/step2a
```

この状態で、`work/answer.txt` を `git add` し、`git commit` でコミットしましょう。
その後 `git push` し、GitHub 上で PullRequest を作ってみましょう。

まだmergeしてはいけません。

次に、`git switch main` で main ブランチに戻ってください。
その後、`step2b` というブランチを作成します。

`work/answer.txt` の内容を以下のように変更してください。

```txt
1
2
3
4
5
6
7
8
9
10
```

その後同様に `git add` と `git commit` を行い、`git push` し、GitHub 上で PullRequest を作ってみましょう。

まずは `step2a` の PullRequest をmergeしてみましょう。
