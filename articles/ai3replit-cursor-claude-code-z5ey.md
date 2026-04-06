---
title: "プログラミング未経験の僕が、AI開発ツール3つをガチ比較した結果…！【Replit, Cursor, Claude Code】"
emoji: "📝"
type: "tech"
topics: ["AI開発", "プログラミング初心者", "Replit", "Cursor", "Claude"]
published: true
---
# プログラミング未経験の僕が、AI開発ツール3つをガチ比較した結果…！【Replit, Cursor, Claude Code】

## 結論から言うと…ぶっちゃけ○○一択！と言いたいけど、そう単純じゃなかった話

プログラミング未経験の僕が、巷で話題のAI開発ツール3つを実際に触ってみて感じた「ぶっちゃけどうなの？」という率直な感想と、一番コスパの良いツールはどれだったのかを序盤で提示します。

プログラミングの「プ」の字も知らなかった僕が、最近話題の「AIで開発」ってやつに手を出してみたんです。正直、「AIがコード書いてくれるなら、俺でもできるんじゃね？」くらいの軽い気持ちでした。だって、ガジェット好きとしては最新ツールは試したいじゃないですか。

今回、僕がガチで使い倒したのはこの3つ。
1.  **Replit (レプリット)**
2.  **Cursor (カーソル)**
3.  **Claude Code (クロード コード)**

この3つを、まるで新しいゲーミングPCやスマホをレビューするかのごとく、使い心地からコスパまで徹底的に検証しました。結論から言っちゃうと、「これ一択！」って単純な話じゃなかったんです。それぞれのツールに「あ、これは神！」ってなる瞬間と、「うわ、まじか…」って頭を抱える瞬間があって。

この記事では、プログラミング未経験の僕が、どんなところで感動して、どんなところでつまずいたのかを、ガジェットレビュアー並みの辛口レビューでぶっちゃけていきます。あなたが「AIで開発」を始めたいと思ってる超初心者なら、きっとこの記事が最高の参考書になるはず。だって、僕もつい最近まであなたと同じ立場だったから！

## 【レビュー①】Replitは「全部入りゲーミングPC」？ワクワクするけど、ちょっと重いかも…

Replitを触ってみた体験談。環境構築不要で手軽に始められる良さや、多機能ゆえの戸惑い、AIチャットの使い勝手などをガジェットレビュアー目線で語ります。正直な感想もズバッと言っちゃいます。

まず最初に手をつけたのがReplit。なんせ「環境構築不要！ブラウザで即開発！」って謳い文句が魅力的すぎたんです。新しいPC買ったら電源入れてすぐゲームしたいじゃないですか？そんなノリで始められました。

Replitにアクセスして、言語を選んでポチッとするだけで、はい、もう開発環境が目の前に！これは感動モノでしたね。本当に何も準備いらないんだもん。

:::message
Replitはブラウザ上で動作する統合開発環境（IDE）。Python、JavaScript、HTML/CSSなど、様々な言語に対応していて、コードの記述から実行、デプロイまで一貫して行えるのが特徴。特にAI機能が充実していて、コード生成やデバッグをAIがサポートしてくれます。
:::

僕が最初に試したのはPythonでの簡単なウェブアプリ開発。AIチャットに「Pythonで簡単な電卓アプリを作って、ウェブブラウザで動かしたい」って入力してみたら、サクサクとコードを生成してくれたんです。

```python:main.py
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def index():
    result = None
    if request.method == 'POST':
        try:
            num1 = float(request.form['num1'])
            num2 = float(request.form['num2'])
            operation = request.form['operation']

            if operation == 'add':
                result = num1 + num2
            elif operation == 'subtract':
                result = num1 - num2
            elif operation == 'multiply':
                result = num1 * num2
            elif operation == 'divide':
                if num2 != 0:
                    result = num1 / num2
                else:
                    result = "Error: Division by zero"
        except ValueError:
            result = "Error: Invalid input"
    return render_template('index.html', result=result)

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=81)
```
```html:templates/index.html
<!DOCTYPE html>
<html>
<head>
    <title>Simple Calculator</title>
    <style>
        body { font-family: sans-serif; margin: 20px; }
        input[type="text"] { width: 100px; padding: 5px; margin: 5px; }
        button { padding: 8px 15px; margin: 5px; }
    </style>
</head>
<body>
    <h1>Simple Calculator</h1>
    <form method="POST">
        <input type="text" name="num1" placeholder="Number 1" required>
        <select name="operation">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">*</option>
            <option value="divide">/</option>
        </select>
        <input type="text" name="num2" placeholder="Number 2" required>
        <button type="submit">Calculate</button>
    </form>
    {% if result is not None %}
        <h2>Result: {{ result }}</h2>
    {% endif %}
</body>
</html>
```
@[card](https://replit.com/@replit/Python)

Replitの画面は、左側にファイルエクスプローラー、中央にコードエディタ、右側にコンソールやAIチャット、そして実行結果のウェブビューが表示される「全部入り」な感じ。まさにゲーミングPCのデスクトップみたいで、いろんな機能がギュッと詰まってる。

ただ、多機能ゆえの戸惑いも正直ありました。どこに何があるのか、最初はちょっと迷う。AIチャットも優秀なんだけど、たまに「ん？なんでこうなるの？」って首を傾げる挙動もあって。僕がプログラミングの知識がなさすぎるせいもあるんですけどね。

一番気になったのは、ブラウザで動くとはいえ、そこそこリソースを食うのか、たまに動作がもっさりする瞬間があったこと。特にAIを多用すると、処理に時間がかかる時もあって、「もうちょっとサクサク動いてくれよ～」って思っちゃいました。まるで買ったばかりのゲーミングPCが、設定ミスでカクつくみたいな。

**Replitをガチレビューした僕の結論:**
*   **良い点:** 環境構築不要で即スタートできるのは神。AI機能も強力で、簡単なアプリならサクサク作れる。デプロイまでできるのはすごい。
*   **悪い点:** 多機能すぎて初心者は迷うことも。動作が若干重く感じることがある。AIの生成コードを理解するための基礎知識はやっぱり必要。

プログラミング未経験の僕からすると、「AIで開発ってこういうことか！」って感動を味わえるツールだけど、完璧ではない。例えるなら、全部入りのゲーミングPCだけど、設定をいじくり回す楽しさも含めて「ちょっと玄人向け」かな？