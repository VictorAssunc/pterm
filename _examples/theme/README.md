# theme

![Animation](animation.svg)

```go
package main

import (
	"github.com/pterm/pterm"
	"reflect"
	"time"
)

func main() {
	pterm.Info.Println("These are the default theme styles.\n" +
		"You can modify them easily to your personal preference,\n" +
		"or create new themes from scratch :)")
	pterm.Println()

	v := reflect.ValueOf(pterm.ThemeDefault)
	typeOfS := v.Type()

	if typeOfS == reflect.TypeOf(pterm.Theme{}) {
		for i := 0; i < v.NumField(); i++ {
			field, ok := v.Field(i).Interface().(pterm.Style)
			if ok {
				field.Println(typeOfS.Field(i).Name)
			}
			time.Sleep(time.Millisecond * 250)
		}
	}
}

```
