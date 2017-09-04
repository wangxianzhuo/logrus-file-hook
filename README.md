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

	logrus.AddHook(&filehook.NewFileHook("logs/", "windows", 1000))

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

## Installation

```shell
go get github.com/wangxianzhuo/filehook
```