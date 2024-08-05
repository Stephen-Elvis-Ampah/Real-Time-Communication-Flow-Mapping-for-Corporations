# CommuniGraph: Real-Time Communication Flow Mapping for Corporations

## Introduction

In today's corporate environment, where efficient communication is paramount, visualizing the network of interactions within an organization like TechCorp can be incredibly beneficial. This project, a dynamic visualization tool, offers a deep dive into the communication patterns between different departments, aiming to optimize interactions and enhance organizational efficiency.

## Background

At TechCorp, like many other companies, communication silos often impede seamless collaboration across departments. This visualization tool was developed to break down these barriers by clearly illustrating how different parts of the organization interact, which can help identify areas for improvement.

## Tool Description

The "Visual Network Graph" utilizes the power of R and the Highcharter library to render an interactive and dynamic network graph of TechCorp's internal communications. This tool not only maps out department interactions but also updates dynamically with new data, providing ongoing insights into communication patterns.

## Features

- **Dynamic Visualization**: The graph updates in real-time as new data becomes available.
- **Interactive Elements**: Detailed statistics about communication volumes and patterns can be viewed by hovering over any node.
- **Customizable Appearance**: Users can customize the visual aspects such as colors and node sizes according to their preference or specific metrics.

## Implementation

This tool is designed to be plug-and-play for any organization interested in visualizing their internal communication networks. The GitHub repository includes detailed documentation on how to set up and adapt the visualization to specific organizational data.

## Impact

This visualization has already helped TechCorp identify key communication nodes and channels, leading to strategic interventions that have improved overall communication efficiency and effectiveness.

## Future Directions

Plans are underway to enhance the tool with predictive capabilities, using machine learning to forecast potential communication breakdowns and suggest optimal communication pathways.

## Conclusion

This project demonstrates the powerful role that data visualization can play in enhancing organizational communication. It provides not just a snapshot but a dynamic view of the communication landscape, supporting continuous improvement and strategic decision-making.

CommuniGraph: Real-Time Communication Flow Mapping for Corporations
================
Stephen Elvis Ampah
05.08.2024

## Introduction

In today’s corporate environment, where efficient communication is
paramount, visualizing the network of interactions within an
organization like TechCorp can be incredibly beneficial. This project, a
dynamic visualization tool, offers a deep dive into the communication
patterns between different departments, aiming to optimize interactions
and enhance organizational efficiency.

## Background

At TechCorp, like many other companies, communication silos often impede
seamless collaboration across departments. This visualization tool was
developed to break down these barriers by clearly illustrating how
different parts of the organization interact, which can help identify
areas for improvement.

## Tool Description

The “Visual Network Graph” utilizes the power of R and the Highcharter
library to render an interactive and dynamic network graph of TechCorp’s
internal communications. This tool not only maps out department
interactions but also updates dynamically with new data, providing
ongoing insights into communication patterns.

Stephen Elvis Ampah
05.08.2024

``` r
library(highcharter)
```

    ## Registered S3 method overwritten by 'quantmod':
    ##   method            from
    ##   as.zoo.data.frame zoo

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(data.table)
```

    ## 
    ## Attaching package: 'data.table'

    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     between, first, last

``` r
# library(WDI)
```

``` r
# Preparing the data
XY <- c(0, 2, -3, 4, -2, 6)
MN <- c(0, 3, 6, 8, 6, 7)

dt <- data.table(
  from = c("TechCorp", "TechCorp", "HR", "IT", "HR", "IT", "HR", "IT"),
  to = c("HR", "IT", "06 HR", "6 IT", "25 HR", "25 IT", "30 HR", "30 IT")
  )

# Create the highchart object
highchartzero() %>%
  hc_add_series(
    data = dt,
    type = "networkgraph",
    layoutAlgorithm = list(
      enableSimulation = TRUE,
      integration = "verlet"
    ),
    marker = list(
      symbol = "circle",
      radius = 35,
      lineColor = "none",
      # nodes = nodes,
      fillColor = list(
        linearGradient = list(x1 = 0, y1 = 1, x2 = 0, y2 = 0),
        stops = list(
          c(0, "#4C9A9E"),
          c(1, "#7BFAFF"))),
      states = list(
        hover = list(
          fillColor = "#E91E63",
          lineColor = "none",
          radius = 35
        )
      )
    ),
    
    link = list(
      color = list(
        linearGradient = list(x1 = 0, y1 = 1, x2 = 0, y2 = 0),
        stops = list(
          c(0, "#4C9A9E"),
          c(1, "#7BFAFF"))),
      width = '3'
    ),
    
    dataLabels = list(
      enabled = TRUE,
      style = list(
        color = "#f8f9fa",
        fontSize = "14px",
        fontWeight = "bold",
        textOutline = FALSE
      ),
      
      y = 20,
      linkFormat = ""
    ),
    
    nodes = list(
      list(id = "06 HR", xy = XY[1], mn = MN[1]),
      list(id = "6 IT", xy = XY[2], mn = MN[2]),
      list(id = "25 HR", xy = XY[3], mn = MN[3]),
      list(id = "25 IT", xy = XY[4], mn = MN[4]),
      list(id = "30 HR", xy = XY[5], mn = MN[5]),
      list(id = "30 IT", xy = XY[6], mn = MN[6]),
      list(id = "TechCorp"),
      list(id = "HR"),
      list(id = "IT")
    )
  ) %>%
  
  hc_title(
    text = "Network Graph",
    style = list(
      color = "white",
      fontSize = "20px",
      fontWeight = "bold"
    )
  ) %>%
  
  # Tooltip enables the hovering effect to take place
  hc_tooltip(
    enabled = T,
    useHTML = TRUE,
    formatter = JS(
      "function() {
          if (this.point.id === '06 HR' || this.point.id === '25 HR' || this.point.id === '30 HR' || this.point.id === '6 IT' || this.point.id === '25 IT' || this.point.id === '30 IT') {
            return this.point.name + '<br>XY: ' + this.point.xy + '<br>MN: ' + this.point.mn;
          } else {
            return this.point.name;
          }
        }"
    )
  )%>%
  
  hc_add_dependency(
    "modules/networkgraph.js"
  ) %>%
  
  hc_credits(
    enabled = FALSE
  ) 
```

    ## PhantomJS not found. You can install it with webshot::install_phantomjs(). If it is installed, please make sure the phantomjs executable can be found via the PATH variable.

![](CommuniGraph_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

