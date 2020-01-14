# R-Shiny
---
title: "Introduction to R shiny package"
author: "Hakan Turgay & Bertan Taylan"
output:
  revealjs::revealjs_presentation: 
      incremental: true
      reveal_options:
        slideNumber: true
        previewLinks: true

---



```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
```
# <span style="font-weight:bold">  Chapter 1 </span> <br> </br> Motivation, Basic R-Shiny Package and Example {data-background=#00ccff .center}


## Motivation
- Scientists mostly use R to process their analyzes

- Presenting/Sharing their findings are usually done in static format

- <span style="color:purple; font-weight:bold"> Problem : </span>They cannot present additional questions directly


- <span style="color:purple; font-weight:bold"> Simple idea: </span>Immigrating ratios from a specific region of Turkey due to years and also forecasts about these ratios (e.g. Journalist)

## What is Shiny package? 

- Shiny is an R package that makes it easy to build <span style="color:red; font-weight:bold">interactive web applications</span> (apps) straight from R. This lesson will get you started building Shiny apps right away.
- Build useful web applications <span style="color:purple; font-weight:bold">with only a few lines of code</span>—no JavaScript required.
- Shiny applications are <span style="color:green; font-weight:bold">automatically “live”</span> in the same way that spreadsheets are live. Outputs change instantly as users modify inputs, without requiring a reload of the browser.
- Shiny user interfaces can be built entirely using R, or can be written directly in HTML, CSS, and JavaScript for more <span style="color:blue; font-weight:bold">flexibility.</span>
- Pre-built output widgets for displaying <span style="color:aqua; font-weight:bold">plots, tables, and printed output of R objects.</span>

## Basically
<div margintop= 10px align ="center"> 
  <br>R Shiny = R + interactivity + web made easy</br>
</div>

<div align ="center"; padding-bottom: 25px>
  <img src="../images/whats.png" alt="kmeans" class="center">
</div>


## Install Shiny Package 
If you still haven’t installed the Shiny package, open an R session, connect to the internet, and run

```r
install.packages("shiny")
```

## First App in  Shiny 

```r
library(shiny)
runExample("01_hello")
```

<div id="CodeOutput" name="CodeOutput" style="text-align: center; vertical-align: middle;">
Code Output
</div>
<div align ="center"; padding-bottom: 10px>
  <img src="../images/first app in shiny.PNG" alt="firstapp" class="center" width="700" height="400">
    </div>
## More Example

```r 
runExample("01_hello")      # a histogram
runExample("02_text")       # tables and data frames
runExample("03_reactivity") # a reactive expression
runExample("04_mpg")        # global variables
runExample("05_sliders")    # slider bars
runExample("06_tabsets")    # tabbed panels
runExample("07_widgets")    # help text and submit buttons
runExample("08_html")       # Shiny app built from HTML
runExample("09_upload")     # file upload wizard
runExample("10_download")   # file download wizard
runExample("11_timer")      # an automated timer
```
# <span style="font-weight:bold">  Chapter 2</span> <br> </br> Structure of a Shiny App {data-background=#00cc66 .center}
## Main Structure
<head>
<style>
div .row{
    font-size:75%;
}
</style>
</head>

<body>

<div class="row">
  <div class="col-md-6" markdown="1">

* <span style="color:red; font-weight:bold">ui: </span> Nested R functions that assemble an HTML user interface for the app

* <span style="color:red; font-weight:bold">server : </span> A function with instructions on how to build and rebuild the R objects
displayed in the UI

* <span style="color:red; font-weight:bold">shinyApp : </span> Combines ui and server into a functioning app

* Save the template as <span style="color:purple; font-weight:bold">app.R</span>

* a call to the shinyApp function
  
</div>

  <div class="col-md-4" markdown="1">
   
```r
    library(shiny)
    
    ui <- fluidPage(
     
    )
    
    server <- function(input, output, session) {
      
    }
    
    shinyApp(ui, server)
```
</div>
</div>
</body>
## Alternative Approach
<div align="center">
  <img src="../images/alternative.PNG" alt="kmeans" class="center">
</div>

## Say Hello with Shiny

```r
library(shiny)
ui <- fluidPage(
    "Hello Shiny Package"
    )

server <- function(input, output) {
    
}

shinyApp(ui = ui, server = server)
```
<div id="CodeOutput" name="CodeOutput" style="text-align: center; vertical-align: middle;">
Code Output
</div>
  working code:

<div align ="center"; padding-bottom: 25px>
  <img src="../images/hello shiny.PNG" alt="helloshiny" 
  class="center" width="200" height="40"> 
    </div>
# <span style="font-weight:bold">  Chapter 3</span> <br> </br> Inputs and Outputs {data-background=#00ccff .center}
## Overview

Build your app around <span style="color:purple; font-weight:bold">inputs</span> and <span style="color:green; font-weight:bold">outputs</span>

<div align ="center" >
<img src="../images/kmeans.PNG" alt="kmeans" class="center" style="width:512px;height:512px">
</div>

## Input Syntax
<div align="center"  style = "margin-top: 150px">

<img src="../images/input-syntax.PNG" alt="kmeans" class="center">
</div>

## Input 
```r
sliderInput(inputId = "num",
  label = "Choose a number",
  value = 25, min = 1, max = 100)
```
```r
library(shiny)
ui <- fluidPage(
    sliderInput(inputId = "num",
                label = "Choose a number",
                value = 25, min = 1, max = 100)
    )

server <- function(input, output) {
    
}

shinyApp(ui = ui, server = server)
```

## Code Output

<div align ="center"; padding-bottom: 25px>
  <img src="../images/input.PNG" alt="input" 
  class="center" width="500" height="200"> 
    </div>

## Entegration Input and Output

Use <span style="color:red; font-weight:bold">3 rules</span> to write the server function



```r
server <- function(input, output) {




}

```

## 1 - Save objects to display to output$

<head>
  <style>
  .grid-container {
    display: grid;
    grid-template-columns: auto auto;
    grid-gap: 10px;
    background-color: #ffffff;
      padding: 10px;
  }

.grid-container > div {
  background-color: #ffffff;
  text-align: center;
  padding: 20px 0;
  font-size: 30px;
}
</style>
  </head>
  <body>
  
  <div class="grid-container">
  <div>
```r

server <- function(input, output) {  
  output$hist <- # code
}


```
</div>
  
  <div>
  <div align="center">
  <img src="../images/firstRule.PNG" alt="First Rule" class="center">
  </div></div>
  
  <div>
  <div style="text-align: center;">
  <img src="../images/output-syntax.PNG" alt="kmeans" class="center">
  
  </div></div>
  
  </div>
  
  </body>

## 2 - Build objects to display with render*()

[ING] UI tarafinda bulunan 'hist' (histogram) objesi server tarafindaki 'RenderPlot' methodu ile uretilecek . 
Not: hist ve RenderPlot vurgulanacak ..


```r

server <- function(input, output) {  
  output$hist <- renderPlot({

   #code

  }) 
}

```
## Render Method

<div align="center"  >
  <img src="../images/render.PNG" alt="First Rule"   
  class="center">
</div>

<div style="margin-left: 40px;">

```r

server <- function(input, output) {
  output$hist <- renderPlot({

    title <- "100 random normal values"           

    hist(rnorm(100), main = title) 

  }) 
}

```
</div>

## 3 - Access input values with input$
<div style="margin-left: 40px;">

```r
server <- function(input, output) {  
  
  output$hist <- renderPlot({    
  hist(rnorm(input$num))  
  
  }) 

}

```
<div align="center"  >
  <img src="../images/parameter.PNG" alt="First Rule"   
  class="center">
</div>

</div>

## ...and more "Render Method"  example

<div align="center"  >
  <img src="../images/render_methods.PNG" alt="First Rule"   
  class="center">
</div>

## ...and more Input functions  example

<div align="center"  >
  <img src="../images/input-more.PNG" alt="First Rule"   
  class="center">
</div>



## Result  (Reactivity) {.smaller}

  Reactivity automatically occurs whenever you use an input value to render an output object
  
<div style="margin-left: 40px;">
```r
library(shiny)
ui <- fluidPage(
    sliderInput(inputId = "num",
                label = "Choose a number",
                value = 25, min = 1, max = 100),
    plotOutput("hist")
    )

server <- function(input, output) {
    output$hist <- renderPlot({
        hist(rnorm(input$num))
    })
}

shinyApp(ui = ui, server = server)
```
</div>

## Code Output
working code:

<div align ="center"; padding-bottom: 25px>
  <img src="../images/reactivity result.PNG" alt="res" 
  class="center" width="1000" height="550"> 
    </div>
    
# <span style="font-weight:bold">  Chapter 4</span> <br> </br> Using Checkbox in Shiny {data-background=#00cc66 .center}
## Reviewing an Example 
```R
library(shiny)
runExample("02_text")
```


<div align ="center"; padding-bottom: 25px>
  <img src="../images/checkbox.png" alt="kmeans" class="center">
</div>


##  Starting to Code Analysis 
<div align ="center"; padding-bottom: 0px>
  <img height="600px" src="../images/analysis.png" alt="kmeans" class="center">
</div>
## Change code
<div style="font-size:28px">
```r
library(shiny)

ui <- fluidPage(
  titlePanel("Shiny Text"),
  sidebarLayout(
    
    sidebarPanel(
      
      checkboxGroupInput("dataset", "Choose a dataset:",
                         c("rock", "pressure", "cars"),
                         selected = "rock"),
                         
      numericInput(inputId = "obs",
                   label = "Number of observations to view:",
                   value = 10)
    ),
    
    mainPanel(
      verbatimTextOutput("summary"),
      tableOutput("view")
```
</div>
## Result
working code:

<div align ="center"; padding-bottom: 25px>
  <img src="../images/workingcode checkbox.PNG" alt="check" 
  class="center" width="1000" height="550"> 
    </div>

# <span style="font-weight:bold">  Chapter 5</span> <br> </br> Improving the Design  {data-background=#00ccff .center}
## Design Part {.build}

<div class="row">
  <div class="col-md-6" markdown="1">
  
  * Assemble UI with HTML/CSS/... widgets
  
  * Adjustment of the layout scheme
  
  </div>
  <div class="col-md-2" markdown="1">
  <img height="450px" class="center-block" src="../images/layout.png">
  </div>
</div>

## A Sidebar Component: Sidebar Layout
<div style="font-size:27px">
* The sidebar layout is a basic model for starting to develop applications.
* This layout gives a sidebar for inputs and a big area for printing outputs. </div>
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/sidebar layout.PNG" alt="sidebar" 
  class="center" > 
    </div>
    
## Grid Layout
* This feature is a component of <span style="color:purple; font-weight:bold">content</span> part.
* Rows are created by the fluidRow() function and columns defined by the column() function.
* First parameter of column function is its width (which can take values between 1 and 12).
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/grid layout.PNG" alt="grid" 
  class="center" > 
    </div>
    
## Tabsets
<div style="font-size:27px">
* Tabsets are good alternatives in need of subdividing the user interface into discrete sections and are components of <span style="color:purple; font-weight:bold">content</span> part.
* tabsetPanel function can be used for creating Tabsets.
</div>
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/tabset layout.PNG" alt="tabset" 
  class="center" > 
    </div>
    
## Navlists
* navlistPanel function  provides the ability of listing components on sidebar.
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/navlist layout.PNG" alt="navlist" 
  class="center" > 
    </div>
    
## Navbar Pages
* With navbarPage function, we can create different tabs which contains different sub-elements.
* Navbar pages are components of <span style="color:purple; font-weight:bold">navigation</span> part.
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/navbar layout.PNG" alt="navbar" 
  class="center"> 
    </div>

# <span style="font-weight:bold">  Chapter 6</span> <br> </br> Implementations in Shiny: JavaScript, HTML and CSS {data-background=#00cc66 .center}

## Using HTML in R Shiny 

<head>
  <style>
  .item3 { grid-area: main; }
.item4 { grid-area: right; }


.grid-container {
  display: grid;
  grid-template-areas:
    
    
    'main right';
  grid-gap: 10px;
  background-color: #ffffff;
    padding: 10px;
}

.grid-container > div {
  background-color: #ffffff;
    text-align: center;
  padding: 20px 0;
  font-size: 30px;
}
</style>
  </head>
  <body>
  
  <center>  <br>In R, <span style="color:purple; font-weight:bold">HTML elements</span> can be defined by <span style="color:green; font-weight:bold">tags</span> keyword.
</center>
  
  <div class="grid-container">
  
  <div class="item3">
  ```r
ui <− fluidPage (
  tags$h1(”R Shiny Introduction”) ,
  tags$hr () ,
  tags$br () ,
  tags$p(strong(”Istanbul Technical University”)),
  tags$p(em(”Mathematical Engineering”)),
  tags$a(href=”https://www.itu.edu.tr”,”Website”))
server <− function(input , output){} > 
  shinyApp(ui = ui , server = server)
```
  
  </div>  
  
  <div class="item4">
  
  <img src="../images/html tags.PNG" alt="tags" 
class="center" width="500" height="300"> 
  
  </div>
  </div>
  
  </body>
    
## ...and more Html Tag
 
<div align="center"  style = "margin-top: 20px">
  <img src="../images/html_tags.PNG" alt="html tag" class="center">
</div>

## External file import (html, css , js ext)

<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
 {
  box-sizing: border-box;
}


.column {
  float: left;
  width: 33.33%;
  padding: 10px;
  
}


.row:after {
  content: "";
  display: table;
  clear: both;
}
</style>
</head>
<body>

Method of importing depends on type of the file;

<div class="row">

  <div class="column" style="background-color:#ffffff;">
    
  <h4>To include a <span style="color:orange; font-weight:bold">CSS</span> file</h4>
<br> <small> use <span style="font-weight:bold">includeCSS()</span> or 
<br> <span style="font-weight:bold">1.</span> Place the file in the <span style="font-weight:bold">www</span> subdirectory 
<br><span style="font-weight:bold">2.</span> Link to it with: 
</small>
```r 
tags$head(tags$link(rel = "stylesheet",
type = "text/css", href = "<file name>"))
```
    
  </div>
  
  <div class="column" style="background-color:#ffffff;">
    
  <h4>To include <span style="color:green; font-weight:bold">JavaScript</span></h4>
<br> <small> use <span style="font-weight:bold">includeScript()</span> or 
<br> <span style="font-weight:bold">1.</span> Place the file in the <span style="font-weight:bold">www</span> subdirectory 
<br><span style="font-weight:bold">2.</span> Link to it with: 
</small>
```r 
tags$head(tags$script(src = "<file name>"))
```     
  </div>
  
  <div class="column" style="background-color:#ffffff;">
  
<h4>To include <span style="color:blue; font-weight:bold">HTML file</span></h4>
    
```r
includeHTML("include.html")
```

  </div>
  
</div>

</body>


## An Example on Include Javascript 

```javascript
//myscripts.js file
document.body.style.backgroundColor = "skyblue";
```
<img src="../images/js-example.png" alt="javascript" class="left" width="650" height="490">

## Result 

<img src="../images/js-effect.png" alt="kmeans" class="left" width="650" height="500">

# <span style="font-weight:bold">  Chapter 7</span> <br> </br> Introduction to HTMLWidgets Package {data-background=#00ccff .center}

## Overview
* This package builds a framework for creating R bindings to JavaScript libraries. HTMLWidgets can be 
    * Used at the R console for <span style="color:green; font-weight:bold"> data analysis </span>
    * Embedded within <span style="color:blue; font-weight:bold"> R Markdown </span> documents 
    * Incorporated into <span style="color:purple; font-weight:bold"> Shiny </span> web applications
    
## Creating a Widget

* Three elements forms the widget:
    
    * <span style="color:red; font-weight:bold"> Dependencies </span>: JavaScript and CSS assets will be used by the widget 
    * <span style="color:gray; font-weight:bold">R binding </span>: This is the function where R stuff happens
    * <span style="color:green; font-weight:bold">JavaScript binding </span>: JavaScript code that connects everything and passes the data and the choices collected from the R binding to the JavaScript library which is (are) using in widget

## Some most-used HTMLWidget Examples

<head>
<style>
  .grid-container {
    display: grid;
    grid-template-columns: 500px auto;
    grid-gap: 10px;
    background-color: #ffffff;
      padding: 5px;
  }

.grid-container > div {
  background-color: #ffffff;
  text-align: center;
  padding: 20px 0;
  font-size: 30px;
}
</style>
</head>
<body>
  
  
<div class="grid-container">
<div>
<div align ="left">
<img src="../images/leaflet_example.png" alt="kmeans" class="left" width="650" height="250">
</div> <br>leaflet</div>
<div>
<div align ="right">
<img src="../images/dygraph_example.png" alt="kmeans" class="right" width="500" height="250">
</div> <br>dygraph</div>
</div>
  
</body>

## A Small Case Study: Predicted Deaths From Lung Disease By Using Dygraph Package

Ui part of the code:

<div style="font-size:25px">

```r
ui <- fluidPage(
  
  titlePanel("Predicted Deaths from Lung Disease (UK)"),
  
  sidebarLayout(
    sidebarPanel(
      numericInput("months", label = "Months to Predict", 
                   value = 72, min = 12, max = 144, step = 12),
      selectInput("interval", label = "Prediction Interval",
                  choices = c("0.80", "0.90", "0.95", "0.99"),
                  selected = "0.95"),
      checkboxInput("showgrid", label = "Show Grid", value = TRUE),
      hr(),
      div(strong("From: "), textOutput("from", inline = TRUE)),
      div(strong("To: "), textOutput("to", inline = TRUE)),
      div(strong("Date clicked: "), textOutput("clicked", inline = TRUE)),
      div(strong("Nearest point clicked: "), textOutput("point", inline = TRUE)),
      br(),
      helpText("Click and drag to zoom in (double click to zoom back out).")
    ),
    mainPanel(
      dygraphOutput("dygraph")
    )
```
</div>

## Server part of the code {.small}

<div style="font-size:23px">

```r
server <- function(input, output) {
  
  predicted <- reactive({
    hw <- HoltWinters(ldeaths)
    predict(hw, n.ahead = input$months, 
            prediction.interval = TRUE,
            level = as.numeric(input$interval))
  })
  output$dygraph <- renderDygraph({
    dygraph(predicted(), main = "Predicted Deaths/Month") %>%
      dySeries(c("lwr", "fit", "upr"), label = "Deaths") %>%
      dyOptions(drawGrid = input$showgrid)
  })
  output$from <- renderText({
    strftime(req(input$dygraph_date_window[[1]]), "%d %b %Y")      
  })
  output$to <- renderText({
    strftime(req(input$dygraph_date_window[[2]]), "%d %b %Y")
  })
  output$clicked <- renderText({
    strftime(req(input$dygraph_click$x), "%d %b %Y")
  })
  output$point <- renderText({
    paste0('X = ', strftime(req(input$dygraph_click$x_closest_point), "%d %b %Y"), 
           '; Y = ', req(input$dygraph_click$y_closest_point))
  })
```
</div>

## Result

<div align ="center"; padding-bottom: 25px>
  <img src="../images/dygraph slide .PNG" alt="check" 
  class="center" width="1000" height="550"> 
    </div>




## Creating a widget step-by-step

<h2><b>Requirements</b></h2>

  * We need to create a new R package that relies on the <span style="color:green; font-weight:bold"> htmlwidgets </span> package.
```r
install.packages("htmlwidgets")
```

## Scaffolding

To create a new widget you can call the <span style="color:purple; font-weight:bold"> scaffoldWidget </span> function to generate the basic structure for your widget. This function will:

  * Create the <span style="color:blue; font-weight:bold">.R,</span> <span style="color:grey; font-weight:bold">.js,</span> and <span style="color:green; font-weight:bold">.yaml</span> files required for your widget
  * <b>Tip</b>: If provided, take a Bower package (which is a package manager for web) name and automatically download the JavaScript library (and its dependencies) and add the required entries to the .yaml file. This method is highly preferrable because it guarantees that you get started with the right file structure. 
  
## MyWidget

We want to create a widget named ‘mywidget’ in a new package of the same name:

```r
devtools::create("mywidget")               # create package using devtools
setwd("mywidget")                          # navigate to package dir
htmlwidgets::scaffoldWidget("mywidget")    # create widget scaffolding
devtools::install()                        # install the package so we can try it
```
<div style="font-size:27px">
* This creates a simple widget that takes a single text argument and displays that text within the widgets HTML element. You can try it like this:
</div>
```r
library(mywidget)
mywidget("hello, world")
```
<div style="font-size:27px">
* This is the most minimal widget possible and doesn’t yet include a JavaScript library.
</div>

# <span style="font-weight:bold">  Chapter 8</span> <br> </br> Case Studies {data-background=#00cc66 .center}



## Case Study: Childlessness and Gender Gap By Using Ggraph Package

* In this section, we will build interactive world maps and show these in the form of an Shiny app.
* At first, we're going to start with <span style="color:purple; font-weight:bold">importing, exploring and cleaning the data</span> that datasets we're going to use. Since the data sets are dirty, we have to get them in a better shape to make more useful for us.  
* Final forms of our datasets will be like this:
<div align="center"  style = "margin-top: 20px">
  <img src="../images/dataset_example.PNG" alt="example" class="center">
</div>
<div align="center"  style = "margin-top: 20px">
  <img src="../images/dataset_example2.PNG" alt="example" class="center">
</div>

## Creating a function to build map
<div style="font-size:25px">

* Next, it’s time to define the <span style="color:blue; font-weight:bold">function</span> that we’ll use for building our world maps. The inputs to this function are the merged data frame, the world data containing geographical coordinates, and the data type, period and indicator the user will select in the R Shiny app. 
 ```r
worldMaps <- function(df, world_data, data_type, period, indicator){
  
  # Function for setting the aesthetics of the plot
  my_theme <- function () { 
    theme_bw() + theme(axis.text = element_text(size = 14),
                       axis.title = element_text(size = 14),
                       strip.text = element_text(size = 14),
                       panel.grid.major = element_blank(), 
                       panel.grid.minor = element_blank(),
                       panel.background = element_blank(), 
                       legend.position = "bottom",
                       panel.border = element_blank(), 
                       strip.background = element_rect(fill = 'white', colour = 'white'))
  }
```
</div>

## Function Continues:
<div style="font-size:25px">

```r
  # Select only the data that the user has selected to view
  plotdf <- df[df$Indicator == indicator & df$DataType == data_type & df$Period == period,]
  plotdf <- plotdf[!is.na(plotdf$ISO3), ]
  # Add the data the user wants to see to the geographical world data
  world_data['DataType'] <- rep(data_type, nrow(world_data))
  world_data['Period'] <- rep(period, nrow(world_data))
  world_data['Indicator'] <- rep(indicator, nrow(world_data))
  world_data['Value'] <- plotdf$Value[match(world_data$ISO3, plotdf$ISO3)]
  
  # Create caption with the data source to show underneath the map
  capt <- paste0("Source: ", ifelse(data_type == "Childlessness", "United Nations" , "World Bank"))
 # Specify the plot for the world map
  library(RColorBrewer)
  library(ggiraph)
  g <- ggplot() + 
    geom_polygon_interactive(data = world_data, color = 'gray70', size = 0.1,
                                    aes(x = long, y = lat, fill = Value, group = group, 
                                        tooltip = sprintf("%s<br/>%s", ISO3, Value))) + 
    scale_fill_gradientn(colours = brewer.pal(5, "RdBu"), na.value = 'white') + 
    labs(fill = data_type, color = data_type, title = NULL, x = NULL, y = NULL, caption = capt) + 
    my_theme()
  return(g)
}
```
</div>
## Last Step: Building the Shiny App
<div style="font-size:25px">
* Now we put our data in a good shape and world mapping function ready and specified.
* Let's start with UI.

```r
# Define the UI
ui = fluidPage(
  
  # App title
  titlePanel("Childlessness and Gender Gap Index Data"),
  
  # Sidebar layout with input and output definitions
  sidebarLayout(
    
    # Sidebar panel for inputs 
    sidebarPanel(
      
      # First input: Type of data
      selectInput(inputId = "data_type",
                  label = "Choose the type of data you want to see:",
                  choices = list("Childlessness" = "Childlessness", "Gender Gap Index" = "Gender Gap Index")),
      
      # Second input (choices depend on the choice for the first input)
      uiOutput("secondSelection"),
      
      # Third input (choices depend on the choice for the first and second input)
      uiOutput("thirdSelection")
    ),
```
</div>

## Ui Continues with Main Panel:

```r
 # Main panel for displaying outputs
    mainPanel(
      
      # Hide errors
      tags$style(type = "text/css",
                 ".shiny-output-error { visibility: hidden; }",
                 ".shiny-output-error:before { visibility: hidden; }"),
      
      # Output: interactive world map
      girafeOutput("distPlot")
      
    )
  )
)
```
## Server side of the app
<div style="font-size:25px">
```r
# Define the server
server = function(input, output) {
  
  # Create the interactive world map
  output$distPlot <- renderGirafe({
    ggiraph(code = print(worldMaps(df, world_data, input$data_type, input$period, input$indicator)))
  })
  
  # Change the choices for the second selection on the basis of the input to the first selection
  output$secondSelection <- renderUI({
    choice_second <- as.list(unique(df$Period[which(df$DataType == input$data_type)]))
    selectInput(inputId = "period", choices = choice_second,
                label = "Choose the period for which you want to see the data:")
  })
  
  # Change the choices for the third selection on the basis of the input to the first and second selections
  output$thirdSelection <- renderUI({
    lab <- ifelse(input$data_type == "Childlessness", "age group", "indicator")
    choice_third <- as.list(unique(df$Indicator[df$DataType == input$data_type & df$Period == input$period]))
    selectInput(inputId = "indicator", choices = choice_third,
                label = paste0("Choose the type of ", lab, " you want to explore:"))
  })
}
```
</div>
## Result

<div align="center"  style = "margin-top: 20px">
  <img src="../images/ggraph case study.PNG" alt="example" class="center">
</div>

## Case Study: Earthquake Map By Using Leaflet Package
<div style="font-size:25px">

* We used USGS's data from: https://earthquake.usgs.gov/earthquakes/search/
 * By using filtering options, we took the <span style="color:red; font-weight:bold">data</span> of a specific <span style="color:blue; font-weight:bold">time period</span> for specific <span style="color:green; font-weight:bold">locations</span> in order to use in our research.
</div> 
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/earthquake website.PNG" alt="screenshot" class="center"  width="900" height="460">
  </div>
  
## Distinguishing Depths


```r
library(shiny)
library(leaflet)
library(dplyr)
library(leaflet.extras)

data <- read.csv("./data/data.csv")
country <- data["place"]

data$depth_type <-      ## 
    ifelse(
        data$depth <= 70,
        "shallow",
        ifelse(
            data$depth <= 300 | data$depth > 70,
            "intermediate",
            ifelse(data$depth > 300, "deep", "other")
```

## Forming the UI

```r
ui <- fluidPage(mainPanel(
    #this will create a space for us to display our map
    leafletOutput(outputId = "mymap"),
    #this allows us to put the checkmarks on top of the map to
    #allow people to view earthquake depth or overlay a heatmap.
    absolutePanel(
        top = 250,
        left = 30,
        checkboxInput("markers", "Depth", FALSE),
        checkboxInput("heat", "Heatmap", FALSE)
    )
))
```

## Server part

```r
server <- function(input, output, session) {
    #define the color palette for the magnitude of the earthquake
    pal <- colorNumeric(
        palette = c(
            'gold',
            'orange',
            'dark orange',
            'orange red',
            'red',
            'dark red'
        ),
        domain = data$mag
    )
    #define the color of for the depth of the earthquakes
    pal2 <- colorFactor(palette = c('blue', 'yellow', 'red'),
                        domain = data$depth_type)
```

## Creating the Map

```r
output$mymap <- renderLeaflet({
leaflet(data) %>%
  addTiles() %>%
  addFullscreenControl(position = "topleft", pseudoFullscreen = TRUE) %>%
    setView(lng = 35, lat = 42, zoom = 5)  %>% #setting the view over
      addTiles() %>%
      addCircles(
          data = data,
          lat = ~ latitude,
          lng = ~ longitude,
          weight = 0.5,
          radius = ~ sqrt(mag) * 15000,
          popup = ~ as.character(mag),
          label = ~ as.character(paste0("Magnitude: ", sep = " ", mag)),
          color = ~ pal(mag),
          fillOpacity = 0.5
```

## Making Checkboxes Dynamic With observe Function
<div style="font-size:27px">
```r
observe({
        proxy <- leafletProxy("mymap", data = data)
        proxy %>% clearMarkers()
        if (input$markers) {
            proxy %>% addCircleMarkers(
                stroke = FALSE,
                color = ~ pal2(depth_type),
                fillOpacity = 0.2,
                label = ~ as.character(paste0("Magnitude: ", sep = " ", mag))
            ) %>%
                addLegend(
                    "bottomright",
                    pal = pal2,
                    values = data$depth_type,
                    title = "Depth Type",
                    opacity = 1
                )
        }
        else {
            proxy %>% clearMarkers() %>% clearControls()
        }
```
</div>

## Map Adjustments with Using leafletproxy Function

```r
observe({
        proxy <- leafletProxy("mymap", data = data)
        proxy %>% clearMarkers()
        if (input$heat) {
            proxy %>%  addHeatmap(
                lng =  ~ longitude,
                lat =  ~ latitude,
                intensity = ~ mag,
                blur =  10,
                max = 0.05,
                radius = 15
            )
        }
        else{
            proxy %>% clearHeatmap()
        }
```

## Result

<div align ="center"; padding-bottom: 25px>
  <img src="../images/earthquake case study.PNG" alt="screenshot" class="center">
  </div>
  
  
## Case Study: Migration By Using Leaflet Package

 * We used Aegean Boat Report's data from: https://aegeanboatreport.com/reports/ 
 * By using Excel, we shaped this data to make it useful for our research.
 
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/excel.PNG" alt="excel" class="center">
  </div>
  
## Using Leaflet

* For creating a map we used <span style="color:green; font-weight:bold">Leaflet</span> library.
* <span style="color:green; font-weight:bold">Leaflet</span> is a open source <span style="color:grey; font-weight:bold">JavaScript</span> library for creating interactive maps.
* It can be implemented and used in <span style="color:blue; font-weight:bold">Shiny</span> easily.
* <span style="color:green; font-weight:bold">Leaflet</span> gives the opportunity of adding informational popups to particular part of maps.
* <div align ="center"; padding-bottom: 25px>
  <img src="../images/leaflet.PNG" alt="leaflet" class="center">
  </div>

## Result

<div align ="center"; padding-bottom: 25px>
  <img src="../images/case study result.PNG" alt="result" width="1500" height="400" class="center">
  </div>
