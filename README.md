# mozjpeg

## 概要

mozjpeg をインストールする ansible role
現在はビルドしてインストール.

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
mozjpeg_force_install: no
mozjpeg_version: 3.3.1
mozjpeg_command_name: "mozjpegtran"
mozjpeg_download_url: "https://github.com/mozilla/mozjpeg/archive/v{{ mozjpeg_version }}.tar.gz"
mozjpeg_prefix: "/usr/local"
mozjpeg_download_dest: "{{ mozjpeg_prefix }}/src"
mozjpeg_ldconfig_path: "{{ mozjpeg_prefix }}/lib"
mozjpeg_install_dest: "{{ mozjpeg_prefix }}/bin"
mozjpeg_dependencies:
  - "libpng-dev"
  - "libtiff-dev"

# ※ 特に group_vars で修正するような項目はない
```

### Example playbook

```yaml
- hosts:
    - servers
  become: True
  roles:
    - { role: mozjpeg, tags: ["mozjpeg"] }
```
