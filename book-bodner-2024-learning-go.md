[[$Bibliography]]

A go project is called a module. You create one by writing `go mod init <name>`.

Go takes formatting very seriously. You should always run `go fmt` and `go vet` before committing / building.

It's common practice in the go community to use Makefiles.

---

There are five types of literals in Go: an integer, a floating-point, a rune, a string and a complex number. They are defined as explicitly specified numbers, characters or strings.

---

A string in Go consists of a sequence of bytes, not runes. When getting a single value from a string using an index expression, you get a byte back. However when slicing a string, you ofc get a string.

Be aware when your string contains things other than an UTF-8 code points, e.g. emojis that make up multiple code points. These take up multiple bytes, so the length of a string containing emojis will be longer than the number of characters in the string.

If you want to check if something exists in a map, you use the "comma ok idiom". Basically

```go
m := map[string]int{
	"hello": 5,
	"world": 0,
}

v, ok := m["hello"]
fmt.Println(v, ok)
```

Will print out `5 true`.

Go does not have a Set, but you can use a map to simulate most of the features you would expect from a set.

When you have related data you want to group together you use a Struct.