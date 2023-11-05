# yaml-to-environ
[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)

## 概要
AWS cdkなどのために環境ごとに環境変数のyamlを作った場合に,これをdockerの環境で実行したい時に、指定した環境のために`.env`を切り出す。

例:
`.env.yaml`
```yaml:.env.yaml
KEY0: "common_api_key"
KEY1:
  local: "local_key1"
  prod: "prod_key1"
KEY2:
  local: "local_key2"
  default: "default_key2"
```
`.env`
```bash:.env
KEY0="common_api_key"
KEY1="local_key1"
KEY2="local_key2"
```


## usage 

```bash
yaml-to-environ {option}
```

## .env.yamlの設定

1. 環境ごとに環境変数を変える必要がなければ、そのまま環境変数をかく  
   exp.
   ```yaml
   KEY0: "common_api_key"
   ```
2. 環境ごとに環境変数を変える時は、サブキーとして環境名を指定する  
   exp.
   ```yaml
   KEY1:
     dev: "dev_key1"
     prod: "prod_key1"
   ```
3. 環境ごとに環境変数を変えたいが、そのほかは同じでいい場合はサブキーに`default`を指定する  
   exp.
   ```yaml
   KEY2:
     dev: "dev_key2"
     default: "default_key2"
   ```


## help
```shell
Usage: yaml-to-environ {options}

Options:
  -V, --version                output the version number
  -i --input-file <fileName>   input file .env.yaml (default: ".env.yaml")
  -o --output-file <fileName>  output file .env (default: ".env")
  -e --environ <environ>       select env default local (default: "local")
  -h, --help                   display help for command
```
