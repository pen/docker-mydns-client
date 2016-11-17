# mydns-client

## Description

[MyDNS](www.mydns.jp)に登録したレコードの維持と更新のため、約15分おきにアドレスを通知する。
Dockerの練習で作った。

## インストール

```shell
mkdir $HOME/mydns
vi $HOME/mydns/mydns.conf
docker run -v $HOME/mydns:/ext:ro -d pengo/mydns-client
```

### 設定ファイル

```
# domain            id              pwd             addr4           addr6
example.com         mydns46A9       hoge123fuga
example.jp          mydns37S64      uhi@456!nyoro   192.168.255.254
v6.example.jp       mydns82B1       7-8#9foobar     -               0::1
```

1行1アカウントで複数のアカウントを指定できる。domainは備忘のためで使用されない。
IPアドレスを書けばダイレクト通知、書かなければログイン通知になる。

ファイルは毎回読まれるのでコンテナを動かしたまま編集可。
