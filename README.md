# ETrobo-Docker
[![Docker Automated build](https://img.shields.io/docker/automated/korosuke613/etrobo-docker.svg?style=flat-square)](https://hub.docker.com/r/korosuke613/etrobo-docker/)

TOPPERS/EV3RTのビルド環境をラッピングしたUbuntuベースのDocker Image

* OS : Ubuntu 16.04.3
* Imageのサイズ : 約1.8GB
* `macOS 10.13.2`, `Windows10 Pro 16299.192のPowerShell` にて動作確認済

## 使用例
`app.cfg`の存在するディレクトリ(`/some/src/`とする)に移動してから、次のコマンドを実行する。

```
$ docker run -v /some/src/:/home/hrp2/sdk/workspace/src korosuke613/etrobo-docker
```

ビルドがうまく行った場合、`/some/src`に`app`というEV3RT向けの実行ファイルが生成されている。

ちなみに、相対パスを指定したい場合、`$PWD`を利用すると楽。(UNIX/LINUXでのみ可能)

```
$ cd /some/src/
$ docker run -v $PWD:/home/hrp2/sdk/workspace/src korosuke613/etrobo-docker 
```

### 手っ取り早く動作確認をしたい場合
以下のコマンドを実行する

#### Unix / Linux の場合

```bash
$ git clone --recursive --depth=1 https://github.com/korosuke613/ETrobo-Docker.git
$ cd ETrobo-Docker/sample/src
$ docker run -v $PWD:/home/hrp2/sdk/workspace/src korosuke613/etrobo-docker
```

#### PowerShellの場合
```PowerShell
$ git clone --recursive --depth=1 https://github.com/korosuke613/ETrobo-Docker.git
$ cd ETrobo-Docker/sample/src
$ docker run -v $PWD:/home/hrp2/sdk/workspace/src korosuke613/etrobo-docker
```