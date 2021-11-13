---
title: "Rust環境のSetup for macOS"
emoji: "📑"
type: "tech"
topics: ["rust", "setup"]
published: false
---

# Mac で Rust

Rustの勉強を始めたので、今後も参照するであろうコマンド類をまとめておきます.

調べると他にもいっぱい書いてる方がいるので、かなり備忘的な感じです.

## Rust Install

オフィシャルのページに手順があるので、コマンドをまんまコピーで実行.

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### ちなみにWindowsは

https://forge.rust-lang.org/infra/other-installation-methods.html

rustup-init.exe があるのでこちらを使うか、Chocolatey あたりでインストールです.

## すでにインストール済みの環境をアップデートする

インストール済みの人は、最新版にアップデート.

```bash
rustup update
```

バージョン確認は

```bash
rustup --version
```

```bash
cargo --version
```

あたりで確認.

## パッケージのアップデート

```cargo``` でインストール済みのパッケージを全部アップデートするには、とりあえず```cargo-update```をインストールして、以降はこいつを利用するのが早い模様.

```bash
cargo install cargo-update
```

これで```cargo-update```が入るので、以降は以下のコマンド.

```bash
cargo install-update --all
```
