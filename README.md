# PWSearch

PwnWiki 数据库搜索命令行工具。该工具有点像 `searchsploit` 命令，只是搜索的不是 Exploit Database 而是 PwnWiki 条目。

## 安装

您可以直接用 `pip` 命令从 PyPI 安装 PWSearch：

```shell
pip3 install -U pwsearch
```

您也可以 clone 该仓库并直接从源码启动：

```shell
git clone https://github.com/k4yt3x/pwsearch.git
pip3 install -U -r pwsearch/pwsearch/requirements.txt
```

## 命令行使用方法

![screenshot](https://user-images.githubusercontent.com/21986859/123427780-9543a500-d5b4-11eb-837f-7db87ea93f00.png)

```shell
# 搜寻关键词
pwsearch search CVE-2019-0708

# 在浏览器中打开详细页面
pwsearch open -p 2051

# 直接从源码启动的话需要把 pwsearch 当模组：
cd pwsearch
python -m pwsearch search CVE
```

您可以使用 `-t` 开关来将输出结果打印成更容易阅读的表格。注意 `-t` 是 `search` 命令的参数，所以要打在 `search` 之后。

![table](https://user-images.githubusercontent.com/21986859/123427979-d0de6f00-d5b4-11eb-831d-57e1006c7f20.png)

您也可以使用 `-q` 开关来隐藏日志信息。注意 `-q` 是全局参数，所以要打在 `search` 和 `open` 之前。

![quiet](https://user-images.githubusercontent.com/21986859/123428503-67ab2b80-d5b5-11eb-8f2b-f75b3f67dd56.png)

## Python 接口调用方法

```python
from pwsearch import Pwsearch

# 创建 Pwsearch 实例
pwsearch = Pwsearch()

# 搜索关键词，最多返回 20 个结果
# results 内容为包含搜索结果标题的 list
results = pwsearch.search(["关键词1", "关键词2"], max_results=20)

# 并发获取页面详细信息
# pages 内容为 list(dict())
# 可以自己试试看比较好理解
pages = pwsearch.pages(results)

# 也可不用异步仅获取一个页面
page = pwsearch.page(results[0])
```

## 软件许可

由于管理问题，目前本软件改为使用[专有协议](LICENSE)，请在使用前仔细阅读。使用该软件表明您已阅读并同意 EULA 中的内容。如有需要修改该源码，请联系作者取得授权。

© 2021 K4YT3X
All rights reserved.

## 友情链接

- PwnWiki: https://www.pwnwiki.org
- 论坛: https://forums.pwnwiki.org
- 中文 Telegram 群组: https://t.me/pwnwiki_zh
