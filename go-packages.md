# golangパッケージメモ

主観によるパッケージメモ。  
網羅とかはしてない。公式とか事実上一択なやつとかは載せてない。

## まとめ

- https://awesome-go.com
- https://github.com/avelino/awesome-go
    - ここに載ってるからといって安心はできない。微妙なのもあるので吟味は必要。
- https://golanglibs.com/
    - GrowingとかPopularとか見れておもしろい
- https://github.com/kaxap/arl/blob/master/README-Go.md

## CLI

CLI用のライブラリやオプションパーサ

- https://github.com/urfave/cli
    - かつてcodegangsta/cliと呼ばれていたもの
    - 定番
    - bash completion対応
    - サブコマンド対応
    - ヘルプメッセージがテンプレートで柔軟に変更できる
- https://github.com/spf13/cobra
    - 最近の定番（urfave/cliよりも優勢になってきた？）
    - 大きなプロジェクト用な感じ
    - フラグの部分は https://github.com/spf13/pflag を利用している
    - bash completion対応
- https://github.com/jessevdk/go-flags
    - 指定方法などの柔軟性が高い
- https://github.com/jawher/mow.cli
    - spf13/cobraよりもう少しシンプルな感じ
    - 引数の順序とか繰り返しとかの制約ができるのが特徴
    - -h, --helpが固定で変更できない
    - ヘルプメッセージの内容をカスタマイズできない
- https://github.com/alecthomas/kingpin
    - 好みではない感じだった（忘れた）
    - bash completion対応
- https://github.com/cybozu-go/cmd
    - Contextベース、シグナルハンドリング、ロギング、gracefulなどなど

## TUI

- https://github.com/nsf/termbox-go
    - https://github.com/jroimartin/gocui
    - https://github.com/gizak/termui
- https://github.com/gdamore/tcell
    - なんかすごそう
    - https://github.com/marcusolsson/tui-go
    - https://github.com/rivo/tview
    - https://github.com/gcla/gowid
- https://github.com/VladimirMarkelov/clui
- https://github.com/cznic/wm

## TTY/PTY

- https://github.com/mattn/go-tty
- https://github.com/kr/pty

## JSON

`encoding/json`以外の選択肢。

- https://github.com/tidwall/gjson
- https://github.com/buger/jsonparser
- https://github.com/mailru/easyjson
- https://github.com/pquerna/ffjson
- https://github.com/json-iterator/go

## YAML

- https://github.com/go-yaml/yaml
    - Pure Go
    - 一番starが多くて一番よくできてる（libyamlからtranspile）
    - ~~LGPLv3 License~~
        - ~~過去に何度か変えてくれというissueが立っているが変える気はない模様~~
    - Apache License v2
        - See https://github.com/go-yaml/yaml/issues/160
- https://github.com/cloudfoundry-incubator/candiedyaml
    - **DEPRECATED**になった
    - Pure Go
    - MIT License
        - go-yamlの作者が「go-yamlのコードが含まれている」と指摘しているのが気になる
    - docker/libcomposeもgo-yamlからこっちに乗り換えてる
    - Cloud Foundryなので安心感がある
        - と思いきやCFの他のプロダクトはgo-yamlに戻し始めてるっぽい？

## TOML

- https://github.com/naoina/toml
    - v0.4.0 compliant
    - タグは"-"と"omitempty"のみ
    - CamelCase, snake_caseとかいい感じにマッピングしてくれる
    - Marshalが空白全部詰められてて機械的
- https://github.com/kezhuw/toml
    - v0.4.0 compliant
    - タグは"-", "omitempty", "inline", "multiline", "string", "datetime", "ascii", "literal"など色々ある(undocumented)
    - Marshalが適当に空白も入れてくれて綺麗
- https://github.com/pelletier/go-toml
    - v0.4.0 compliant
    - ~~Marshal/Unmarshalではなくqueryする感じで使う~~
        - いつのまにかMarshal/Unmarshalもサポートしてた
    - ツリーナビゲーションやクエリもできる
    - シンタックスエラーに行番号とカラム番号もレポートされる
    - 値をコメントアウトした状態にできるっぽい
- https://github.com/BurntSushi/toml
    - v0.4.0 compliant
    - タグは"omitempty", "omitzero"のみ
    - MarshalはあるけどUnmarshalがなくてEncoderを使う（あまり変わらないが）
    - starが一番多いけど、一番古い感じ

## Web関連

- https://github.com/PuerkitoBio/goquery
    - jQueryっぽくスクレイピングできる
    - “Go言語のスクレイピング系ライブラリまとめ” https://qiita.com/okatai/items/db6999ea1ab39ec0bd3e
- https://github.com/headzoo/surf
    - Mechanizeみたいなブラウザ操作のエミュレート
- http://go-colly.org/
    - スクレイピング、クローラーフレームワーク
    - よさげ
- https://github.com/go-playground/validator
    - バリデータ
- https://agouti.org/
    - WebDriver
- https://github.com/chromedp/chromedp
    - puppeteerのGo版みたいなやつ
- https://github.com/go-rod/rod
    - DevTools Protocolを使ったスクレイピングライブラリ

## WAF

- HTTP Router+α系
    - https://github.com/labstack/echo MIT
    - https://github.com/gin-gonic/gin MIT
    - https://github.com/go-martini/martini MIT
    - https://github.com/go-chi/chi MIT
    - https://github.com/zenazn/goji MIT
- フルスタック
    - https://github.com/gobuffalo/buffalo MIT
    - https://github.com/revel/revel MIT
    - https://github.com/astaxie/beego Apache 2.0 Sinatra, Flask like
        - 中国で主に使われてそうな雰囲気
    - https://github.com/kataras/iris BSD-3-Clause
        - スペックを見るととにかく最強感があるけど、Go界隈では次の理由から避けられている
        - 一時期物議を醸した
            - コミットを書き換えてContributorを自分だけにする、LICENSEを消す、issueを編集する…など、作者が信頼できない
            - https://www.quora.com/Why-do-so-many-Go-developers-hate-the-IRIS-web-framework
            - http://www.florinpatan.ro/2016/10/why-you-should-not-use-iris-for-your-go.html
- https://github.com/ant0ine/go-json-rest
    - JSON REST APIに特化
- 参考
    - https://github.com/mingrammer/go-web-framework-stars
    - [【2017年版】Go言語のフレームワーク比較と需要の高まり｜フリエン](https://furien.jp/columns/182/)

## HTTP

- https://github.com/elazarl/goproxy
    - http proxyライブラリ
- https://github.com/lucperkins/rek
    - HTTPクライアント

## WebSocket

- https://github.com/gorilla/websocket

## テンプレートエンジン

- https://github.com/eknkc/amber
    - Pug
- https://github.com/eknkc/pug
    - Pug
- https://github.com/yosssi/ace
    - SlimやJade風
- https://github.com/aymerick/raymond
    - Handlebars.jsのGo版
- https://github.com/flosch/pongo2
    - Django風
- https://github.com/valyala/quicktemplate
    - Mako風
- https://github.com/tyler-sommer/stick
    - Twig
- https://github.com/Masterminds/sprig
    - Twig
- https://github.com/biz/templates
    - 標準テンプレートのレイアウト化
- https://github.com/james-maloney/templates
    - 標準テンプレートのレイアウト化

## バリデータ

- https://github.com/astaxie/beego/tree/master/validation
- https://github.com/go-ozzo/ozzo-validation
- https://github.com/asaskevich/govalidator
- https://github.com/go-playground/validator
    - WAFで採用されてたりするけど、いまいちピンとこない

## GraphQL

[GoにおけるGraphQLライブラリ大横断 | HiCustomer Tech Blog](https://tech.hicustomer.jp/posts/go-graphql/)

- https://github.com/graphql-go/graphql
- https://github.com/graph-gophers/graphql-go
- https://github.com/99designs/gqlgen
    - スキーマからコード生成
- https://github.com/samsarahq/thunder
    - コードからスキーマ生成もできる

## 正規表現

- https://github.com/dlclark/regexp2
    - .NETの正規表現エンジンを移植したやつ
    - つよそう

## Parser

- https://github.com/alecthomas/participle

## Parser combinator

- https://github.com/prataprc/goparsec
- https://github.com/vektah/goparsify
- https://github.com/opsidian/parsley

## デーモン関連

- https://github.com/VividCortex/godaemon
    - 自身を起動することでデーモン化するライブラリ
    - シンプル
    - よくあるforkと同じで3-stageで処理される
    - ファイルの引き継ぎもできる
- https://github.com/sevlyar/go-daemon
    - 自身を起動することでデーモン化するライブラリ
    - 子を1回起動するだけっぽい
    - ログやPIDファイルを指定する機能がある
    - デーモンにシグナルを送信して制御する機能がある
        - flagを使っているのでそのへんがアプリとかち合わないか気になる
- https://github.com/takama/daemon
    - OSのサービスに登録することで制御できるようにするライブラリ
- https://github.com/kardianos/service
    - OSのサービスに登録することで制御できるようにするライブラリ
    - エントリポイントがライブラリで決められてる感じ
- https://github.com/fiorix/go-daemon
    - 指定したコマンドをデーモン化して実行するツール（ライブラリではない）
    - Cで書かれてるしGo以外の実行ファイルにも使えるしGo関係無かった

## プロセス

- https://github.com/codeskyblue/go-sh
    - Goからシェルとか外部コマンドの呼び出しを簡単にするライブラリ

## XDG Base Directory Specification

- https://github.com/goulash/xdg
    - パス取得とFindと分かれてるのが良い
- https://github.com/BurntSushi/xdg
- https://github.com/casimir/xdg-go
- https://github.com/adrg/xdg

## gettext

- https://github.com/leonelquinteros/gotext

## JavaScriptエンジン

- https://github.com/robertkrimen/otto
- https://github.com/olebedev/go-duktape

## DNSサーバ

- https://github.com/coredns/coredns
    - Kubernetesで使うために作られた
    - つよそう
- https://github.com/kenshinx/godns
- https://github.com/nanopack/shaman

## DB用ライブラリ

- https://github.com/jmoiron/sqlx
    - 標準のdatabase/sqlを便利にした感じのライブラリ
    - https://github.com/Code-Hex/sqlx-transactionmanager
        - トランザクション処理を楽にするライブラリ
        - sqlxのラッパーになっている
- https://github.com/go-gorp/gorp
    - ORMっぽいけどORMじゃない
- ORM
    - https://github.com/jinzhu/gorm
    - https://github.com/naoina/genmai
    - https://github.com/volatiletech/sqlboiler
- Query Builder
    - https://github.com/Masterminds/squirrel
    - https://github.com/dropbox/godropbox/tree/master/database/sqlbuilder
    - https://github.com/samonzeweb/godb
    - https://github.com/doug-martin/goqu
- Debug
    - https://github.com/gchaincl/sqlhooks
        - database/sqlの処理前後にフックを追加してロギングとかできるようにするライブラリ
- Driver
    - https://github.com/lib/pq
        - 今はメンテナンスのみ。jackc/pgxを推奨している。
    - https://github.com/jackc/pgx
    - https://github.com/mattn/go-sqlite3

## ロガー

- https://github.com/Sirupsen/logrus
    - そこそこの規模のアプリケーションだとよく使われてる印象
    - ログレベル別に出したり、JSONで出したりいろいろできる
    - 独自インターフェイス
- https://github.com/comail/colog
    - 標準のlogのフィルタとして動作
    - `log.Print("debug: debugging")`みたいにしてログレベルを制御する
    - JSON出力にも対応
- https://github.com/hashicorp/logutils
    - 標準のlogのフィルタとして動作
    - `log.Print("[DEBUG] Debugging")`みたいにしてログレベルを制御する
- https://github.com/cybozu-go/log

## テスト

- https://github.com/google/go-cmp
    - 値の比較をしていい感じにdiffが得られる

## 画像

- https://github.com/disintegration/imaging
    - 画像処理
- https://github.com/nfnt/resize
    - リサイズ
    - メンテされてないっぽい
- https://github.com/muesli/smartcrop
    - 画像の重要な部分を抜き出す

## PDF

- https://github.com/jung-kurt/gofpdf
    - 良く出来てるらしい
    - が、まだUTF-8がサポートされていないらしい
- https://github.com/signintech/gopdf
    - 日本語サポートしてる

## Excel

- https://github.com/360EntSecGroup-Skylar/excelize
    - よくできてそう（未評価）
- https://github.com/tealeg/xlsx
    - よくできてそう。有名。
    - 既存のフォーマットやオブジェクトが壊れるかも？
    - 重い。メモリ食う。
- https://github.com/plandem/xlsx
    - 既存のデータを壊さないように心がけている？
- https://github.com/loadoff/excl
    - 既存のデータを壊さないように心がけている

## Syntax highlight

- https://github.com/alecthomas/chroma

## 形態素解析

- https://github.com/shogo82148/go-mecab
    - libmecabのラッパー
- https://github.com/ikawaha/kagome
    - Pure Goな実装

## gRPC

- https://github.com/grpc/grpc-go
- https://github.com/lileio/lile
    - gRPCを使ったアプリケーションのジェネレータ

## Plugins

- https://github.com/hashicorp/go-plugin
    - gRPCを使ったプラグインシステム

## セキュリティ

- https://github.com/pquerna/otp
    - TOTPライブラリ

## Desktop Notification

- https://github.com/gen2brain/beeep
- https://github.com/deckarep/gosx-notifier macOS
- https://github.com/go-toast/toast Windows 10

## Windows

- [https://github.com/AllenDang/w32](https://github.com/AllenDang/w32)
    - Win32 API

## fsnotify, watch

- https://github.com/fsnotify/fsnotify
- https://github.com/rjeczalik/notify

## タスクランナー

- https://github.com/go-task/task
- https://github.com/tj/robo
- https://magefile.org/

## 実装支援ライブラリ

- https://github.com/wesovilabs/koazee
    - コレクションのストリーム
