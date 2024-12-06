# 授权头检查和添加工具

## 安装

```shell
go install github.com/HJH0924/addlicense@latest
```

## 使用
```shell
addlicense -h # 查看帮助信息
```
添加许可证
```shell
addlicense -v -c "Tvux" . --skip-dirs=third_party,.idea
```
