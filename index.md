## Welcome to GitHub Pages
<html>
<script src='https://d3js.org/d3.v5.min.js'></script>
<style> circle {fill: lightblue; stroke: black;} </style>
<body onload='init()'>
<svg width=300 height=300>
</svg>
<script>
async function init() {
const data =await d3.csv("https://flunky.github.io/cars2017.csv");
var margin = 50;
var svg=d3.select("svg").append('g').attr("transform","translate(" + margin + "," + margin + ")");
var x = d3.scaleLog().domain([10,150]).range([0,200]);
var y = d3.scaleLog().domain([10,150]).range([200,0]);


svg.selectAll("circle").data(data).enter().append("circle")
      .attr("cx", function (d) { return (x(d.AverageCityMPG)); } )
      .attr("cy", function (d) { return (y(d.AverageHighwayMPG)); } )
      .attr("r", function (d) { return d3.sum([2,d.EngineCylinders]); });

d3.select("svg").append("g").attr("transform", "translate(50,50)")
.call(d3.axisLeft(y).tickValues([10, 20, 50, 100]).tickFormat(d3.format("~s")));
d3.select("svg").append("g").attr("transform", "translate(50,250)")
.call(d3.axisBottom(x).tickValues([10, 20, 50, 100]).tickFormat(d3.format("~s"))); 
}
</script>
</body>
</html>
You can use the [editor on GitHub](https://github.com/xzhang0123/testd3/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/xzhang0123/testd3/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
