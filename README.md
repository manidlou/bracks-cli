#bracks-cli

[![travis build][travis-image]][travis-url] [![npm version][npm-image]][npm-url] 

`bracks` command line interface. If you don't know what `bracks` style document is, please read [bracks](https://github.com/mawni/nodejs-bracks).

#####Install
Please use `npm install -g bracks-cli`. `-g` because it is a command line utility and is preferred to be exposed globally. Then, run `bracks -v` to make sure that it has been installed successfully. If you encounter with a problem or getting `EACCES` error, please read [fixing-npm-permissions](https://docs.npmjs.com/getting-started/fixing-npm-permissions). If still not successful, please mention that in the `issues`. It will be responded back as fast as possible.

#####How to use
You can use `bracks` either by manually run it whenever you want and pass the `-o` (flag for output), or you can have it watch the provided *bracks* directory by passing the `-w` (flag for watch).

If you run it with `-o`, here is how you can use it:

Please create a directory and name it `bracks`. Then, put all `html` or `ejs` files that are written in a `bracks` syntax in this direcory. Files can be located in sub-direcories. It doesn't matter. The parser will find them, convert them all to html or ejs, and pipe the result documents to the provided destination. The parser presumes everything under `bracks` directory is written in a `bracks` style. As a result, they all being converted to html and/or ejs and being piped to the provided target directory.

If you run it with `-w`, here is how you can use it:

Instead of writing all files completely and then pass them to `bracks`, you can have it watch the provided *bracks* directory. By running it this way, upon any changes in any files under the given *bracks* directory, the parser parses the files, converts them all to html or ejs (whatever the original file extension is), and pipes the result documents to the provided target directory. Please notice here, in this mode, if the parser doesn't find any errors, nothing will be shown on the console in order to avoid disrupting the flow of development. So, if you don't see any errors on the console after you saved your file, you can have a pretty good confidence that changes were being transferred correctly to the corresponding file under the provided target directory.

#####List of command line options
The complete list of `bracks` command line options:

1. `bracks -o <path to bracks directory> <target directory>`

    example: `bracks -o /home/yourproj/bracks /home/yourproj/views`

2. `bracks -w <path to bracks directory> <target directory>`

    example: `bracks -w /home/yourproj/bracks /home/yourproj/views`

3. `bracks -v` (show the current version of the app)

4. `bracks -h` (show the help menu)

#####Example of a `bracks` style html document
*index.html*:
```
<!DOCTYPE html>
html[
  c/[your comment]/c
  head[title[your page title]title]head
  body[
    h1[explore your mind]h1
    b[your bold text]b
    div(id="yourdiv" class="yourdivclass")[
      a(href="https://www.google.com")[link to google]a
      ul(style="list-style-type:disc")[
        li[item1]li
        li[item2]li
        li[a(href="https://www.google.com")[link to google]a]li
      ]ul
    ]div
    div[
      p[it is a samp s script footer paragraph tester]p
    ]div
  ]body
]html
```
#####Example of a `bracks` style ejs document
*index.ejs*:
```
<!DOCTYPE html>
html[
  head[
    title[your page title]title
    link(rel="stylesheet" href="/stylesheets/style.css")/]
    meta(charset="utf-8")/]
  ]head
  body(class="%= page %]")[
    [% include partials/template/header.ejs %]
      section(class="layout")[
        div(class="primary")[
          %- include partials/content/home-page.ejs -%
        ]div
        p[explore your mind]p
        aside(class="secondary")[
          %- include partials/content/proj-page.ejs %]
        ]aside
      ]section
    [% include partials/template/footer.ejs %]
  ]body
]html
```

[travis-image]: https://img.shields.io/travis/mawni/bracks-cli/master.svg
[travis-url]: https://travis-ci.org/mawni/bracks-cli
[npm-image]: https://img.shields.io/npm/v/bracks-cli.svg?maxAge=2592000
[npm-url]: https://npmjs.org/package/bracks-cli
[downloads-image]: https://img.shields.io/npm/dm/bracks-cli.svg?maxAge=2592000
[downloads-url]: https://npmjs.org/package/bracks-cli
