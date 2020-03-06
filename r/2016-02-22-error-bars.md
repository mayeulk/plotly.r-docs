---
name: Error Bars
permalink: r/error-bars/
description: How to add error bars to plots in R.
layout: base
thumbnail: thumbnail/error-bar.jpg
language: r
page_type: example_index
display_as: statistical
order: 4
output:
  html_document:
    keep_md: true
---


### Bar Chart with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

fig <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'bar', name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000'))
fig <- fig %>% add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

fig
```

<div id="htmlwidget-9a7b5958107bbff52000" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9a7b5958107bbff52000">{"x":{"visdat":{"43845a5156c5":["function () ","plotlyVisDat"],"43847fa46187":["function () ","data"]},"cur_data":"43847fa46187","attrs":{"43845a5156c5":{"x":{},"y":{},"error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"43847fa46187":{"x":{},"y":{},"error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"bar","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Scatterplot with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

fig <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'scatter', mode = 'markers',
        name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000'))
fig <- fig %>% add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

fig
```

<div id="htmlwidget-042a871cb1c1f20e6861" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-042a871cb1c1f20e6861">{"x":{"visdat":{"43844ed65a8c":["function () ","plotlyVisDat"],"43841421032f":["function () ","data"]},"cur_data":"43841421032f","attrs":{"43844ed65a8c":{"x":{},"y":{},"mode":"markers","error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"43841421032f":{"x":{},"y":{},"mode":"markers","error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"mode":"markers","error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"mode":"markers","error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"scatter","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Line Graph with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

fig <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'scatter', mode = 'lines+markers',
        name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000'))
fig <- fig %>% add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

fig
```

<div id="htmlwidget-ed30a3963134ddfc4e44" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-ed30a3963134ddfc4e44">{"x":{"visdat":{"438461954f5c":["function () ","plotlyVisDat"],"438421fdd860":["function () ","data"]},"cur_data":"438421fdd860","attrs":{"438461954f5c":{"x":{},"y":{},"mode":"lines+markers","error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"438421fdd860":{"x":{},"y":{},"mode":"lines+markers","error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"mode":"lines+markers","error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"mode":"lines+markers","error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"scatter","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Reference

See [https://plot.ly/r/reference](https://plot.ly/r/reference) for more information and chart attribute options!
