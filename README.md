# Motivation

At [Zalando](http://zalando.de), we maintain a [public Tech
Radar](http://zalando.github.io/tech-radar/) to help our engineering teams
align on technology choices. It is based on the [pioneering work
by ThoughtWorks](https://www.thoughtworks.com/radar).

This repository contains the code to generate the visualization:
[`radar.js`](/docs/radar.js) (based on [d3.js v7](https://d3js.org)).
Feel free to use and adapt it for your own purposes.

> [!NOTE]
> Since v0.12, we're using d3.js v7. See [related PR](https://github.com/zalando/tech-radar/pull/197/files)
> if you need to apply changes in your fork.

## Usage

1. include `d3.js` and `radar.js`:

```html
<script src="https://d3js.org/d3.v7.min.js"></script>
<script src="https://zalando.github.io/tech-radar/release/radar-0.12.js"></script>
```

2. insert an empty `svg` tag:

```html
<svg id="radar"></svg>
```

3. configure the radar visualization:

```js
radar_visualization({
  repo_url: "https://github.com/zalando/tech-radar",
  svg_id: "radar",
  width: 1450,
  height: 1000,
  scale: 1.0,
  colors: {
    background: "#fff",
    grid: "#bbb",
    inactive: "#ddd"
  },
  // Some font families might lead to font size issues
  // Arial, Helvetica, or Source Sans Pro seem to work well though
  font_family: "Segoe UI",
  title: "My Radar",
  quadrants: [
    { name: "Bottom Right" },
    { name: "Bottom Left" },
    { name: "Top Left" },
    { name: "Top Right" }
  ],
  rings: [
    { name: "INNER",  color: "#ff9c5c" },
    { name: "SECOND", color: "#d9486c" },
    { name: "THIRD",  color: "#a774d8" },
    { name: "OUTER",  color: "#346cef" }
  ],
  print_layout: true,
  links_in_new_tabs: true,
  entries: [
   {
      label: "Some Entry",
      quadrant: 0,
      ring: 1,         
      moved: -1             // -1 = moved out (triangle pointing down)
                            //  0 = not moved (circle)
                            //  1 = moved in  (triangle pointing up)
                            //  2 = new       (star)
   },
  ]
});
```

Entries are positioned automatically so that they don't overlap. The "scale" parameter can help
in adjusting the size of the radar.

As a working example, you can check out `docs/index.html` &mdash; the source of our [public Tech
Radar](http://zalando.github.io/tech-radar/).

## Deployment

Tech Radar is a static page, so it can be deployed using any hosting provider of your choice offering static page hosting.

## Local Development

1. install dependencies with yarn (or npm):

```
yarn 
```

2. start local dev server:

```
yarn start
```

3. your default browser should automatically open and show the url
 
```
http://localhost:3000/
```

## License

```
The MIT License (MIT)

Copyright (c) 2017-2025 Zalando SE

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
