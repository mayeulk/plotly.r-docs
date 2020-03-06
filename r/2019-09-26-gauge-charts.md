---
name: Gauge Chart
permalink: r/gauge-charts/
description: How to create a Gauge Chart in R with Plotly
layout: base
thumbnail: thumbnail/gauge.jpg
language: r
redirect_from: r/gauge-meter
display_as: financial
order: 7
output:
  html_document:
    keep_md: true
---


### Basic Gauge

  A radial gauge chart has a circular arc, which displays a single value to estimate progress toward a goal.
  The bar shows the target value, and the shading represents the progress toward that goal. Gauge charts, known as
  speedometer charts as well. This chart type is usually used to illustrate key business indicators.

  The example below displays a basic gauge chart with default attributes. For more information about different added attributes check [indicator](https://plot.ly/r/indicator/) tutorial.


```r
library(plotly)

fig <- plot_ly(
    domain = list(x = c(0, 1), y = c(0, 1)),
    value = 270,
    title = list(text = "Speed"),
    type = "indicator",
    mode = "gauge+number") 
fig <- fig %>%
  layout(margin = list(l=20,r=30))

fig
```

<div id="htmlwidget-db680fe7d74b3c53addd" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-db680fe7d74b3c53addd">{"x":{"visdat":{"57ab338d48c":["function () ","plotlyVisDat"]},"cur_data":"57ab338d48c","attrs":{"57ab338d48c":{"domain":{"x":[0,1],"y":[0,1]},"value":270,"title":{"text":"Speed"},"mode":"gauge+number","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"margin":{"b":40,"l":20,"t":25,"r":30},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"domain":{"x":[0,1],"y":[0,1]},"value":270,"title":{"text":"Speed"},"mode":"gauge+number","type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Add Steps, Threshold, and Delta

The following examples include "steps" attribute shown as shading inside the radial arc, "delta" which is the
  difference of the value and goal (reference - value), and "threshold" to determine boundaries that visually alert you if the value cross a defined threshold.


```r
library(plotly)

fig <- plot_ly(
  domain = list(x = c(0, 1), y = c(0, 1)),
  value = 450,
  title = list(text = "Speed"),
  type = "indicator",
  mode = "gauge+number+delta",
  delta = list(reference = 380),
  gauge = list(
    axis =list(range = list(NULL, 500)),
    steps = list(
      list(range = c(0, 250), color = "lightgray"),
      list(range = c(250, 400), color = "gray")),
    threshold = list(
      line = list(color = "red", width = 4),
      thickness = 0.75,
      value = 490))) 
fig <- fig %>%
  layout(margin = list(l=20,r=30))

fig
```

<div id="htmlwidget-e29fb76981cd863cf9a4" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e29fb76981cd863cf9a4">{"x":{"visdat":{"57ab2dd750e4":["function () ","plotlyVisDat"]},"cur_data":"57ab2dd750e4","attrs":{"57ab2dd750e4":{"domain":{"x":[0,1],"y":[0,1]},"value":450,"title":{"text":"Speed"},"mode":"gauge+number+delta","delta":{"reference":380},"gauge":{"axis":{"range":[null,500]},"steps":[{"range":[0,250],"color":"lightgray"},{"range":[250,400],"color":"gray"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"margin":{"b":40,"l":20,"t":25,"r":30},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"domain":{"x":[0,1],"y":[0,1]},"value":450,"title":{"text":"Speed"},"mode":"gauge+number+delta","delta":{"reference":380},"gauge":{"axis":{"range":[[],500]},"steps":[{"range":[0,250],"color":"lightgray"},{"range":[250,400],"color":"gray"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Custom Gauge Chart
The following example shows how to style your gauge charts. For more information about all possible options check our [reference page](https://plot.ly/r/reference/#indicator).


```r
library(plotly)

fig <- plot_ly(
  type = "indicator",
  mode = "gauge+number+delta",
  value = 420,
  title = list(text = "Speed", font = list(size = 24)),
  delta = list(reference = 400, increasing = list(color = "RebeccaPurple")),
  gauge = list(
    axis = list(range = list(NULL, 500), tickwidth = 1, tickcolor = "darkblue"),
    bar = list(color = "darkblue"),
    bgcolor = "white",
    borderwidth = 2,
    bordercolor = "gray",
    steps = list(
      list(range = c(0, 250), color = "cyan"),
      list(range = c(250, 400), color = "royalblue")),
    threshold = list(
      line = list(color = "red", width = 4),
      thickness = 0.75,
      value = 490))) 
fig <- fig %>%
  layout(
    margin = list(l=20,r=30),
    paper_bgcolor = "lavender",
    font = list(color = "darkblue", family = "Arial"))

fig
```

<div id="htmlwidget-1829a10903cfef24531c" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1829a10903cfef24531c">{"x":{"visdat":{"57ab28303c3f":["function () ","plotlyVisDat"]},"cur_data":"57ab28303c3f","attrs":{"57ab28303c3f":{"mode":"gauge+number+delta","value":420,"title":{"text":"Speed","font":{"size":24}},"delta":{"reference":400,"increasing":{"color":"RebeccaPurple"}},"gauge":{"axis":{"range":[null,500],"tickwidth":1,"tickcolor":"darkblue"},"bar":{"color":"darkblue"},"bgcolor":"white","borderwidth":2,"bordercolor":"gray","steps":[{"range":[0,250],"color":"cyan"},{"range":[250,400],"color":"royalblue"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"indicator"}},"layout":{"margin":{"b":40,"l":20,"t":25,"r":30},"paper_bgcolor":"lavender","font":{"color":"darkblue","family":"Arial"},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"mode":"gauge+number+delta","value":420,"title":{"text":"Speed","font":{"size":24}},"delta":{"reference":400,"increasing":{"color":"RebeccaPurple"}},"gauge":{"axis":{"range":[[],500],"tickwidth":1,"tickcolor":"darkblue"},"bar":{"color":"darkblue"},"bgcolor":"white","borderwidth":2,"bordercolor":"gray","steps":[{"range":[0,250],"color":"cyan"},{"range":[250,400],"color":"royalblue"}],"threshold":{"line":{"color":"red","width":4},"thickness":0.75,"value":490}},"type":"indicator","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plot.ly/r/reference/#indicator](https://plot.ly/r/reference/#indicator) for more information and chart attribute options!
