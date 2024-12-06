# 授权头检查和添加工具


## 安装

```bash
go install github.com/HJH0924/addlicense@latest
```

帮助信息为：

```bash
$ addlicense -h
Usage: addlicense [flags] pattern [pattern ...]

The program ensures source code files have copyright license headers
by scanning directory patterns recursively.

It modifies all source files in place and avoids adding a license header
to any file that already has one.

The pattern argument can be provided multiple times, and may also refer
to single files.

Flags:

      --check                check only mode: verify presence of license headers and exit with non-zero code if missing
  -h, --help                 show this help message
  -c, --holder string        copyright holder (default "Google LLC")
  -l, --license string       license type: apache, bsd, mit, mpl (default "apache")
  -f, --licensef string      custom license file (no default)
      --skip-dirs strings    regexps of directories to skip
      --skip-files strings   regexps of files to skip
  -v, --verbose              verbose mode: print the name of the files that are modified
  -y, --year string          copyright year(s) (default "2021")
```

参数说明：

- `--check` 只检查
- `-f, --licensef` 指定版权头文件
- `-v` 打印被更改的文件
- `--skip-dirs` 跳过指定的文件夹

## 使用方法

1. 创建版权头文件

```bash
$ cat ./boilerplate.txt
Copyright 2024 Tvux

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

2. 检查文件中是否都有该版权头

```bash
$ addlicense --check -f ./boilerplate.txt . --skip-dirs=third_party
```

3. 给缺失版权头的文件添加版权头

```bash
$ addlicense -v -f ./boilerplate.txt . --skip-dirs=third_party
```
