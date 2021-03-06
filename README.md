Swift-HTML-Parser
=================
A swift wrapper around libxml for parsing HTML

Usage
=================
```swift
import Foundation

let html = "<html><head></head><body><ul><li><input type='image' name='input1' value='string1value' class='abc' /></li><li><input type='image' name='input2' value='string2value' class='def' /></li></ul><span class='spantext'><b>Hello World 1</b></span><span class='spantext'><b>Hello World 2</b></span><a href='example.com'>example(English)</a><a href='example.co.jp'>example(JP)</a></body>"

var err : NSError?
var parser     = HTMLParser(html: html, error: &err)
if err != nil {
    println(err)
    exit(1)
}

var bodyNode   = parser.body

if let inputNodes = bodyNode?.findChildTags("b") {
    for node in inputNodes {
        println(node.contents)
    }
}

if let inputNodes = bodyNode?.findChildTags("a") {
    for node in inputNodes {
        println(node.contents)
        println(node.getAttributeNamed("href"))
    }
}

```
