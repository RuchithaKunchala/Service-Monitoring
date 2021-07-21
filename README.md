# Service Monitoring Dashboard
This document will help you know about Database Monitoring Dashboard and some related aspects. The currently illustriated Service Monitoring Dashboard is built to monitor the Time Series Data Base for Applications taken in real time ensuring availabilty and performance.

# Need for Monitoring?
Continuous Monitoring is a process to monitor and identify compliance issues and security risks throughout each phase of DevOps and IT operations lifecycle. Monitoring the services not only gives you the ability to respond quickly to problems and outages, it can also help to anticipate and prevent errors that may occur in the future which sometimes may lead to system crash or frequent ups and downs in the server. The currently built Service Monitoring Dashboard allows the users to keep an eye and view into the performance & health of an application. It also helps the viewers to quickly detect and resolve any issues. 

# Dependencies used
### Grafana

Grafana allows you to query, visualize, alert on and understand your metrics no matter where they are stored. Create, explore, and share dashboards with your team and foster a data driven culture. It enables to visualise fast and flexible client-side graphs with a multitude of options.

* **Visualize**: Fast and flexible client side graphs with a multitude of options. Panel plugins offer many different ways to visualize metrics and logs.
* **Dynamic Dashboards**: Create dynamic & reusable dashboards with template variables that appear as dropdowns at the top of the dashboard.
* **Explore Metrics**: Explore your data through ad-hoc queries and dynamic drilldown. Split view and compare different time ranges, queries and data sources side by side.
* **Explore Logs**: Experience the magic of switching from metrics to logs with preserved label filters. Quickly search through all your logs or streaming them live.
* **Alerting**: Visually define alert rules for your most important metrics. Grafana will continuously evaluate and send notifications to systems like Slack, PagerDuty, VictorOps, OpsGenie.
* **Mixed Data Sources**: Mix different data sources in the same graph! You can specify a data source on a per-query basis. This works for even custom datasources.

### Prometheus 

Prometheus is a systems and service monitoring system. It collects metrics from configured targets via a pull model at given intervals, evaluates rule expressions, displays the results, and can trigger alerts when specified conditions are observed. 

The features that distinguish Prometheus from other metrics and monitoring systems are:

* A **multi-dimensional** data model (time series defined by metric name and set of key/value dimensions)
* PromQL, a **powerful and flexible query language** to leverage this dimensionality
* No dependency on distributed storage; **single server nodes** are autonomous
* An HTTP **pull model** for time series collection
* **Pushing time series** is supported via an intermediary gateway for batch jobs
* Targets are discovered via **service discovery** or **static configuration**
* Multiple modes of **graphing and dashboarding support**
* Support for hierarchical and horizontal **federation**

### HTTP Endpoints

Endpoints allow you to monitor and interact with your application. Spring boot actuator provides inbuilt HTTP endpoints to any application for health checks and metrics for different monitoring and management purposes. These Actuator endpoints are exposed over JMX and HTTP, most of the times HTTP based actuators endpoints are used because they are easy to access over the browser.

# Getting Started

### INstalling the Services

Grafana and Prometheus, both the packages are installed on Unix Machine. 
Use the below command to download Grafana,
```sh
   https://artifactory.global.standardchartered.com/artifactory/generic-release/grafana-artifacts/grafana-6.6.0.linux-amd64.tar.gz
  ```

Next extract the tar package,
```sh
   tar –xvzf grafana-6.6.0.linux-amd64.tar.gz
  ```

Move to the Grafana package. Now, to start the service we have to execute the following command:
```sh
   ./grafana-server
```

NOTE: To restart the Grafana Service, kill the PID of Grafana and run the above-mentioned command again.

Command to kill the current PID,
```sh
   kill -9 $(lsof -t -i:3000)
```

Go to https://prometheus.io/download/

Download the following command to any path in your Linux server.
```sh
   prometheus-2.28.1.linux-amd64.tar.gz
```

Next extract the tar package,
```sh
   tar –xvzf  prometheus-2.28.1.linux-amd64.tar.gz
```

Move to the Prometheus package. Now, to start the service execute the following command,
```sh
   ./prometheus
```

NOTE: To restart the Prometheus Service, kill the PID of Grafana and run the above-mentioned command again.

Command to kill the current PID,
```sh
   kill -9 $(lsof -t -i:9090)
```

### Configuring HTTP Endpoints

Configure Prometheus to monitor the hosts which are exposed through http endpoints. In order to do this, modify Prometheus’s configuration file. By default, Prometheus looks for the file prometheus.yml in the current working directory.
To get more insights onto configuration of the YAML file, check the following Documentation on Prometheus website,

https://prometheus.io/docs/introduction/first_steps/

Here’s a sample configuration that is automatically available on YAML file of prometheus:

```sh
global:
  scrape_interval: 10s

  external_labels:
    monitor: 'media_search'

scrape_configs:
  - job_name: 'media_search'

    scrape_interval: 10s

    static_configs:
      - targets: ['localhost:9888', 'localhost:9988', 'localhost:9989']
``` 

The above sample file is configured such that it’s scraping metrics from the servers running at localhost:9888, localhost:9988 and localhost:9989

In prometheus terms, an endpoint you can scrape is called an instance, usually corresponding to a single process. 
A collection of instances with the same purpose, a process replicated for scalability or reliability for example, is called a job.

### Integrating Prometheus to Grafana

After both Grafana and Prometheus services are installed successfully, follow the below steps:
Now that the Grafana server is up, we can configure it from our web-browser. Open the following URL from the browser,
http://localhost:3000 or 
http://IP_address_of_server:3000

After logging in, we would then be directed to the homepage, here we would configure the data source i.e., Prometheus. Click on ‘Add Data Source’

Next select ‘Prometheus’ & press ‘Select’,

Next, we need to enter the Prometheus details. Once you have entered the details correctly, click on ‘Save & Test’, if details entered are correct you will get the message ‘Data source is working’,

Once the data source has been added successfully, we can either create our own custom dashboard or can use one of many dashboards available on the Grafana official website.

That’s it! Now the Prometheus should start up and you should be able to browse to a status page about itself at the following URL,

http://localhost:9090/ or 
http://IP_address_of_server:9090/

Give it about 30 seconds to collect data about itself from its own HTTP metrics endpoint.
You can also verify that Prometheus is serving metrics about itself by navigating to its own metrics endpoint,

http://localhost:9090/metrics or
http://IP_address_of_server:9090/metrics

### Querying Data

Prometheus provides a functional query language called PromQL (Prometheus Query Language) that lets the user select and aggregate time series data in real time. The result of an expression can either be shown as a graph, viewed as tabular data in Prometheus’s expression browser, or consumed by external system via the HTTP API.

You can refer the following link, which has some examples, for a better understanding,

https://prometheus.io/docs/prometheus/latest/querying/examples/

### Building Dashboard

This covers the main aspects of the project building. You can create a custom dashboard that is specific to your application. The dashboard can be built by either starting from scratch or duplicating an existing dashboard.

Creating a Dashboard from scratch 

1.	Click on the Grafana logo in the left-hand corner.
2.	Open the Dashboards dropdown.
3.	Click on New.
4.	Select the type of panel you want to display (Graph, singlestat, table, pie chart, etc).
5.	Click on the Panel Title and then click on the edit button as depicted below:

6.	From here, simply designate the desired metrics to display. A completed example is pictured below:

![huhu](https://user-images.githubusercontent.com/60230072/126484620-1cd54986-c06d-4ebc-aba5-c4add07d8e88.jpg)

The above screenshot contains several features of interest:
1.	In order to query the data set and see a visualization, you will need to specify a query. Below the Queries to source tab, you will see an empty query with a select metric option. Click here to begin enumerating the query. Section already provides dashboards for a number of common queries by default, but you can use this technique to visualize any relevant metrics that are not already being reported.
2.	Grafana dashboards can perform and visualize multiple queries simultaneously. This allows you to compare two separate metric values, such as 4xx and 5xx errors.
Finally, save your changes by clicking the Save icon on the top of the screen.
In the similar way, we can create many panels and make a dynamic dashboard for monitoring different services.


# Summary

The currently built Service Monitoring Dashboard monitors 2 different micro-services from different environments in real time while ensuring availability and performance. It monitors metrics such as the CPU Usage, JVM Memory, Garbage Collection, Connection Pool and some other basic statistics. 

# References
1.	Udemy
2.	Grafana Documentation
3.	Prometheus Documentation
4.	YouTube
