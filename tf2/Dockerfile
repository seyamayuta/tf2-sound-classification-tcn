# https://hub.docker.com/r/tensorflow/tensorflow/
# Jupyterは最新版を個別で導入するため-jupyterタグ付きのイメージは利用しない。
FROM tensorflow/tensorflow:2.4.1-gpu

# ラベル指定
LABEL maintainer "Yoshitada Kurozumi"

# 対話形式での確認無効化（Dockerイメージビルド時に入力待ちで先に進めなくなるため）
# ENVで設定するとイメージ自体に設定が引き継がれるため、ARGで一時的な設定とする。
ARG DEBIAN_FRONTEND=noninteractive

# 参照先のリポジトリを日本のミラーサイトに変更
# Ubuntu Mirror site: <https://launchpad.net/ubuntu/+archivemirrors>
# src: archive.ubuntu.com
# dst: linux.yz.yamagata-u.ac.jp
RUN sed -i.backup -e 's|archive.ubuntu.com|linux.yz.yamagata-u.ac.jp|g' /etc/apt/sources.list

# 必要なパッケージの追加とタイムゾーンの設定
RUN apt-get update && apt-get install -y \
    tzdata \
    libsndfile1 \
&&  ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
&&  apt-get clean \
&&  rm -rf /var/lib/apt/lists/*

ENV TZ=Asia/Tokyo

# JupyterLab関連
# JupyterLabのコード補完エラー対応のためjediはバージョンを指定（2021/04/11時点）
RUN python3 -m pip install --upgrade pip \
&&  pip install \
    black \
    jupyterlab \
    jupyterlab_code_formatter \
    jupyterlab_widgets \
    import-ipynb \
    ipywidgets \
&&  pip install -U "jedi<0.18"

## 追加パッケージ
RUN pip install \
    tensorflow-io \
    tensorflow-graphics-gpu \
    keras-tcn \
    matplotlib \
    seaborn \
    pretty_midi \
    librosa \
    Pillow \
    opencv-python

# ENTRYPOINT [ "/bin/bash" ]
# WORKDIR /workspace
