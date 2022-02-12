# Go Hugo Goldmark KaTeX Support

Add [KaTeX](https://katex.org/) support to hugo to render math without
Javascript. This patch is based on the [graemephi/goldmark-qjs-katex
package](https://github.com/graemephi/goldmark-qjs-katex). Note that Chrome
still doesn't support MathML, use a proper browser! You can find a [demo
here](https://nox.im/posts/2021/1230/the-probability-of-six-sigma-events/).
Checkout and patch hugo:

```sh
git clone https://github.com/gohugoio/hugo.git
cd hugo
git fetch -a
# or latest tagged version, it may work too
git checkout v0.92.2
git apply 0001-PATCH-goldmark-add-katex-extension-support.patch
```

And install the hugo binary.

```sh
go mod tidy
go install
```

or move the binary manually if replacing a homebrew version

```sh
go build
which hugo
/usr/local/bin/hugo
mv hugo /usr/local/bin/hugo
```

Enable Katex in the hugo config:

```toml
[markup]
  defaultMarkdownHandler = "goldmark"
  [markup.goldmark.extensions]
    katex = true
```
