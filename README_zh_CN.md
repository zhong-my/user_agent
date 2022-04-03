# User-Agent
<p align="center">
  <a href="https://github.com/mssola/user_agent/actions/workflows/ci.yml" title="Travis CI status for the default branch"><img src="https://github.com/mssola/user_agent/actions/workflows/ci.yml/badge.svg" alt="Build Status for the default branch" /></a>
  <a href="http://godoc.org/github.com/mssola/user_agent" title="godoc.org page"><img src="https://godoc.org/github.com/mssola/user_agent?status.png" alt="godoc.org page" /></a>
  <a href="https://en.wikipedia.org/wiki/MIT_License" rel="nofollow"><img alt="MIT" src="https://img.shields.io/badge/license-MIT-blue.svg" style="max-width:100%;"></a>
</p>

---

UserAgent 是一个用于解析 HTTP 用户代理的 Go 包，举个例子：

```go
package main

import (
    "fmt"

    "github.com/mssola/user_agent"
)

func main() {
    // "New" 方法会创建一个 UserAgent 对象，将用来解析传入的字符串参数。
    // 如果你想解析更多字符串，你可以重复这个对象或调用：ua.Parse("another string")
    ua := user_agent.New("Mozilla/5.0 (Linux; U; Android 2.3.7; en-us; Nexus One Build/FRF91) AppleWebKit/533.1 (KHTML, like Gecko) Version/4.0 Mobile Safari/533.1")

    fmt.Printf("%v\n", ua.Mobile())   // => true
    fmt.Printf("%v\n", ua.Bot())      // => false
    fmt.Printf("%v\n", ua.Mozilla())  // => "5.0"
    fmt.Printf("%v\n", ua.Model())    // => "Nexus One"

    fmt.Printf("%v\n", ua.Platform()) // => "Linux"
    fmt.Printf("%v\n", ua.OS())       // => "Android 2.3.7"

    name, version := ua.Engine()
    fmt.Printf("%v\n", name)          // => "AppleWebKit"
    fmt.Printf("%v\n", version)       // => "533.1"

    name, version = ua.Browser()
    fmt.Printf("%v\n", name)          // => "Android"
    fmt.Printf("%v\n", version)       // => "4.0"

    // 让我们看看机器人的例子。

    ua.Parse("Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)")

    fmt.Printf("%v\n", ua.Bot())      // => true

    name, version = ua.Browser()
    fmt.Printf("%v\n", name)          // => Googlebot
    fmt.Printf("%v\n", version)       // => 2.1
}
```

如果你想阅读整个 API 文档，可以从这里查看 [godoc](http://godoc.org/github.com/mssola/user_agent).

## 安装

```
go get -u github.com/mssola/user_agent
```

## 贡献

你想贡献代码或报告一个错误？可以阅读这里 [CONTRIBUTING.md](./CONTRIBUTING.md) file.

## [更新日志](https://pbs.twimg.com/media/DJDYCcLXcAA_eIo?format=jpg&name=small)

阅读这个文件 [CHANGELOG.md](./CHANGELOG.md)。

## 开源协议

```
Copyright (c) 2012-2021 Miquel Sabaté Solà

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```
