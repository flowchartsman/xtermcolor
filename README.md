# XtermColor

Find the closest xterm color to anything implementing [color.Color](https://golang.org/pkg/image/color/#Color).

Provides a [color.Palette](https://golang.org/pkg/image/color/#Palette) as `xtermcolor.Colors` so you can use `.Convert` and `.Index`,
but also provides convenience functions to get the index as a `uint8` from a `color.Color`, a 32 bit integer, or a 24 bit hex string.

Fork of [tomnomnom/xtermcolor](https://github.com/tomnomnom/xtermcolor) so that it can be a module.

Full documentation can be found on [GoDoc](https://pkg.go.dev/github.com/flowchartsman/xtermcolor).

Basic usage (examples/basic.go):

```go
package main

import (
	"fmt"
	"image/color"

	"github.com/flowchartsman/xtermcolor"
)

func main() {
	fmt.Println(xtermcolor.Colors.Convert(color.RGBA{128, 64, 32, 255}))

	fmt.Println(xtermcolor.FromColor(color.RGBA{120, 210, 120, 255}))

	fmt.Println(xtermcolor.FromInt(0xCC66FFFF))

	code, err := xtermcolor.FromHexStr("#FEFEFE")
	if err != nil {
		fmt.Println(err)
	}
	fmt.Println(code)
}
```

```
▶ go run examples/basic.go 
{135 95 0 255}
114
171
15
```

## xtermcolor command

There's also an `xtermcolor` command you can install by running:

```
▶ go get github.com/flowchartsman/xtermcolor/cmd/xtermcolor
```

Or you can download a binary from the [releases page](https://github.com/flowchartsman/xtermcolor/releases).

The command returns the color code for a 24 bit hex number:

```
▶ xtermcolor cc66ff
171
```

...or for seperate 8 bit red, green and blue components:

```
▶ xtermcolor 210 128 0
172
```
