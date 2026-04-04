---
title: "【爆死】「AI使えば誰でもエンジニア」を信じたプログラミング未経験の僕が、地獄を見た1ヶ月間"
emoji: "📝"
type: "tech"
topics: ["tech"]
published: true
---
【爆死】「AI使えば誰でもエンジニア」を信じたプログラミング未経験の僕が、地獄を見た1ヶ月間

# 【爆死】「AI使えば誰でもエンジニア」を信じたプログラミング未経験の僕が、地獄を見た1ヶ月間

正直に言います。最初は完全にAIをナメてました。

「AIを使えば誰でもエンジニアになれる！」

そんな甘い言葉を鵜呑みにして、プログラミング経験ゼロの僕が個人開発に挑んだ1ヶ月間。結果は……見事に爆死でした。AIに振り回され、エラーの沼に沈み、深夜に頭を抱え続けた地獄の日々を、今から赤裸々に告白します。

この記事は、僕と同じように「AIに作ってもらおう」と考えている、プログラミング未経験〜始めて半年以内の初心者のあなたに向けて書きました。僕の失敗談が、あなたの爆死を少しでも回避するヒントになれば嬉しいです。

## 正直に言います。最初は完全にAIをナメてました

話は1ヶ月前に遡ります。
当時、僕は「何か新しいことに挑戦したい」という漠然とした思いを抱えていました。そんな時、SNSで目にしたのが「AIがあれば、コードが書けなくてもアプリが作れる！」というキラキラした言葉です。

「え、マジで？ これなら俺にもできるんじゃね？」

プログラミングの「プ」の字も知らない僕でしたが、一瞬で心が踊りました。だって、今までプログラミングって、謎の呪文をカタカタ入力する超絶難しいものだと思ってたから。それがAIの力で、まるで魔法のように実現できるなんて、夢のようじゃないですか。

「よし、AIを使って個人開発者としてデビューだ！」

僕は根拠のない自信に満ち溢れ、ワクワクしながらAIとの開発生活をスタートさせました。もちろん、具体的なアイデアなんて何もありません。とりあえず「なんかすごいアプリ」を作りたい、とだけ思ってました。今思えば、この時点でかなりイタい思考回路だったと反省しています。

:::message
僕がAIに個人開発を丸投げしようと思ったのは、ちょうど話題になり始めた頃で、SNSで「AIで爆速開発！」みたいな記事がバズってたのがきっかけでした。あの頃は本当に夢見てたなぁ……。
:::

## 『AI先生、アプリ作ってください！』→爆誕したのは「動かないゴミコードの山」

意気揚々とAIチャットを開き、僕が最初にAIに投げかけたプロンプトは、今振り返ると本当にアホらしいものでした。

```text
AI先生、チャットアプリを作ってください！
デザインはかっこよくて、機能はたくさんあるやつがいいです！
```

完璧な丸投げですね。
しかし、AIはそんな無茶な要望にも律儀に答えてくれました。
数秒後、画面にはズラズラと大量のコードが表示されたのです。

「おおおおお！すごい！これがAIの力か！」

僕は感動しました。まさかこんなに簡単にコードが出てくるとは。
早速、指示された通りにファイルをいくつか作成し、コードをコピペしていきます。
そして、いよいよ実行の時。ドキドキしながらターミナルでコマンドを打ち込みました。

```bash:terminal
node app.js
```

しかし、画面に表示されたのは、期待していたチャットアプリの画面ではなく、おびただしい数のエラーメッセージでした。

```text
Error: Cannot find module 'express'
    at Function.Module._resolveFilename (node:internal/modules/cjs/loader:1143:15)
    at Function.Module._load (node:internal/modules/cjs/loader:984:27)
    at Module.require (node:internal/modules/cjs/loader:1232:19)
    at require (node:internal/modules/cjs/helpers:102:18)
    at Object.<anonymous> (/path/to/your/app.js:3:17)
    at Module._compile (node:internal/modules/cjs/loader:1369:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1427:10)
    at Module.load (node:internal/modules/cjs/loader:1206:32)
    at Function.Module._load (node:internal/modules/cjs/loader:1027:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:139:12)
```

「え、なにこれ？！」

僕は混乱しました。AIがくれたコードは、動かないゴミコードの山だったのです。
しかも、エラーメッセージの意味が全く理解できません。「cannot find module 'express'」？ モジュール？ エクスプレス？ なにそれ美味しいの？ 状態です。

そこからが、僕とエラーとの長い長い格闘の始まりでした。
エラーメッセージをAIに投げ、その解決策として提示されたコードをコピペし、また別のエラーが出て……という無限ループ。

:::details 僕が初めてAIに丸投げして爆死した時のプロンプトと、AIの回答（一部抜粋）
```text
AI先生、チャットアプリを作ってください！
デザインはかっこよくて、機能はたくさんあるやつがいいです！
```

---

はい、承知いたしました。Node.jsとExpress、Socket.IOを使ったシンプルなチャットアプリの基本的なコードを提供します。このコードはサーバーサイドとクライアントサイドに分かれています。

**1. サーバーサイド (app.js)**

```javascript:app.js
const express = require('express');
const http = require('http');
const socketIo = require('socket.io');

const app = express();
const server = http.createServer(app);
const io = socketIo(server);

app.use(express.static(__dirname + '/public'));

app.get('/', (req, res) => {
    res.sendFile(__dirname + '/public/index.html');
});

io.on('connection', (socket) => {
    console.log('A user connected');

    socket.on('chat message', (msg) => {
        io.emit('chat message', msg);
    });

    socket.on('disconnect', () => {
        console.log('User disconnected');
    });
});

const PORT = process.env.PORT || 3000;
server.listen(PORT, () => {
    console.log(`Server running on port ${PORT}`);
});
```

**2. クライアントサイド (public/index.html)**

```html:public/index.html
<!DOCTYPE html>
<html>
<head>
    <title>AI Chat App</title>
    <style>
        body { margin: 0; padding-bottom: 3rem; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; }
        #form { background: rgba(0, 0, 0, 0.15); padding: 0.25rem; position: fixed; bottom: 0; left: 0; right: 0; display: flex; height: 3rem; box-sizing: border-box; backdrop-filter: blur(10px); }
        #input { border: none; padding: 0 1rem; flex-grow: 1; border-radius: 2rem; margin: 0.25rem; }
        #input:focus { outline: none; }
        #form > button { background: #333; border: none; padding: 0 1rem; margin: 0.25rem; border-radius: 3px; outline: none; color: #fff; }
        #messages { list-style-type: none; margin: 0; padding: 0; }
        #messages > li { padding: 0.5rem 1rem; }
        #messages > li:nth-child(odd) { background: #efefef; }
    </style>
</head>
<body>
    <ul id="messages"></ul>
    <form id="form" action="">
        <input id="input" autocomplete="off" /><button>Send</button>
    </form>
    <script src="/socket.io/socket.io.js"></script>
    <script>
        var socket = io();

        var form = document.getElementById('form');
        var input = document.getElementById('input');
        var messages = document.getElementById('messages');

        form.addEventListener('submit', function(e) {
            e.preventDefault();
            if (input.value) {
                socket.emit('chat message', input.value);
                input.value = '';
            }
        });