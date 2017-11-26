---
title: "How to Use Hugo"
date: 2017-11-26T23:02:16+09:00
---

# Hugoの使い方

Officialの[Quick Start](https://gohugo.io/getting-started/quick-start/)通りでサクッとできます。  
Go言語一切知らなくてもできます。  
便利です。

## インストールと起動(Macの場合)

```shellsession
$ brew install Hugo
```

しておもむろに任意のディレクトリで

```shellsession
$ hugo new site .
```

するだけで準備は完了です。

注意点としては、このディレクトリはGitで管理しておくと便利で、またテーマを追加しないとただの真っ白なページが表示されて焦ることになります(なりました)。

テーマをGitのsubmoduleとして追加するには以下のようにします。  
( `hugo-theme-docdock` テーマを使うとこのサイトと同じような見た目になります)

```shellsession
$ git submodule add https://github.com/vjeantet/hugo-theme-docdock.git themes/docdock
```

`config.toml` に以下の行を追記します。

```
theme = "docdock"
```

その後ローカルでHugoのサーバーを起動し表示を確認します。  
`Web Server is available at ` に書かれているURLにアクセスすると表示が確認できます。  
便利ですね。

なお `-D` または `--buildDrafts` はdraftなPostも表示するオプションです、たぶん。

```shellsession
$ hugo server -D
Started building sites ...

Built site for language en:
2 of 2 drafts rendered
0 future content
0 expired content
3 regular pages created
8 other pages created
0 non-page files copied
1 paginator pages created
0 tags created
0 categories created
total in 8 ms
Watching for changes in /path/to/your/working/directory/{data,content,layouts,static,themes}
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at //localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

なお、このWebサイトの[設定ファイルはここ](https://github.com/mazgi/example-document-with-hugo/blob/master/docs.source/config.toml)にあります。

## Postの追加

`hugo server` コマンドを実行したのと同じディレクトリ上で以下のようにコマンドを実行するとPostを追加できます。

```shellsession
$ hugo new posts/title-of-your-post.md
```

コマンドを実行すると(設定を変えていなければ)以下のような内容で `content/posts/title-of-your-post.md` というファイルが生成されます。

```
---
title: "Title of Your Post"
date: 2017-11-26T23:02:25+09:00
---

```

好きなようにMarkdownを書きましょう。  
保存すると先ほどのURLで即時確認できます。  
便利ですね。

なおこの記事もHugoの1つのPostですが[Markdown形式のソースはここ](https://github.com/mazgi/example-document-with-hugo/blob/master/docs.source/content/posts/how-to-use-hugo.md)にあります(予定)。

## GitHub Pagesとして公開するだけで

Postのファイルから以下の行を削ります。  
( `false` に変えてもいいんでしょう、きっと)

```
draft: true
```

そして `hugo` コマンドを実行します。

```shellsession
$ hugo
Started building sites ...

Built site for language en:
0 of 2 drafts rendered
0 future content
0 expired content
1 regular pages created
8 other pages created
0 non-page files copied
1 paginator pages created
0 tags created
0 categories created
total in 10 ms
```

StaticなHTML他が生成されました。  
速いですね。


GitHub Pagesの場合、あとは `commit` して `push` するだけです。
