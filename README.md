# mozjpeg

![ansible ci](https://github.com/link-u/ansible-roles-v2_mozjpeg/workflows/ansible%20ci/badge.svg)

## 概要

mozjpeg をインストールする ansible role

弊社で用意した deb パッケージからインストールする

## 動作確認バージョン

- Ubuntu 18.04 (bionic)
- ansible >= 2.8
- Jinja2 2.10.3

## 使い方 (ansible)

### Role variables

```yaml
### インストール設定 ###############################################################################
## 基本設定
mozjpeg_install_flag: True  # インストールフラグ

## make install していた名残の変数.
#  * deb に以降する際に make install したファイルを掃除するのに以下の変数は必要
#  * 特に group_vars で修正するような項目はない
mozjpeg_version: 3.3.1
mozjpeg_download_url: "https://github.com/mozilla/mozjpeg/archive/v{{ mozjpeg_version }}.tar.gz"
mozjpeg_prefix: "/usr/local"
```

### Example playbook

```yaml
- hosts:
    - servers
  become: True
  roles:
    - { role: mozjpeg, tags: ["mozjpeg"] }
```

## 後方互換性について

### 削除された変数の一覧

deb パッケージでのインストールに移行したため以下の変数は `group_vars` から削除して頂いて大丈夫です.

* `mozjpeg_force_install`
* `mozjpeg_command_name`
* `mozjpeg_download_dest`
* `mozjpeg_ldconfig_path`
* `mozjpeg_dependencies`
* `mozjpeg_install_dest`
