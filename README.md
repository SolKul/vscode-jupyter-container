# vscode-notebook-devcontainer
simple vscode project for development python and jupyter notebook in docker

# Usage

## Install Remote Container

Install Extensino for Visual Studio Code. 
[Remote - Containers - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)


## clone repository

clone this repository

## Open in Container

1. open Command Palette in Visual Studo Code.
2. Exec `Remote-Containers: Reopen Folder in Container`
3. wait until docker-compose build

# メモ


## Jupyter Labについて

徐々に推奨エディタが`Lab`に移り変わっているっぽい

`loacalhost:8888/tree`にアクセスすると、従来の`jupyter notebook`に、  
`loacalhost:8888/lab`にアクセスすると、`jupyter lab`にアクセスする

```docker-compose.yml
environment:
    - JUPYTER_ENABLE_LAB=yes
```

とすると、`localhost:8888`にアクセスした時点で`jupyter lab`にアクセスするするようになる。

## nbextensionsについて

`jupyter_contrib_nbextensions`は`jupyter notebook`でしか使えない。選択中の文字を強調する`Highlit Selected Word`を使いたいため、`jupyter notebook`+`jupyter_contrib_nbextensions`を使い続けている。いまのところ同じ機能は`jupyter lab`は対応していない。

ただ、

```docker-compose.yml
environment:
    - JUPYTER_ENABLE_LAB=yes
```

としてしまうと、`jupyter notebook`が`jupyter lab`管理下のものになってしまい、`jupyter_contrib_nbextensions`は使えなくなる。`jupyter_contrib_nbextensions`を使いたい場合は上はしないようにする。

## 権限について

普通に立ち上げるとユーザーは`jovyan`になってしまい、`apt-get`もできないが、

`Dockerfile`中で

```Dockerfile
USER root
```

として終われば`bash`は`root`で起動する。また上記のように`root`でDockerfileを終え、、`docker-compose.yml`で、

```docker-compose.yml
environment:
    - GRANT_SUDO=yes
```

としていれば、`jovyan`も`sudo`が使えるようになる。

つまり`GRANT_SUDO=yes` かつ`USER root`なら`jovyan`は`sudo`を使えるということ

https://jupyter-docker-stacks.readthedocs.io/en/latest/using/recipes.html

参照