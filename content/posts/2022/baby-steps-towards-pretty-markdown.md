---
title: "Baby Steps Towards Pretty Markdown"
date: 2022-10-17T22:43:19+02:00
draft: true
categories: blog
tags:
  - markdown
  - css
---

`config.yml`:

```yml
markup:
  highlight:
    style: dracula
```

Fenced code block with language indicated:

````markdown
```python
package main

import "fmt"

func main() {
fmt.Println("Hello, World!")
}
```
````

Resulting render:

```python
package main

import "fmt"

func main() {
	fmt.Println("Hello, World!")
}
```

Also make article a tad more readable by centering and setting a maximum width.

```css
#content {
  margin-left: auto;
  margin-right: auto;
  max-width: 900px;
}
```
