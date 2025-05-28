# Xinference Server

Dify 用にモデルをホストするためのサーバーです。

## 環境

- uv

## モデル

### Embedding

#### uri-large

https://huggingface.co/cl-nagoya/ruri-large

### Rerank

#### ruri-reranker-large

https://huggingface.co/cl-nagoya/ruri-reranker-large

## セットアップ

### Python をインストール

```bash
uv python install
```

### 依存関係を同期

```bash
uv sync
```

### モデルをダウンロード

```bash
uv python download_models.py
```

### サーバーを起動

```bash
uv run xinference-local --host 0.0.0.0
```

### カスタムモデルを追加 (初回のみ)

#### uri-large

```bash
uv run xinference register --model-type embedding --file ruri-large.json --persist
```

#### ruri-reranker-large

```bash
uv run xinference register --model-type rerank --file ruri-reranker-large.json --persist
```

### モデルを起動

#### uri-large

```bash
uv run xinference launch -n ruri-large -t embedding
```

#### ruri-reranker-large

```bash
uv run xinference launch -n ruri-reranker-large -t rerank
```

### 起動中のモデルを確認

```bash
uv run xinference list

UID         Type       Name          Dimensions
----------  ---------  ----------  ------------
ruri-large  embedding  ruri-large          1024

UID                  Type    Name
-------------------  ------  -------------------
ruri-reranker-large  rerank  ruri-reranker-large
```

### ブラウザでアクセス

http://0.0.0.0:9997/
