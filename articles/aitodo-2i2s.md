---
title: "プログラミング未経験の僕が、AIと雑談しながらTodoアプリを育ててみた話"
emoji: "📝"
type: "tech"
topics: ["AI", "プログラミング初心者", "個人開発", "Todoアプリ"]
published: true
---
# プログラミング未経験の僕が、AIと雑談しながらTodoアプリを育ててみた話

昨日の夜、ふと思い立って「自分だけのTodoアプリ」を作り始めたんです。

「AIってすごいらしいじゃん？」って最近よく聞くじゃないですか。でも、具体的に何ができるのか、プログラミング未経験の僕にはさっぱり分からなかったんですよね。そんな時にふと「もしAIと一緒になら、何か作れるんじゃないか？」って思ったんです。

それで、何を作るか考えたときに、一番シンプルで分かりやすいのがTodoアプリかなって。毎日使うものだし、自分好みにできたら便利だろうなって。ちょうど、ずっと使ってるTodoアプリがちょっと使いにくいなーって思ってたところだったんですよね。よし、やるなら今しかない！って感じで、AIに相談してみることにしたんです。

## まずはAIと「どんなアプリにする？」ってブレストから

AIに話しかけるのって、最初はちょっとドキドキしました。まるで、新しい友達に話しかけるみたいな感覚で。「プログラミング未経験なんだけど、Todoアプリ作りたいんだよね。どんな感じにしたらいいかな？」って、本当にざっくりした感じで聞いてみたんです。

そしたら、AIが「どんな機能が欲しいですか？」「どんな見た目にしたいですか？」って、まるでカフェで友達とアイデア出ししてるみたいに、色々質問してくれたんですよね。

:::message
AIとのブレストは、本当に想像以上にスムーズでした。最初から完璧な答えを期待するんじゃなくて、ざっくりとしたイメージを伝えるだけで、AIが具体的な質問で掘り下げてくれるのがすごく良かったですよ。
:::

例えば、「Todoの追加と削除は必須だよね。あとは、何だろう…」って僕が悩んでたら、AIが「完了したTodoにチェックマークをつけたり、色を変えたりするのはどうですか？」「優先度を設定できるようにしますか？」とか、次々に提案してくれて。

なんだか、自分一人で考えてたら絶対思いつかなかったようなアイデアもポンポン出てきて、めちゃくちゃ楽しかったんですよね。

## 「とりあえず動くもの」を目指して、AIにコードを書いてもらった結果…

ブレストが終わって、いよいよコードを書いてもらう段階に。正直、AIがどれくらいのコードを書いてくれるのか、半信半疑だったんです。

「じゃあ、まずは最小限のTodoアプリのコードを書いてみてくれる？」ってお願いしたら、本当に数秒でずらーっとコードが表示されて。

```javascript:todo-app.js
// これは最小限のTodoアプリのコードです。
// 通常はHTML、CSS、JavaScriptを組み合わせます。
// ここでは、JavaScriptのみで基本的な動作を示します。

class TodoApp {
    constructor() {
        this.todos = [];
        this.appElement = document.getElementById('app');
        this.render();
    }

    addTodo(text) {
        if (text) {
            this.todos.push({ text: text, completed: false });
            this.render();
        }
    }

    toggleComplete(index) {
        if (this.todos[index]) {
            this.todos[index].completed = !this.todos[index].completed;
            this.render();
        }
    }

    render() {
        this.appElement.innerHTML = ''; // アプリの内容をクリア

        const input = document.createElement('input');
        input.type = 'text';
        input.placeholder = '新しいTodoを追加';
        this.appElement.appendChild(input);

        const addButton = document.createElement('button');
        addButton.textContent = '追加';
        addButton.onclick = () => {
            this.addTodo(input.value);
            input.value = ''; // 入力フィールドをクリア
        };
        this.appElement.appendChild(addButton);

        const ul = document.createElement('ul');
        this.todos.forEach((todo, index) => {
            const li = document.createElement('li');
            li.textContent = todo.text;
            if (todo.completed) {
                li.style.textDecoration = 'line-through';
                li.style.color = 'gray';
            }
            li.onclick = () => this.toggleComplete(index);
            ul.appendChild(li);
        });
        this.appElement.appendChild(ul);
    }
}

// HTMLファイルで <div id="app"></div> が必要です
// const app = new TodoApp();
```

正直、「うわ、何これ…」って思いましたよ。意味不明な記号の羅列に見えて、一瞬「やっぱり僕には無理かな…」って心が折れそうになったんです。

でも、AIがすぐに「これはこういう意味のコードで、Todoを追加するためのボタンとリストを表示するものです」って丁寧に説明してくれて。さらに、「これをHTMLファイルに貼り付けてブラウザで開いてみてください」って具体的な手順まで教えてくれたんです。

言われた通りにやってみたら、本当に真っ白な画面に「新しいTodoを追加」っていう入力欄と「追加」ボタンが表示された時は、ちょっと感動しちゃいましたね。あの瞬間は忘れられないです。

:::message alert
AIが生成したコードをそのまま使うときは、セキュリティや動作の安定性を確認するのが大事だよ、って言われました。僕の場合は趣味の個人開発だったので、とりあえず動くことを優先しちゃいましたけど、仕事で使う場合は注意が必要みたいです。
:::