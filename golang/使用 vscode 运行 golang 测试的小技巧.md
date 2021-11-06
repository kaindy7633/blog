# 使用 vscode 运行 golang 测试的小技巧

在使用 `Vscode` 编写 `Golang` 应用程序时，我们需要快速的得到测试结果，或者在学习编写样例代码时也会有这样的需求，此时我们可以打开 `vscode` 中的 `go` 配置，让测试自动运行，并打印出相应的结果。

按顺序打开：

文件 >> 首选项 >> 设置 >> 工作区设置 >> 在 setting.json 中编辑

填入以下内容：

```json
"go.coverOnSave": true,
"go.testFlags": ["-v"]
```

`coverOnSave` 意思很明白，保存代码时运行测试

`testFlags` 后面跟上了 `-v` 参数，表示需要在控制台中输出打印结果

如有以下测试代码：

```go
package try_test

import "testing"

func TestFirstTry(t *testing.T) {
	t.Log("My first try!!")
}
```

保存后自动运行得到如下结果：

```
Running tool: /usr/local/go/bin/go test -timeout 30s -coverprofile=/var/folders/rh/vdky3chn32s1dcfbz03rn5n80000gn/T/vscode-goavrJLe/go-code-cover go-entry-to-actual-combat/ch2/test -v

=== RUN   TestFirstTry
    /Users/kaindy/MyWorks/project/go-entry-to-actual-combat/ch2/test/first_test.go:6: My first try!!
--- PASS: TestFirstTry (0.00s)
PASS
coverage: [no statements]
ok  	go-entry-to-actual-combat/ch2/test	1.883s	coverage: [no statements]
```
