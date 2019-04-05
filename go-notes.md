# golangメモ

## netパッケージを使うとdynamic linkになる

`net/http`などを使うとdynamic linkになってしまい、そのままバイナリをコピーしただけだと動かない場合がある。

### static linkにする方法

```sh
go build -a -tags netgo -installsuffix netgo
```

## cgoを使っているとdynamic linkになる

### static linkにする方法

```sh
go build --ldflags '--extldflags "static"'
```

netパッケージと合わせるとこんな感じ。

```sh
go build -a -tags netgo -installsuffix netgo --ldflags '-extldflags "-static"'
```

※CentOSの場合、`glibc-static`がインストールされていないと失敗する。

## パッケージ別サイズ

https://github.com/jondot/goweight
