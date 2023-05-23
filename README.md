### ■ サービス名<br>
YONDE | ラジオ番組への投稿をお助けします

<br>

### ■ サービス概要<br>
「オールナイトニッポン」のリスナーが、各番組に投稿メールを簡単に送ることができるWebサービス

<br>

    < オールナイトニッポンとは？ >

    「オールナイトニッポン（以下、ANN）」とは、1967年から放送されている、
    日本のラジオ番組で、全国ネットで毎週月曜日から土曜日の未明に
    放送されています。
    
    各曜日日替わりでミュージシャン、芸人、Youtubeといった
    様々な著名人がパーソナリティを務め、多くのファンに親しまれています。
    
    主な放送内容は、様々なジャンルの音楽やパーソナリティのエピソードトーク、
    そしてお題に沿っておもしろい回答をリスナーが投稿するネタ投稿コーナーです。
    
    各番組では、常にリスナーからの投稿（媒体：Eメール）を募集しており、
    採用されるとパーソナリティから番組内で読み上げられたり、
    番組オリジナルノベルティグッズがもらえたりします。
    
    なお、投稿は（1）ネタ投稿コーナーへの投稿と、（2）それ以外の一般的な
    メッセージである「ふつおた（ふつうのおたよりの略）」の投稿と
    2種類に大きくわかれます。

<br>

### ■ 前提・仮説<br>
- 若い世代のファンが多そうなパーソナリティが抜擢されることが多い（今年はJO1, Ado, あのちゃんなど）
- 最近の事象で、若い世代には、PCを使わずスマホだけで生活している方や、Eメールの送り方がわからないという方が一定数いると言われている
- パーソナリティが年単位で頻繁に変わるため、その度に普段ラジオを聞かないし投稿もしたこともない新しいリスナーが定期的に流入していると思われる

<br>

### ■ メインのターゲットユーザー<br>

- パーソナリティをきっかけにラジオ番組を聴き始めた新規のANNリスナーで、投稿をしたい人
- Eメールになじみがないであろう若い世代のANNリスナーで、投稿をしたい人
- 投稿をしたいと思っているが、方法がわからない人

<br>

### ■ サブのターゲットユーザー<br>
- ずっと投稿を続けているラジオリスナー
  - （余談：すでに投稿までの各個人のルーティーンが決まっているとは思うのですが、投稿の下書きをためておけるノートみたいなポジションのサービスになれたらいいかなと思っています。）

<br>

### ■ ユーザーが抱える課題<br>
- 投稿媒体がEメールに限られている
-  Googleフォームのようなフォームがないので、Eメールを作成して、番組に送信する必要がある
- Eメールに名前（or ラジオネーム）や件名を毎回コピペして送らないといけない
- 各番組のネタ投稿コーナーごとに、「メールにはこのように書いてください」といった指示がある

これらにより、投稿したくてもできない方が、潜在的にそこそこいるのではないかと考えました

<br>

### ■ 課題に対する仮説<br>
- Eメールになじみがない人には投稿のハードルが高い
  - そもそもEメールの作成・送信方法がわからない
- 番組からのEメールの書き方の指示がわかりにくい
- せっかく投稿しているのに、番組からの指示と異なっているため、採用されない場合がある

<br>

    < 現状の投稿手順＆番組側からの指示 >
    ANNの番組を聞いていて、自分もネタを投稿したいと思ったとき、下記のアクションが必要です。

    1. 番組公式サイトにアクセスして、下記のような番組からの指示を読み込む
      （この書き方は、指示がわかりにくいな…と感じます。）

        「あたしゃぁ～」
          ちびまる子ちゃんが好きなAdo。
          好きすぎてまるちゃんの「あたしゃぁ～」って言い方を無意識でマネしてしまうこともあります。
          このコーナーでは、「あたしゃぁ～」の後に何かを言ってください。

          例えば
            「あたしゃぁ～　博多で豚骨ラーメンを食べるときに
            「麺の固さ」を「やわ」でオーダーする奴は、
            逆に信用できるんじゃないかって思うんだよねぇ～。」

          件名は「　あたしゃ　」でお願いします。

    2. Eメール作成＆送信
      番組からの指示には明記がないのですが、下記のように作成しなければ
      採用されにくいという現実があります。
      
        件名：実際のコーナー名は「あたしゃぁ～」だが、件名は「あたしゃ」にしないといけないので注意
      
        本文：下記の順で記載
            ・1行目に都道府県名とラジオネーム
            ・改行
            ・ネタ
            さらに、ほどよく改行を入れて、読みやすくすることが大事。

<br>

### ■ 解決方法<br>
1. リリース時（MVP）
    - 目的：ユーザーの投稿のハードルを下げること

    - 機能 1：フォームにしたがって内容を記載するだけで、番組の指示にしたがったEメールが作れる機能を実装（Google APIのOAuth認証とmail_toメソッドを使用）
        - コーナー名は選択式にする（選択すると番組の指示にしたがった件名が入る）
        - ラジオネームや都道府県などの毎回記載する内容を登録できる機能
          - デフォルトを登録できる機能で、投稿内容作成時には自動入力されている
        - ほどよく改行がはいった本文が生成される

    - 機能 2：番組のコーナーが更新されるかもしれないので、スクレイピングで1週間に一回内容を取得する(Mechanize gemを使用)


    - 注意：スマホユーザーが使用しやすいWebアプリにするため、スマホ画面での見栄え・使用感にも細心の気を配ること
      - （余談：スマホ版の画面遷移図も作ろうと思っています。）

<br>

    〈理想の画面遷移〉
    　1. ユーザーがフォームに必要項目を入力する＆作成ボタンクリック
    　2. 確認画面表示＆投稿ボタンクリック
    　3. ユーザーのメールアドレスから必要項目が入力されたEメールが番組のメールアドレスに送信される

    ▼ 希望する人には2.3のステップをこのようにしたい
    ユーザーのメーラーで必要項目が入力されたEメールの下書きがポップアップされるので、それを確認して送信してもらう

<br>

2. アップデート時（暫定のアイデア・ユーザーの反応により柔軟に変更の予定）
    - 目的：ユーザーがより採用されやすくなる投稿メールを作れるようになること
    - 機能：投稿内容の壁打ちできる機能を実装
      - ChatGPTなどのLLMモデルサービスを用いて、投稿内容の相談相手になってもらう機能
        - 暴力的な差別的な表現があれば、言い換え案を提案してくれる
      - 下記のような採用されるコツが投稿作成時に表示される
        - 「書き言葉」ではなく「話し言葉」であること
        - トークが展開するような投稿であること
        - 1メールにつき話題は1つまで

<br>

### ■ 実装予定の機能<br>
- ゲストユーザー
    - 投稿メール作成機能
    - 投稿メール保存機能（ただしクッキーとセッションが残っている限り）
    - 投稿メール送信機能

<br>

- アカウント登録済みユーザー
  - アカウント作成機能
  - ログイン機能
  - 投稿作成機能
  - 投稿メール保存機能
    - 上記内で、お気に入り登録機能
    <!-- - 上記内で、採用された場合、マークをつけられる機能 -->
  - 投稿メール送信機能

<br>

- 管理ユーザー
    - アカウント登録済みユーザーの一覧、詳細、作成、編集、削除機能
    - アカウント登録済みユーザー投稿の一覧、詳細、作成、編集、削除機能
    - ANN番組の一覧、詳細、作成、編集、削除機能

<br>

### ■ なぜこのサービスを作りたいのか？<br>
投稿のハードルを下げて、投稿する人・採用される人を増やし、ANNの今後の発展に少しでも寄与できるようになりたいからです。

<br>

### ■ スケジュール<br>
README〜ER図作成：5/27<br>
メイン機能実装：5/28 - 6/30<br>
β版をRUNTEQ内リリース（MVP）：7/1<br>
本番リリース：7/15あたり<br>
アップデートのリリース：9/15あたり<br>

<br>

### ■ 技術選定
- Rails7（バックエンド）
- Rails7（フロントエンドとしてHotwire）
- mysql（バックエンド・データベース）
- JavaScript
- Bootstrap（フロントエンド）
- Fly.io（デプロイ先）
- Google APIのOAuth認証
