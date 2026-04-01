---
title: "プログラミング知識ゼロの僕がClaude Codeで個人開発を始めたら、まさかの結果に！"
emoji: "📝"
type: "tech"
topics: ["tech"]
published: true
---
プログラミング知識ゼロの僕がClaude Codeで個人開発を始めたら、まさかの結果に！

# プログラミング知識ゼロの僕がClaude Codeで個人開発を始めたら、まさかの結果に！

結論から言うと、Claude Codeは神ツール…と言いたいところだけど、そう単純じゃない。

AI個人開発に憧れて、プログラミング知識ゼロの僕がClaude Codeに飛び込んだ率直な感想を、ガジェットレビューのノリで語らせてほしい。

「プログラミング？いや、AIに作ってもらえばよくね？」

そんな軽い気持ちでAI個人開発の世界に足を踏み入れた僕。使うツールは、巷で話題の「Claude Code」。なんかすごそうじゃん？ってのが選んだ理由の8割くらいを占めてる。でも、実際に使ってみてわかったのは、想像してたのとはちょっと違う、奥深い世界がそこにあったってことだ。正直、最初は「これ、本当に使えるの？」って半信半疑だったんだよね。

この記事は、僕みたいな「AIでなんか作ってみたいけど、何から始めたらいいの？」って思ってる、プログラミング未経験〜始めて半年の超初心者向け。僕の試行錯誤と、そこから見えてきたClaude Codeのリアルな姿を、忖度なしでレビューしていくよ。

## 「バイブコーディング」って何？AIに丸投げ開発の衝撃と戸惑い

僕がClaude Codeで始めたのは、まさに「バイブコーディング」と呼ぶにふさわしい体験だった。バイブコーディングって何かって？それはね、プログラミングを「書く」のではなく「感じる」ようにAIと対話しながら開発すること。

最初に「こんなアプリ作りたいんだけど」ってざっくり伝えたら、Claude Codeが「じゃあ、こういう機能が必要ですね。コードはこんな感じでどうですか？」って、ものの数秒で返してきたのにはマジでビビった。

:::message
僕はまず、手始めに「簡単なTODOリストアプリ」を作ろうと決めたよ。理由は、機能がシンプルでイメージしやすかったから。いきなり複雑なものに挑戦すると挫折しちゃうからね。
:::

僕がやったことといえば、ひたすら「もっとこうしてほしい」「ここは違う」ってAIにフィードバックするだけ。まるで熟練の職人が弟子に指示を出すみたいにね。でも、指示を出す側がプログラミング知識ゼロだから、最初は戸惑いの連続だった。

例えば、「ボタンを押したらリストに追加されるようにしたい」って伝えると、Claude CodeはHTML、CSS、JavaScriptのコードをまとめて出してくる。

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TODOリスト</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>シンプルなTODOリスト</h1>
        <input type="text" id="todoInput" placeholder="新しいタスクを入力">
        <button id="addButton">追加</button>
        <ul id="todoList"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>
```text

```css
/* style.css */
body {
    font-family: sans-serif;
    background-color: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
}

.container {
    background-color: #fff;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    width: 400px;
    max-width: 90%;
}

h1 {
    text-align: center;
    color: #333;
    margin-bottom: 20px;
}

#todoInput {
    width: calc(100% - 70px);
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    margin-right: 10px;
}

#addButton {
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

#addButton:hover {
    background-color: #0056b3;
}

#todoList {
    list-style: none;
    padding: 0;
    margin-top: 20px;
}

#todoList li {
    background-color: #f9f9f9;
    padding: 10px;
    border-bottom: 1px solid #eee;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

#todoList li:last-child {
    border-bottom: none;
}

.deleteButton {
    background-color: #dc3545;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 4px;
    cursor: pointer;
}

.deleteButton:hover {
    background-color: #c82333;
}
```text

```javascript
// script.js
document.addEventListener('DOMContentLoaded', () => {
    const todoInput = document.getElementById('todoInput');
    const addButton = document.getElementById('addButton');
    const todoList = document.getElementById('todoList');

    addButton.addEventListener('click', addTodo);
    todoInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') {
            addTodo();
        }
    });

    function addTodo() {
        const todoText = todoInput.value.trim();
        if (todoText === '') {
            alert('タスクを入力してください！');
            return;
        }

        const listItem = document.createElement('li');
        listItem.textContent = todoText;

        const deleteButton = document.createElement('button');
        deleteButton.textContent = '削除';
        deleteButton.classList.add('deleteButton');
        deleteButton.addEventListener('click', () => {
            todoList.removeChild(listItem);
        });

        listItem.appendChild(deleteButton);
        todoList.appendChild(listItem);
        todoInput.value = ''; // 入力欄をクリア
    }
});
```text

正直、このコードが何をしてるのか、最初は全然わからなかった。HTMLが骨組み、CSSが見た目、JavaScriptが動き、くらいはなんとなく知ってたけど、具体的にどの行がどう作用してるのかはちんぷんかんぷん。でも、指示通りにファイルを作ってブラウザで開いたら、ちゃんと動くんだよ。これには感動したね。「え、僕、プログラミングできたんじゃね？」って錯覚するレベル。

AIに丸投げ開発は、まさに新しい体験だった。コードを「書く」のではなく、「動くもの」としてイメージし、AIとの対話を通じて具現化していく感覚。これは、従来のプログラミング学習とは全く違うアプローチだ。深夜2時にふと思い立って、スマホからポチポチ指示を出すだけでも、それっぽいものができていく。これは新しい！って素直に思ったね。