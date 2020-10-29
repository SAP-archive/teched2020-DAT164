# Exercise 1 - Combine Reviews and Master Data

In this exercise you will combine product and review data to a joint data set that can be used for analytics.
The data could either be processed directly, e.g., it can be pushed to SAP Analytics Cloud, input to further data analysis operations, or it can be stored to be used directly in other data pipelines.

Here, we will show how to combine the data and store it using the data transform operators.

## Configure Input Source

1. Open the SAP Data Pipelines Modeller
<br>![](./images/1000_open_modeller.png)
<br/>

1. Create a new Graph
<br>![](./images/1020_create_graph.png)
<br/>

1. In the operators section, search for "Structured File Reader" and drag the operator into the graph
<br>![](./images/1030_search_file_consumer.png)
<br/>

1. Configure the operator as shown in the image
<br>![](./images/1041_config_file_consumer.png)
<br>![](./images/1050_config_storage_type_s3.png)
<br/>

1. In the operators section, search for "Table Consumer" and drag the operator into the graph
<br>![](./images/1080_select_table_consumer.png)
<br/>

1. Configure the table consumer
<br>![](./images/1090_config_table_consumer.png)
<br/>

1. In the operators section, search for "Data Transform" and drag the operator into the graph
<br>![](./images/1110_search_data_transform.png)
<br/>

1. Connect the file consumer and the table consumer to the data transform operator
<br>![](./images/1120_connect_file_consumer.png)
<br>![](./images/1130_connect_table_consumer.png)
<br>![](./images/1135_connected.png)
<br/>

1. Double click the data transform operator to get into the ETL view
<br>![](./images/1140_transform_join.png)
1. Connect the two data inputs to the join operator
<br>![](./images/1142_join_connect1.png)
<br>![](./images/1143_join_connect2.png)
<br/>


## Summary

Now that you have ... 
Continue to - [Exercise 2](../ex2/README.md)
