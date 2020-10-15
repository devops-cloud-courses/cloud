# DevOps course

This repo contains a reveal.js presentation about Cloud.
To visualize this presentation, go here: https://cours-ece.github.io/cloud
You can also clone this repo and expose static pages through your favorite web server.

> This course is open source. You can use it freely.

## Table of content

* Introduction
* Chapter one

## See this course locally with docker
```bash
docker build -t course .
docker run -d --rm -p 80:8080 --name=course course
```
* After a few seconds, you can see the slides on http://localhost
* When you want to stop the instance, run:
```bash
docker stop course
```

## Print this course to pdf (only in chrome and chromium)
* Click on [this link](https://cours-ece.github.io/cloud/?print-pdf&pdfSeparateFragments=false)
* Then `CTRL+P` on the generated page
* Change the following settings

Setting | Value
--- | ---
Destination | Save as PDF
Pages | All
Pages per sheet | 1
Margins | Default
Options | Background graphics

* Click on save

## Edit this course
> For any question about Reveal.js usage, read [Reveal Documentation](reveal-documentation.md)

Feel free to submit as many pull request as you wish !

