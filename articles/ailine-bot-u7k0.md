---
title: "プログラミング未経験の私が、AIとLINE Bot作りの珍道中！友達を驚かせた全記録"
emoji: "📝"
type: "tech"
topics: ["tech"]
published: true
---
プログラミング未経験の私が、AIとLINE Bot作りの珍道中！友達を驚かせた全記録

# プログラミング未経験の私が、AIとLINE Bot作りの珍道中！友達を驚かせた全記録

プログラミングなんて全く分からない私が、AIと一緒にLINE Botを作って友達に自慢するまでの、笑いと涙（？）の珍道中をレポートします。

もしあなたが「AIで何か作ってみたいけど、プログラミングはちょっと…」とか、「友達をあっと言わせる何かを仕掛けたい！」なんて思っているなら、ぜひこの記事を読んでみてください。私みたいなド素人でもできたんだから、きっとあなたにもできますよ！

## きっかけは些細なことだった。〜AIとLINE Botに惹かれた理由〜

私の日常は、プログラミングとは全く縁がない、ごく普通のOL生活でした。Excelで関数をコピペするのが精一杯、みたいな。そんな私がなぜAIとLINE Botに興味を持ったのか、そのきっかけは本当に些細なことだったんです。

ある日のこと、友達とカフェでおしゃべりしてた時のこと。
「最近さ、ChatGPTってすごいよね。なんでも答えてくれるし、文章も作ってくれるんだって」
「へー、そんなのあるんだ。でも私には関係ない世界の話かなぁ」
なんて、他人事みたいに話してたんです。

でも、友達の一言が私の心に引っかかりました。
「ねえ、これ使ってさ、なんか面白いことできないかな？たとえば、LINEで話しかけると、面白い返事してくれるBotとか！」

その瞬間、私の頭の中で何かがカチッと音を立てました。「LINE Botかぁ…面白そう！」
これまでAIは「賢いけど、自分には使いこなせないもの」ってイメージだったんですが、友達を驚かせるツールとして考えたら、なんだかワクワクしてきたんです。プログラミングの知識はゼロ。でも、AIが手伝ってくれるなら、もしかしたら私にもできるんじゃないか？そんな淡い期待が、私の珍道中の始まりでした。

## 右も左も分からない！AIに「丸投げ」してみた最初の試み

「LINE Botを作るぞ！」と意気込んだものの、正直、何から手をつけていいのか全く分かりませんでした。まるで深い森に一人放り込まれたような気分。途方に暮れた私は、とりあえずAI（ChatGPT）に「丸投げ」してみることにしました。

深夜2時、眠い目をこすりながら、スマホでChatGPTを開き、恐る恐るこう入力してみました。

```text
LINE Botを作りたいんだけど、どうすればいい？プログラミングは全く分かりません。
```

すると、すぐに返事が返ってきました。

:::message
ChatGPTは、プログラミングの知識がない人にも分かりやすく、手順を細かく教えてくれます。まるで専属の先生がいるみたいで、最初は感動しました！
:::

返ってきた内容は、衝撃的でした。LINE Developersの登録、Messaging APIの有効化、ngrok（これは後で知ったけど、ローカル環境を外部に公開するためのツールらしい）のインストール、Pythonでのコード記述…と、専門用語のオンパレード！

「え、なにこれ？日本語？」

正直、最初は何を言っているのか半分も理解できませんでした。「Messaging API？」「ngrok？」「Python？」もう頭の中はハテナマークだらけ。

でも、そこで諦めなかったのは、AIが「一つずつ丁寧に説明します」って言ってくれたから。まるで手取り足取り教えてくれる先生みたいで、少しだけ安心したんです。よし、ChatGPT先生を信じて、言われた通りにやってみよう！そう決意したのが、私の第一歩でした。

## 「バイブコーディング」の誕生？AI先生との二人三脚開発

AIが教えてくれたコードを、言われるがままにコピペしてはエラーを吐き、またAIに相談する…という、私独自の「バイブコーディング」と名付けた（？）開発スタイルが確立されていきました。

まず、言われた通りにPythonをインストール。これはなんとかできた。
次に、LINE Developersのサイトにアクセスして、Botのチャネルを作ったり、APIのキーを発行したり…もうこの辺から怪しい日本語が出てきて、ChatGPTに逐一「これってどういう意味？」「どこをクリックすればいいの？」って聞きまくりました。

例えば、こんな感じのやりとりです。

```text
私: LINE Developersでチャネルシークレットってどこにあるの？
ChatGPT: チャネル設定画面の「Basic settings」タブ内に「Channel Secret」という項目があります。
私: 見つからないんだけど…
ChatGPT: スクリーンショットを送っていただけますか？（実際には送れないけど、状況を詳しく教えてほしいという意味で）
```

こんな風に、まさに二人三脚。AIがコードを教えてくれるたびに、私はそれをコピーして、自分のPCに貼り付けます。

```python:app.py
from flask import Flask, request, abort
from linebot import LineBotApi, WebhookHandler
from linebot.exceptions import InvalidSignatureError
from linebot.models import MessageEvent, TextMessage, TextSendMessage

app = Flask(__name__)

# ここにあなたのチャネルアクセストークンとチャネルシークレットを設定
LINE_CHANNEL_ACCESS_TOKEN = "YOUR_CHANNEL_ACCESS_TOKEN"
LINE_CHANNEL_SECRET = "YOUR_CHANNEL_SECRET"

line_bot_api = LineBotApi(LINE_CHANNEL_ACCESS_TOKEN)
handler = WebhookHandler(LINE_CHANNEL_SECRET)

@app.route("/callback", methods=['POST'])
def callback():
    signature = request.headers['X-Line-Signature']
    body = request.get_data(as_text=True)
    app.logger.info("Request body: " + body)

    try:
        handler.handle(body, signature)
    except InvalidSignatureError:
        abort(400)

    return 'OK'

@handler.add(MessageEvent, message=TextMessage)
def handle_message(event):
    line_bot_api.reply_message(
        event.reply_token,
        TextSendMessage(text=event.message.text)
    )

if __name__ == "__main__":
    app.run(port=8080)
```
:::details 補足：このコードは何をしているの？
このPythonコードは、LINEからのメッセージを受け取って、そのままオウム返しするシンプルなLINE Botのプログラムです。

- `Flask`: ウェブアプリケーションを作るためのフレームワーク。
- `linebot`: LINE Messaging APIを簡単に使うためのライブラリ。
- `@app.route("/callback", methods=['POST'])`: LINEからのメッセージが届くと、ここに送られてくるように設定します。
- `@handler.add(MessageEvent, message=TextMessage)`: テキストメッセージが来たときに動く部分。
- `TextSendMessage(text=event.message.text)`: 届いたメッセージの内容をそのまま返信する、という意味です。

最初は呪文にしか見えなかったけど、AIが一つずつ説明してくれるおかげで、なんとなく「これはメッセージを受け取る部分」「これは返信する部分」って理解できるようになりました。
:::

そして実行！すると…エラー！

```bash:bash
$ python app.py
Traceback (most recent call last):
  File "app.py", line 1, in <module>
    from flask import Flask, request, abort
ModuleNotFoundError: No module named 'flask'
```

「なんだこれ！？」

もちろん、エラーの意味なんて全く分かりません。すかさずChatGPTにエラーメッセージをコピペして質問。

```text
私: ModuleNotFoundError: No module named 'flask' って出たんだけど、どうすればいい？
ChatGPT: それは、Flaskというライブラリがインストールされていないからです。以下のコマンドを実行してください。
```

```bash:bash
pip install flask line-bot-sdk
```

言われた通りにコマンドを実行。すると、またエラー！
「え、また？！」

こんな感じで、コピペしてはエラー、エラーが出たらAIに質問、言われた通りに修正…というのを繰り返しました。時には「これ、本当に動くようになるの？」と心が折れそうになることも。特に、`ngrok`の設定は本当に意味不明で、なぜ外部に公開する必要があるのか、全く理解できませんでした。

:::message alert
`ngrok`を使う際は、セキュリティに注意が必要です。一時的に外部に公開するツールなので、作業が終わったら必ず停止しましょう。私は、よく停止し忘れて寝てしまい、次の日に慌てて停止する、なんてこともありました…（笑）
:::

でも、少しずつ、本当に少しずつですが、コードの意味が分かってくる瞬間があったんです。「あ、ここがBotの返事の内容を決める部分なんだな」とか、「ここがLINEからのメッセージを受け取る場所なんだな」とか。それがもう、宝物を見つけたような感覚でした。