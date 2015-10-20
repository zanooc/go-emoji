# go-emoji
Golang Emoji parser, comverter to html and images

# Usage

### Parse

```go
parser := NewEmojiParser()
var text = "a #💩 #and #🍦 #😳"
var i = -1
replased := parser.ReplaceAllStringFunc(text, func(s string) string {
	i++
	return strconv.Itoa(i)
})
// replased == "a #0 #and #1 #2"
```

### Convert

#### To HTML-Entities

```go
parser := NewEmojiParser()
var text = "a #💩 #and #🍦 #😳"
var i = -1
replased := parser.ToHtmlEntities(text)
// replased == "a #&#x1F4A9; #and #&#x1F366; #&#x1F633;"
```

#### To HTML-Images

```go
parser := NewEmojiParser()
var text = "a #💩 #and #🍦 #😳"
var i = -1
replased := parser.ToHtmlImages(text)
```
result:
```html
a #<img
class="emoji"
draggable="false"
alt="💩"
src="https://twemoji.maxcdn.com/36x36/1f4a9.png"> #and #<img
class="emoji"
draggable="false"
alt="🍦"
src="https://twemoji.maxcdn.com/36x36/1f366.png"> #<img
class="emoji"
draggable="false"
alt="😳"
src="https://twemoji.maxcdn.com/36x36/1f633.png">
```

# References

1. Instagram developers [blog](http://instagram-engineering.tumblr.com/post/118304328152/emojineering-part-2-implementing-hashtag-emoji)
2. Twemoji SVG [https://github.com/twitter/twemoji](https://github.com/twitter/twemoji)
