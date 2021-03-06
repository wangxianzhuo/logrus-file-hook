# File Hook

File hook for logrus

## Usage

```golang
package main

import (
	log "github.com/sirupsen/logrus"
	"github.com/wangxianzhuo/filehook"
)

func main() {
	// use default path(./log)
	hook, err := filehook.New(&filehook.Option{
		Path:            "./logs/",
		SegmentInterval: 86400,
		NamePattern:     "%YY-%MM-%DD_%HH-%mm-%SS.log",
		LineBreak:       "\n",
	})
	if err != nil {
		panic(err)
	}
	log.AddHook(hook)

	log.Infof("info1")
	log.Infof("info2")
	// time.Sleep(15 * time.Second)
	log.Warnf("warn1")
	log.Warnf("warn2")
}
```

## Parameter

Option

- Path `the logs store path`
	- type `string`
	- default `default ./logs/`
- LineBreak `the line break`
	- type `string`
	- value `\n` or `\r\n`
	- default `default \n`
- SegmentInterval `segment file interval, unit second`
	- type `int64`
	- value `-1` is no segmention, `0` default segmention, `>0` segmention interval 
	- default `default 86400`
- namePattern is the log file name pattern. It can only use SetFileNamePattern() to modify.
	- type `string`
	- default `%YY-%MM-%DD_%HH-%mm-%SS.log`

## Installation

```shell
go get -u github.com/wangxianzhuo/filehook
```