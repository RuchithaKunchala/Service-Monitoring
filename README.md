# Service Monitoring Dashboard
This document will help you know about Database Monitoring Dashboard and some related aspects. The currently illustriated Service Monitoring Dashboard is built to monitor the Time Series Data Base for Standard Chartered Applications taken in real time ensuring availabilty and performance.

# Need for Monitoring?
Continuous Monitoring is a process to monitor and identify compliance issues and security risks throughout each phase of DevOps and IT operations lifecycle. Monitoring the services not only gives you the ability to respond quickly to problems and outages, it can also help to anticipate and prevent errors that may occur in the future which sometimes may lead to system crash or frequent ups and downs in the server. The currently built Service Monitoring Dashboard allows the users to keep an eye and view into the performance & health of an application. It also helps the viewers to quickly detect and resolve any issues. 

# Dependencies used

![logo-horizontal](https://user-images.githubusercontent.com/60230072/126178049-0157d7fa-4839-4be3-a755-b6e58ebc4195.png)

Grafana allows you to query, visualize, alert on and understand your metrics no matter where they are stored. Create, explore, and share dashboards with your team and foster a data driven culture:

* **Visualize**: Fast and flexible client side graphs with a multitude of options. Panel plugins offer many different ways to visualize metrics and logs.
* **Dynamic Dashboards**: Create dynamic & reusable dashboards with template variables that appear as dropdowns at the top of the dashboard.
* **Explore Metrics**: Explore your data through ad-hoc queries and dynamic drilldown. Split view and compare different time ranges, queries and data sources side by side.
* **Explore Logs**: Experience the magic of switching from metrics to logs with preserved label filters. Quickly search through all your logs or streaming them live.
* **Alerting**: Visually define alert rules for your most important metrics. Grafana will continuously evaluate and send notifications to systems like Slack, PagerDuty, VictorOps, OpsGenie.
* **Mixed Data Sources**: Mix different data sources in the same graph! You can specify a data source on a per-query basis. This works for even custom datasources.

![logo-horizontal](https://user-images.githubusercontent.com/60230072/126186233-33df169d-2582-407b-b6ec-9eea12143476.png)

Prometheus, is a systems and service monitoring system. It collects metrics from configured targets at given intervals, evaluates rule expressions, displays the results, and can trigger alerts when specified conditions are observed.

The features that distinguish Prometheus from other metrics and monitoring systems are:

* A **multi-dimensional** data model (time series defined by metric name and set of key/value dimensions)
* PromQL, a **powerful and flexible query language** to leverage this dimensionality
* No dependency on distributed storage; **single server nodes** are autonomous
* An HTTP **pull model** for time series collection
* **Pushing time series** is supported via an intermediary gateway for batch jobs
* Targets are discovered via **service discovery** or **static configuration**
* Multiple modes of **graphing and dashboarding support**
* Support for hierarchical and horizontal **federation**

# Getting Started
