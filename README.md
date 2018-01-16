
<!-- README.md is generated from README.Rmd. Please edit that file -->
fullcalendarWidget
==================

The goal of fullcalendarWidget is to provide interactive calendars as an HTMLWidget using the [fullcalendar library](https://fullcalendar.io).

Installation
------------

You can install fullcalendarWidget from github with:

``` r
# install.packages("devtools")
devtools::install_github("CannaData/fullcalendarWidget")
```

Example
-------

This is a basic example which shows you how to solve a common problem:

``` r
library(shiny)
library(fullcalendarWidget)

ui <- fluidPage(fullcalendarOutput("test"))

server <- function(input, output, server) {
  output$test <- renderFullcalendar({
    fullcalendar(
      events = data.frame(
        title = c("Event 1", "Event 2"),
        start = Sys.Date() + 0:1,
        color = c("blue", "orange")
      ),
      options = list(header = list(
        left = "",
        center = "",
        right = "prev,next"
      )),
      callbacks = list(
        dayClick = DT::JS(
          "function(date, jsEvent, view) {
          alert('Clicked on: ' + date.format());
  }"
        )
        )
        )
  })
  }

shinyApp(ui, server)
```
