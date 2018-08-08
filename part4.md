# Welcome in the Step 4 about building a crypto dashboard with Kibana.

In this part, you will use the ELK microservices to create your first crypto dashboard with Kibana.

The agenda of this section is about:
1. Accessing to Kibana
2. Sourcing the ElasticSearch DataSource
3. Creating your first search with Kibana
4. Creating your first charts with Kibana
5. Creating your first dashboard with Kibana
6. Realizing your first crypto dashboard with Kibana

## About Kibana
Kibana is an open source data visualization plugin for Elasticsearch. It provides visualization capabilities on top of the content indexed on an Elasticsearch cluster. Users can create bar, line and scatter plots, or pie charts and maps on top of large volumes of data. The combination of Elasticsearch, Logstash, and Kibana, referred to as the "ELK Stack". Logstash provides an input stream to Elastic for storage and search, and Kibana accesses the data for visualizations such as dashboards.

More information about Kibana are available [here](https://www.elastic.co/products/kibana).

## 1 - Accessing to Kibana
Please, refer to your provisionned ICP ELK service in order to connect to the Kibana web interface. You simply need to use your web browser. The kibana default port is 5601.

Note that your IP adress is different, you must adapt the following accordingly.
http://<ICP_ELK_Services_URL>:5601

A reachable kibana web interface should look like as follow:
![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99e%CC%81cran%202018-06-20%20a%CC%80%2016.58.10%20(2).png)

That is a good start. You can connect to Kibana. Now, let's see how Kibana can connect to a source of data (in our case the Elasticsearch DB).

## Sourcing the ElasticSearch DataSource

It is time to create an Index Pattern to Connect to Elasticsearh. To use Kibana, you have to tell it about the Elasticsearch indices that you want to explore by configuring one or more index patterns. 

Click on the left tab bar to *"Management"*.

### A. Define an index pattern named "monitor*"
An index pattern identifies one or more Elasticsearch indices that you want to explore with Kibana. Kibana looks for index names that match the specified pattern. An asterisk (*) in the pattern matches zero or more characters. For example, the pattern myindex-* matches all indices whose names start with myindex-, such as myindex-1 and myindex-2.

An index pattern can also simply be the name of a single index.

**Action:** Click on Index pattern area, and fill the tab with **monitor*** as follow. 

**Action:** Then click to **Next Step**.

![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.44.34%20(2).png)

### B. Save your defined an index pattern

Your index contains a timestamp field that you want to use to perform time-based comparisons, select the Index contains time-based events option and select the index field that contains the timestamp. Kibana reads the index mapping to list all of the fields that contain a timestamp.

**Action:** In configure settings panel, please select **@Timestamp**.

**Action:**  Then validate by clicking on **Create** index pattern.

![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.46.34%20(2).png)

### C. Check your new defined pattern

Here you are, you just sourced Kibana to your crypto monitoring Elasticsearch DB and its content. The structure of the index monitor* is displayed front of you.

![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.46.45%20(2).png)

It is now time to capture a set of information from the DB thanks to a search.
**Action:** Click on the left tab bar on **"Discover"**. 

## 3 - Creating your first search with Kibana

You can interactively explore your data from the Discover page. You have access to every document in every index that matches the selected index pattern. You can submit search queries, filter the search results, and view document data. You can also see the number of documents that match the search query and get field value statistics. If a time field is configured for the selected index pattern, the distribution of documents over time is displayed in a histogram at the top of the page.

![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99e%CC%81cran%202018-06-20%20a%CC%80%2017.07.05%20(2).png)

#### B. Let's start to discover and to explore crypto data sent by LinuxONE virtual machine.

When you submit a search request, the histogram, Documents table, and Fields list are updated to reflect the search results. The total number of hits (matching documents) is shown in the toolbar. The Documents table shows the first five hundred hits. 

By default, the hits are listed in reverse chronological order, with the newest documents shown first. You can reverse the sort order by clicking the Time column header. You can also sort the table by the values in any indexed field.

**Action:** Click on **Available** field MODE as follow:
![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.46.45%20(2).png)

**Action:** Click on **add** field MODE as follow:
![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.47.22%20(2).png)

Now we are good. Let's save this search with a name we can refer later. Saving searches enables you to reload them into Discover and use them as the basis for visualizations. Saving a search saves both the search query string and the currently selected index pattern.

**Action:** Click **Save** in the Kibana toolbar, and enter the name **icastats** for the search and click **Save**.

![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.47.40%20(2).png)

Once save, we are good to start to create some visual.

**Action:** Click on the left tab bar on **Visualize**

## Creating your first visualization

Visualize enables you to create visualizations of the data in your Elasticsearch indices. You can then build dashboards that display related visualizations. Kibana visualizations are based on Elasticsearch queries. By using a series of Elasticsearch aggregations to extract and process your data, you can create charts that show you the trends, spikes, and dips you need to know about. 

For the following, You will create visualizations from a search saved from Discover, **icastats**.

**Action:** Click the **Create** new visualization button or the **+** button.

**Action:** Choose the visualization type: **Vertical Bar**

![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.48.41%20(2).png)

**Action:** Specify a search query to retrieve the data for your visualization.

To build a visualization from a saved search, click the name of the saved search you previously saved (icastats). This opens the visualization builder and loads the selected query. When you build a visualization from a saved search, any subsequent modifications to the saved search are automatically reflected in the visualization. To disable automatic updates, you can disconnect a visualization from the saved search.

![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.48.53%20(2).png)

#### 5. Vizualization builder
In the visualization builder, choose the metric aggregation for the visualization’s Y axis: Average
In the visualization builder, choose the metric field for the visualization’s Y axis: AES CBC
For the visualizations X axis, select a bucket aggregation: Date Histogram
For the visualizations X axis, select a bucket field: @Timestamp
For the visualizations X axis, select a bucket interval: Auto

Now click on play button as follow:
![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.49.17%20(2).png)

You should be able to visualize incoming crypto metrics with a bar chart.

#### 6. Now on the top right bar, click on Save.

#### 7. Save as "AES" your first vizualization chart.
![alt text](https://github.com/guikarai/ELK-CPACF/blob/master/images/Capture%20d%E2%80%99%C3%A9cran%202018-05-24%20%C3%A0%2011.47.40%20(2).png)

Repeat the creation of visualization with DES, TDES, SHA-1 and DRBG-SHA-512. Your visualization collection should look like the following:
Capture d’écran 2018-05-24 à 11.51.53 (2)

## Creating your first dashboard

Capture d’écran 2018-05-24 à 11.52.10 (2)

Capture d’écran 2018-05-24 à 11.52.15 (2)

Capture d’écran 2018-05-24 à 11.52.32 (2)

Capture d’écran 2018-05-24 à 11.52.55 (2)
