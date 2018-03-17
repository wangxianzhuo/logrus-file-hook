# File Hook

File hook for logrus

## Usage

```golang
package main

import (
	logrus "github.com/sirupsen/logrus"
	"github.com/wangxianzhuo/filehook"
	"os"
)

func main() {

	logrus.SetFormatter(&logrus.JSONFormatter{})

	logrus.SetOutput(os.Stderr)

	logrus.SetLevel(logrus.DebugLevel)

	hook, err := filehook.New("", "windows", 0)
	if err != nil {
		panic(err)
	}
	hook.SetFileNamePattern("log%YY%MM%DD")
	logrus.AddHook(hook)

	logrus.Warn("warn")
	logrus.Info("info")
	logrus.Debug("debug")
}
```

## Parameter

Optional

- Path `default ./logs/`
- LineBreak `default \n`
- RecreateFileInterval `default 1 day, unit second`
- namePattern can only use SetFileNamePattern() to modify `default %YY-%MM-%DD_%HH-%mm-%SS.log`

## Installation

```shell
go get github.com/wangxianzhuo/filehook
```