# ETrobo-Docker

[![Docker Automated build](https://img.shields.io/docker/automated/korosuke613/etrobo-docker.svg?style=flat-square)](https://hub.docker.com/r/korosuke613/etrobo-docker/)

TOPPERS/EV3RTのビルド環境をラッピングしたUbuntuベースのDocker Image

* OS : Ubuntu 18.04.2 LTS
* Imageのサイズ : 約2GB
* `macOS 10.14.5`, `Windows10 Pro 16299.192のPowerShellおよびBoW` にて動作確認済
* TOPPERS/EV3RTのバージョン : [β7-3](http://dev.toppers.jp/trac_user/ev3pf/wiki/Download)

## 使用例

`app.cfg`の存在するディレクトリ(`/some/src/`とする)に移動してから、次のコマンドを実行する。

```bash
docker run --rm -v /some/src/:/home/hrp2/sdk/workspace/product korosuke613/etrobo-docker
```

ビルドがうまく行った場合、`/some/src`に`app`というEV3RT向けの実行ファイルが生成されている。

ちなみに、相対パスを指定したい場合、`$PWD`を利用すると楽。(UNIX/LINUXでのみ可能)

```bash
cd /some/src/
docker run --rm -v $PWD:/home/hrp2/sdk/workspace/product korosuke613/etrobo-docker
```

### 手っ取り早く動作確認をしたい場合

以下のコマンドを実行する

#### Unix / Linux の場合

```bash
git clone --recursive --depth=1 https://github.com/korosuke613/ETrobo-Docker.git
cd ETrobo-Docker/sample/src
docker run --rm -v $PWD:/home/hrp2/sdk/workspace/product korosuke613/etrobo-docker
```

#### PowerShellの場合

```PowerShell
git clone --recursive --depth=1 https://github.com/korosuke613/ETrobo-Docker.git
cd ETrobo-Docker/sample/src
> docker run --rm -v ${PWD}:/home/hrp2/sdk/workspace/product korosuke613/etrobo-docker
```

#### Bash on Windows(BoW)またはWindows Subsystem for Linux(WSL)の場合

WSL内のディレクトリは`-v`オプションで指定できないので、Windows上の絶対パスを指定する。([参考](https://qiita.com/gentaro/items/7dec88e663f59b472de6 "Docker for WindowsをWSLから使う時のVolumeの扱い方"))

次の例は、`C:\Users\hoge\ETrobo-Docker\sample\src`を共有する場合である。

```bash
git clone --recursive --depth=1 https://github.com/korosuke613/ETrobo-Docker.git
cd ETrobo-Docker/sample/src
docker run --rm -v C:\\Users\\hoge\\ETrobo-Docker\\sample\\src:/home/hrp2/sdk/workspace/product korosuke613/etrobo-docker
```

`\`はエスケープ文字であるため、`\\`というふうにエスケープする必要がある。
