+++
title = "Statistical Forecasting"
weight= 80
description = "Learn how to create statistical forecasts with N2."
images = ["images/logo-gray.png"]
date = "2025-12-12T01:46:39.298Z"
+++

## Prerequisites
- The N2 Core modules, N2 Action module and the built-in Contacts module must be installed.

  If you have not installed the N2 modules yet, please refer to the [Quick Start](/n2-doc/20-getting-started) guide.

- Complete the [Simple Workflow](../20-simple) tutorial.

  Please refer to the [Simple Workflow](../20-simple) tutorial to understand the basics for creating N2 workflow.

## Recommended Additional Modules
Because forecasting relies on historical data, it is recommended to install the **Demo Data Generator** and **Demo Sales Data Generator** modules as well — unless you already have sufficient historical data or are using another dummy data generator.

## Creating Statistical Forecasts
In this section, you will create a workflow that creates a forecast using the nodes from N2 Forecast module.

1. Go to N2 -> Configuration -> Forecast Store.
2. Create new Forecast Store, name it `My Forecast Store` and save it.
3. Create a new graph.
4. Add `StartNode`, `ForecastContextNode`, `BrowseDataNode`, `ForecastDataNode`, `TrainNode`, `ForecastModelStoreNode`, `ForecastNode`, `ForecastNode`, `ForecastResultNode`, `HistoricAverageNode`, `AutoEtsNode`, `FillGapsNode`, `TimeAggregateNode` and connect them. Refer to the figure below on how these nodes are connected.
5. Set the `Model Store` field on the `ForecastContextNode` to `My Forecast Store`.
6. Set the `Model` field on the `BrowseDataNode` to `Sales Order`.
7. Set the `Order by` field on the `ForecastDataNode` to `Order Date`.
8. Add these field mapping to the `ForecastDataNode`:
  1. Field `Order Date` (`date_order` ) is mapped to `ds` with `DateTimeSeries` role.
  2. Field `Total` (`amount_total`) is mapped to `amount` with `Target` role.
9.  Set the `Horizon` field on the `ForecastNode` to `7`.
10. Set the `Season Length` field on the `AutoEtsNode` to `7`.
11. Save and process the graph.
  {{< figure
  src="./images/n2-forecast.png"
  alt="Forecasting workflow."
  caption="Workflow to create forecasts with Historic Average and Auto ETS."
  width="100%"
  >}}
12. Click the `Forecast Visualizer` button to show the forecast visualizer.
13. Run the graph.
  {{< figure
  src="./images/n2-forecast-visualizer.png"
  alt="Forecast visualizer."
  caption="Workflow with forecast visualizer shown."
  width="100%"
  >}}

## Explanation
This tutorial demonstrates how to build a workflow that generates statistical forecasts from historical data and visualizes the results using the Forecast Visualizer.

The workflow prepares time series data, trains forecasting models, and produces future predictions based on past sales behavior.

### Statistical Forecasting with StatsForecast
The N2 Forecast module exposes the StatsForecast library as N2 nodes.
This allows you to:

* Train statistical forecasting models directly within N2 workflows
* Use multiple forecasting strategies, such as Historic Average and Auto ETS
* Store and reuse trained models via Forecast Stores
* Visualize forecast results interactively

By combining these nodes, you can quickly experiment with different forecasting models and horizons using the same underlying data.

## Next Steps
* Try adjusting the Horizon value to forecast further into the future.
* Experiment with different season lengths or additional forecasting nodes.
* Replace demo data with your own historical business data to generate real forecasts.