---
title: "プログラミング未経験の僕が、AIと3日間チャットして「自分だけのTodoアプリ」を育ててみた話"
emoji: "📝"
type: "tech"
topics: ["tech"]
published: true
---
プログラミング未経験の僕が、AIと3日間チャットして「自分だけのTodoアプリ」を育ててみた話

# プログラミング未経験の僕が、AIと3日間チャットして「自分だけのTodoアプリ」を育ててみた話

昨日の夜、ふと思い立って「AIとTodoアプリ開発」を始めてみたんです。プログラミングの知識ゼロの僕が、まさかAI相手に「こんなアプリ作りたい！」と話しかけてみるなんて、数日前までは想像もしてなかったことなんだけど。

なんで急にって？いや、普段からタスク管理はしてたんだけど、市販のアプリだと「なんかちょっと違うんだよな〜」みたいな不満がずっとあったんですよね。でも自分で作るとか無理じゃん、って諦めてたんだけど、最近AIがすごいって聞くから、もしかして…？って。

正直、何から始めたらいいか全くわからなかったんです。AIに「Todoアプリ作りたい」って言えば、それだけで形になるわけないし。でも、とりあえず聞いてみよう、ダメ元で、くらいの気持ちでした。

## 昨日の夜、ふと思い立って「AIとTodoアプリ開発」を始めてみた

深夜2時くらいだったかな。ベッドに入ってスマホいじってたら、急に思い立ってAIチャットを立ち上げました。

僕「なんか、自分だけのTodoアプリ作りたいんだけど、プログラミングとか全然わかんないんだよね。AIとチャットしながら作れるかな？」

結構ざっくりした質問なんだけど、AIはすぐに返事をくれました。

AI「はい、可能です！一緒にTodoアプリを作っていきましょう。まずは、どんなTodoアプリにしたいか、具体的なイメージを教えてください。」

おー、マジか！なんか、いけそうな気がしてきたぞ。

僕「えっとね、シンプルでいいんだけど、タスクを追加できて、終わったら消せるやつ。あと、今日やるタスクと、いつかやるタスクを分けたいな。」

こんな感じで、本当に友達と話すみたいに、作りたいもののイメージを伝えていきました。AIは、僕の曖昧な言葉を汲み取って、具体的な機能に落とし込もうとしてくれるんです。

:::message
**AIとのチャットは、まるで共同作業。**
最初から完璧な指示を出そうとしなくても大丈夫。作りたいもののイメージをざっくり伝えて、AIからの質問に答えていくうちに、だんだん具体化していきます。
:::

## AIくん、まさかの「コード」をくれる！これ、どうすればいいの？

いくつかやり取りを重ねて、AIが「では、まずはタスクを追加する機能から作ってみましょう」と言って、いきなりコードの塊を送ってくれたんですよ。

:::details コードの例（最初のバージョン）
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Todo App</title>
</head>
<body>
    <h1>My Todo List</h1>
    <input type="text" id="taskInput" placeholder="新しいタスクを入力">
    <button onclick="addTask()">追加</button>
    <ul id="taskList">
        <!-- タスクがここに追加されます -->
    </ul>

    <script>
        function addTask() {
            const taskInput = document.getElementById('taskInput');
            const taskText = taskInput.value.trim();
            if (taskText === '') {
                alert('タスクを入力してください！');
                return;
            }

            const taskList = document.getElementById('taskList');
            const listItem = document.createElement('li');
            listItem.textContent = taskText;
            taskList.appendChild(listItem);
            taskInput.value = ''; // 入力欄をクリア
        }
    </script>
</body>
</html>
```
:::

正直、「は？これ、どこに貼り付ければ動くの？」って焦りました。だって、プログラミングなんて全くやったことないから、ファイルを作るって言われても、どうやって作るのかもわからない。

僕「あの、これ、どこに書けばいいんですか？あと、どうやって開けばいいんですか？」

AI「このコードはHTMLファイルとして保存してください。例えば、`index.html`という名前で保存し、そのファイルをウェブブラウザで開けば動きますよ。」

なるほど！言われた通り、パソコンのメモ帳に貼り付けて、`index.html`って名前で保存。そしてそのファイルをダブルクリックしてみたら…

おおお！ブラウザが立ち上がって、入力欄とボタンがある！感動！

入力欄に「牛乳買う」って入れて「追加」ボタンを押すと、ちゃんとリストに表示される！すごい！なんか、ゲームやってるみたいでめっちゃ面白かったんですよね。

:::message alert
**AIが生成したコードを動かす際の注意点**
AIが教えてくれるコードは基本的に安全なものが多いですが、不特定多数から提供されたコードを安易に実行するのはリスクを伴う場合があります。今回はローカル環境で動かす簡単なコードなので問題ありませんが、例えばWebサイトに公開するような場合は注意が必要です。
:::

## 「タスク追加」まではできた！でも「削除」ができない…AIに泣きついた結果

タスクを追加する機能はできたものの、いざ使ってみると「これ、終わったタスクどうするの？」ってなるんですよね。リストが増える一方で、全然減らない。

僕「タスクが追加できるのはいいんだけど、終わったタスクを消したいんだけど、どうすればいい？」

AI「なるほど、タスク削除機能ですね。各タスクの横に削除ボタンを追加して、それを押すとタスクが消えるようにしましょう。」

そしてまたコードをくれたんです。

:::details コードの例（削除機能追加後）
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Todo App</title>
</head>
<body>
    <h1>My Todo List</h1>
    <input type="text" id="taskInput" placeholder="新しいタスクを入力">
    <button onclick="addTask()">追加</button>
    <ul id="taskList">
        <!-- タスクがここに追加されます -->
    </ul>

    <script>
        function addTask() {
            const taskInput = document.getElementById('taskInput');
            const taskText = taskInput.value.trim();
            if (taskText === '') {
                alert('タスクを入力してください！');
                return;
            }

            const taskList = document.getElementById('taskList');
            const listItem = document.createElement('li');
            
            // タスクのテキスト部分
            const taskSpan = document.createElement('span');
            taskSpan.textContent = taskText;
            listItem.appendChild(taskSpan);

            // 削除ボタン
            const deleteButton = document.createElement('button');
            deleteButton.textContent = '削除';
            deleteButton.onclick = function() {
                taskList.removeChild(listItem); // 親要素から自分自身を削除
            };
            listItem.appendChild(deleteButton);
            
            taskList.appendChild(listItem);
            taskInput.value = ''; // 入力欄をクリア
        }
    </script>
</body>
</html>
```
:::

コードを見ても正直、何がどう変わったのかはパッと見じゃ全然わからないんだけど、「このコードを前のと入れ替えてください」って言われた通りにやってみたら…

おお、タスクの横に「削除」ボタンが出てる！押してみたら、ちゃんと消える！

この辺りから、AIとのやり取りが楽しくて仕方なくなってきました。なんか、自分のアイデアがどんどん形になっていくのが、すごく気持ちいいんです。これが「開発」ってやつなのかな。

話が逸れたけど、この削除機能は本当に便利で、これで日常的に使えるアプリの第一歩を踏み出せた気がします。