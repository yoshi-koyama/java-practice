# 何をするのか？

Javaの基礎を勉強するための問題集です。

# 前提
- Javaのバージョンは17を使いましょう
- エディタはIntelliJを使いましょう

# 準備

GitHubの自分のアカウントでリポジトリを作ってください。  

リポジトリの名前は「java-practice」にしてください。  

IntelliJからProjectを作成しましょう。  

<img width="500" alt="スクリーンショット 2022-07-16 19 05 49" src="https://user-images.githubusercontent.com/62045457/179350352-6f6874cc-cb80-4f87-a527-44667322c4ed.png">

ディレクトリ構成は下記のようにしましょう。  

```bash
.
├── .gitignore
├── README.md
└── src
    └── Main.java
```
.gitignoreには下記を記載してください。  

```
HELP.md
.gradle
build/
!gradle/wrapper/gradle-wrapper.jar
!**/src/main/**/build/
!**/src/test/**/build/

### STS ###
.apt_generated
.classpath
.factorypath
.project
.settings
.springBeans
.sts4-cache
bin/
!**/src/main/**/bin/
!**/src/test/**/bin/

### IntelliJ IDEA ###
.idea
*.iws
*.iml
*.ipr
out/
!**/src/main/**/out/
!**/src/test/**/out/

### NetBeans ###
/nbproject/private/
/nbbuild/
/dist/
/nbdist/
/.nb-gradle/

### VS Code ###
.vscode/
```

README.mdには下記を記載してください。  

```
# このプロジェクトについて

Javaの基礎的な文法を勉強するためのリポジトリです。
```

`src/Main.java`には下記を記載してください。

```java
public class Main {

  public static void main(String[] args) {
    System.out.println("Hello World");
  }

}
```

ソースコードを自動でフォーマットするために以下を設定しましょう。  
Save ActionsというPluginをいれるとよいです。  

<img width="300" alt="スクリーンショット 2022-07-16 19 08 29" src="https://user-images.githubusercontent.com/62045457/179350417-d076580b-9841-42f9-bac8-3a7ace7a08e9.png">

<img width="300" alt="スクリーンショット 2022-07-16 19 08 46" src="https://user-images.githubusercontent.com/62045457/179350423-f3ca3c33-c3fa-4d3c-9b2c-18fcd86247ae.png">

ここまでできたら自分のリポジトリにプロジェクトをpushしましょう。  

pushまでできたらリポジトリのリンクを共有してください。  

----

# 課題１

`feature/add-user`ブランチを作成してください。  

次のようなUser.javaファイルを作ってください。  
フィールドに名前（name）と生年月日（birthdate）を持ちます。  

```java
public class User {

  private final String name;

  private final LocalDate birthdate;
  
}
```

そして、以下のことをIntelliJのコード生成機能を使って作成してください。  
参考: https://pleiades.io/help/idea/generating-code.html#generate-constructors  
- 引数にすべてのフィールドをとるコンストラクタ
- ゲッター
- セッターは不要です
- equals/hashCodeメソッド

# 課題２

Main.javaに以下のusers変数を記述してください。  

```java
public class Main {

  public static void main(String[] args) {
    List<User> users = List.of(
        new User("佐藤美咲", LocalDate.of(1990, 1, 1)),
        new User("鈴木太郎", LocalDate.of(1991, 2, 2)),
        new User("山田一郎", LocalDate.of(2003, 3, 3)),
        new User("鈴木花子", LocalDate.of(2002, 4, 4)));
  }
}
```

# 課題３

すべてのユーザーを標準出力するコードを追加してください。  

出力は次のような形式になるようにしましょう。  

```
【すべてのユーザーを表示する】
名前: 佐藤美咲, 生年月日: 1990-01-01
名前: 鈴木太郎, 生年月日: 1991-02-02
名前: 山田一郎, 生年月日: 2003-03-03
名前: 鈴木花子, 生年月日: 2002-04-04
```

実装のサンプルはこちらです。  
コピペでもいいですし、自分でもっといい方法を考えてもいいです。  

```java
public class Main {

  public static void main(String[] args) {
    List<User> users = List.of(
        new User("佐藤美咲", LocalDate.of(1990, 1, 1)),
        new User("鈴木太郎", LocalDate.of(1991, 2, 2)),
        new User("山田一郎", LocalDate.of(2003, 3, 3)),
        new User("鈴木花子", LocalDate.of(2002, 4, 4)));
     
    System.out.println("【すべてのユーザーを表示する】");
    users.forEach(u -> System.out.printf("名前: %s, 生年月日: %s\n", u.getName(), u.getBirthdate()));
  }
}
```

ここまでの変更をコミットしてください。  

コミットメッセージは次のように日本語で書きましょう。

```bash
$ git commit -m "Userクラスを作成し、usersを表示する処理を記載"
```

または

```bash
$ git commit -m "feat: Userクラスを作成し、usersを表示する処理を記載"
```

または

```bash
$ git commit -m "add: Userクラスを作成し、usersを表示する処理を記載"
```

コミットしたらpushしてください。  
そして、Pull Requestを作成してください。  
Pull Requestはレビューしやすいようにタイトルや説明をよく考えてつくりましょう。  

レビューが完了したらPull Requestをマージしてください。  
リモートの`feature/add-user`ブランチは削除してください。  

Pull Requestをマージしたら自動でリモートのブランチを削除する機能がありますので設定をONにするといいです。  
参考： https://docs.github.com/ja/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-the-automatic-deletion-of-branches  

# 課題3+α

コミットメッセージの書き方について以下の記事を読んでください。  

- https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/
- https://www.praha-inc.com/lab/posts/commit-message

そして次の質問に対する答えを考えて文章にまとめましょう。  

コミットメッセージはどのように書くべきですか？  
その理由は何でしょうか？　　

文章ができたら、それを週報に記載してレビューを依頼してください。  

# 課題4

自分のリポジトリに`feature/display-users`という名前のブランチを作成してください。

すべてのユーザーを標準出力するコードを追加してください。  
生年月日は`yyyy年MM月dd日(E)`形式で出力するようにしてください。  

このとき、これまでの課題で書いたコードは消さなくて大丈夫です。  
このあとの課題も同様です。  

出力は次のようになります。  

```
【すべてのユーザーを表示する】
名前: 佐藤美咲, 生年月日: 1990-01-01
名前: 鈴木太郎, 生年月日: 1991-02-02
名前: 山田一郎, 生年月日: 2003-03-03
名前: 鈴木花子, 生年月日: 2002-04-04
【すべてのユーザーを表示する。ただし生年月日はyyyy/MM/dd(E)形式で出力する】
名前: 佐藤美咲, 生年月日: 1990年1月1日(月)
名前: 鈴木太郎, 生年月日: 1991年2月2日(土)
名前: 山田一郎, 生年月日: 2003年3月3日(月)
名前: 鈴木花子, 生年月日: 2002年4月4日(木)
```

# 課題5

名前が鈴木で始まる人のみを表示してください。  

出力は次のようになります。  
```
【すべてのユーザーを表示する】
名前: 佐藤美咲, 生年月日: 1990-01-01
名前: 鈴木太郎, 生年月日: 1991-02-02
名前: 山田一郎, 生年月日: 2003-03-03
名前: 鈴木花子, 生年月日: 2002-04-04
【すべてのユーザーを表示する。ただし生年月日はyyyy年MM月dd日(E)形式で出力する】
名前: 佐藤美咲, 生年月日: 1990年1月1日(月)
名前: 鈴木太郎, 生年月日: 1991年2月2日(土)
名前: 山田一郎, 生年月日: 2003年3月3日(月)
名前: 鈴木花子, 生年月日: 2002年4月4日(木)
【名前が鈴木で始まる人のみを表示する】
鈴木太郎
鈴木花子
```

ここまでできたら変更をコミットしてpushしましょう。  
そして、Pull Requestを作成してください。  
レビューが完了したらPull Requestをマージして`feature/display-users`ブランチは削除してください。  

# 課題6

`feature/display-users-birthdate`という名前のブランチを作成してください。  

生年月日が2000年1月1日以降の人のみを表示してください。  

出力は次のような形式になるようにしましょう。  
  
```
（省略）
名前: 山田一郎, 生年月日: 2003年3月3日(月)
名前: 鈴木花子, 生年月日: 2002年4月4日(木)
【名前が鈴木で始まる人のみを表示する】
鈴木太郎
鈴木花子
【生年月日が2000年1月1日以降の人のみを表示する】
名前: 山田一郎, 生年月日: 2003-03-03
名前: 鈴木花子, 生年月日: 2002-04-04
```

# 課題7

生年月日の昇順に並び替えて表示してください。

```
【生年月日の昇順に並び替えて表示する】
名前: 佐藤美咲, 生年月日: 1990-01-01
名前: 鈴木太郎, 生年月日: 1991-02-02
名前: 鈴木花子, 生年月日: 2002-04-04
名前: 山田一郎, 生年月日: 2003-03-03
```

# 課題8

生年月日の降順に並び替えて表示してください。

```
【生年月日の降順に並び替えて表示する】
名前: 山田一郎, 生年月日: 2003-03-03
名前: 鈴木花子, 生年月日: 2002-04-04
名前: 鈴木太郎, 生年月日: 1991-02-02
名前: 佐藤美咲, 生年月日: 1990-01-01
```

ここまでできたら変更をコミット、pushし、Pull Requestを作成してください。  
レビューが完了したらPull Requestをマージして`feature/display-users-birthdate`ブランチは削除してください。  

# 課題9

`feature/display-users-age`という名前のブランチを作成してください。

2022年7月1日時点の各ユーザーの年齢を表示してください。

```
【2022年7月1日時点の各ユーザーの年齢を表示する】
名前: 佐藤美咲, 年齢: 32歳
名前: 鈴木太郎, 年齢: 31歳
名前: 山田一郎, 年齢: 19歳
名前: 鈴木花子, 年齢: 20歳
```

# 課題10

2022年7月1日時点で20歳以下のユーザーを表示してください。

```
【2022年7月1日時点で20歳以下のユーザーを表示する】
名前: 山田一郎, 年齢: 19歳
名前: 鈴木花子, 年齢: 20歳
```

# 課題11

2022年7月1日時点で20歳未満のユーザーを表示してください。  

```
【2022年7月1日時点で20歳未満のユーザーを表示する】
名前: 山田一郎, 年齢: 19歳
```

ここまでできたら変更をコミット、pushし、Pull Requestを作成してください。  
レビューが完了したらPull Requestをマージして`feature/display-users-age`ブランチは削除してください。  

# 課題10と11+α

以下、未満という言葉が出てきました。  

これらの言葉はよく似ていますが意味は全然違います。  

以下と未満の違いについて調べてください。  

調べた内容は週報に書いたうえで、レビューを依頼してください。
