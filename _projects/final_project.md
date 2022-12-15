---
name: Final Project Part 3
author: Trevin Kurniawan
tools: [Python, HTML, vega-lite]
description: This project showcases crashes in the city of Chicago

remote_projects:
   -online_cv_public
---
# Crash Reports in Chicago

# Contextual Visualizations

We will be using matplotlib to plot the count of car crashes in different weather conditions. We are also going to be using a bar graph; this visualization will showcase the trend of car crashes according to the weather conditions.

---
{
  "$schema": "https://vega.github.io/schema/vega/v5.json",
  "width": 700,
  "height": 200,
  "padding": 5,
  "data": [
    {
      "name": "table",
      "values": [
        {"category": "CLEAR", "amount": 317},
        {"category": "RAIN", "amount": 142},
        {"category": "UNKNOWN", "amount": 18},
        {"category": "CLOUDY/OVERCAST", "amount": 12},
        {"category": "SNOW", "amount": 8},
        {"category": "FREEZING RAIN/DRIZZLE", "amount": 2}
      ]
    }
  ],
  "signals": [
    {
      "name": "tooltip",
      "value": {},
      "on": [
        {"events": "rect:mouseover", "update": "datum"},
        {"events": "rect:mouseout", "update": "{}"}
      ]
    }
  ],
  "scales": [
    {
      "name": "xscale",
      "type": "band",
      "domain": {"data": "table", "field": "category"},
      "range": "width",
      "padding": 0.05,
      "round": true
    },
    {
      "name": "yscale",
      "domain": {"data": "table", "field": "amount"},
      "nice": true,
      "range": "height"
    }
  ],
  "axes": [
    {"orient": "bottom", "scale": "xscale"},
    {"orient": "left", "scale": "yscale"}
  ],
  "marks": [
    {
      "type": "rect",
      "from": {"data": "table"},
      "encode": {
        "enter": {
          "x": {"scale": "xscale", "field": "category"},
          "width": {"scale": "xscale", "band": 1},
          "y": {"scale": "yscale", "field": "amount"},
          "y2": {"scale": "yscale", "value": 0}
        },
        "update": {"fill": {"value": "steelblue"}},
        "hover": {"fill": {"value": "red"}}
      }
    },
    {
      "type": "text",
      "encode": {
        "enter": {
          "align": {"value": "center"},
          "baseline": {"value": "bottom"},
          "fill": {"value": "#333"}
        },
        "update": {
          "x": {"scale": "xscale", "signal": "tooltip.category", "band": 0.5},
          "y": {"scale": "yscale", "signal": "tooltip.amount", "offset": -2},
          "text": {"signal": "tooltip.amount"},
          "fillOpacity": [
            {"test": "isNaN(tooltip.amount)", "value": 0},
            {"value": 1}
          ]
        }
      }
    }
  ],
  "config": {}
}
---
