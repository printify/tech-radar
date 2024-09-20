# Printify Technology Radar

The Tech Radar is a tool to inspire and support Engineering teams at Printify to pick the best
technologies for new projects; it provides a platform to share knowledge and experience in
technologies, to reflect on technology decisions and continuously evolve our technology landscape.
Based on the [pioneering work of ThoughtWorks](https://www.thoughtworks.com/radar), our
Tech Radar sets out the changes in technologies that are interesting in software development —
changes that we think our engineering teams should pay attention to and use in their projects.

## Maintenance

### Local development

Radar is setup in the most naive way possible - as static index.html based on [Zalando technical radar implementation](https://github.com/zalando/tech-radar/tree/master).

In order to start "local development" serve it with any webserver. F.e. with python:

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Navigate to `http://localhost:8000/` and proceed to the editing.

### Radar content

Radar content is defined in the [data.json](./data.json) file. 
From it you can control:
* Radar Title - `title`
* Radar publish date - `date`
* Radar rings (exactly 4 rings are supported):
    * `rings.[].name` - Ring title. Also serves as ID for item ring placement 
    * `rings.[].color` - Ring color
    * `rings.[].description` - Ring description. Supports HTML styling
* Radar quadrants names list (exactly 4 rings are supported). Also serves as ID for item quadrants placement 
* Blips or entries:
    * `blips.[].name` - Blip title
    * `blips.[].quadrant` - Quadrant name/ID
    * `blips.[].ring` - Ring name/ID
    * `blips.[].moved` - Previous Blip state enum. Supported values are: `IN`, `OUT`, `STILL`
    * `blips.[].link` - Link for blip details

### Radar appearance

Radar is fully defined in 2 files:
* [index.html](./index.html)
* [radar.css](./radar.css)

The only necessary parts are next scripts being included:
```html
    <script src="https://d3js.org/d3.v4.min.js"></script>
    <script src="http://zalando.github.io/tech-radar/release/radar-0.8.js"></script>
```
Other than that any html/css/scripting styling can be applied.

### Radar deployment

No additional setup is required. By default, the repository is configured to serve static files from the main branch. Once your PR is merged, you can access our public [Tech Radar](https://printify.github.io/tech-radar/). Please note that GitHub Pages may take some time to update, so changes might not be immediately visible after the merge.
