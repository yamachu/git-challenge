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
その後、`step2b` の PullRequest を見てみましょう。

ここで、ファイルのコンフリクトが起きていることがわかります。

これを解消してみましょう。

GitHub 上でも行うことが出来ますが、手元のエディタで今回は解消してみましょう。

```sh
$ git fetch origin main:main
```

で main ブランチを最新にしてください。
その後、`step2b` ブランチ上で

```sh
$ git merge main
```

を行うと、正常に merge が出来ずにコンフリクトの解消を求められます。

エディタで `work/answer.txt` を開くと、以下のような状態になっているはずです。

```txt
<<<<<<< HEAD
6
7
8
9
=======
?
6
?
8
?
>>>>>>> main
```

`<<<<<<< HEAD` から `=======` までが `step2b` ブランチの変更で、`=======` から `>>>>>>> main` までが `main` ブランチの変更です。

今回は `step2b` ブランチの変更を取り込みたいので、Accept Current Change を選択してください。

このコンフリクト解消は単純なものであるため、`Accept Current Change` を選択するだけで解消出来ますが、ソースコードの書き換えの場合は単純にいかないこともあります。

Accept Both Changesを選択し修正することが多くの場合でしょう。
変更をよく確認して、正しく修正してください。
