**2024.03.26**

## pip3安装包报错error: externally-managed-environment


### 方案一、(粗暴) 去掉这个提示
```
python3
import sys
sys.path
cd /opt/homebrew/Cellar/python@3.12/3.12.2_1/Frameworks/Python.framework/Versions/3.12/lib/python3.12
rm EXTERNALLY-MANAGED

```

### 方案二、(推荐) 使用pipx
```
brew install pipx
```

### 方案三、(高阶) 使用venv

sudo apt install python3-venv
sudo apt install python3.10-venv

生成一个Python虚拟环境

mkdir -p $HOME/.env && python3 -m venv $HOME/.env/project_name
现在，您将看到一个.env在您的主目录中，并且在 .env 中，您将拥有项目目录。

每个虚拟环境项目目录中都会有自己的 Python 和 Pip 副本。
