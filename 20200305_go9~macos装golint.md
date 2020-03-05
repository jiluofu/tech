**2020.03.05**

## 安装golint，给sublime的gosublime使用
```

cd $GOPATH
mkdir -p src/golang.org/x
cd src/goling.org/x
git clone https://github.com/golang/tools.git tools

cd $GOPATH
go install golang.org/x/lint/golint/
$GOPATH/bin/golint


gosublime配置

"comp_lint_enabled": true,

"comp_lint_commands": [
		{"cmd": ["golint *.go"], "shell": true},
	],

"on_save": [ {"cmd": "gs_comp_lint"}],


```