# Exercise 1 - Combine Reviews and Master Data

In this exercise you will combine product and review data to a 
joint data set that can be used for analytics.

* You will learn how to explore the data sets with the Meta-Data Explorer
* You will do the first steps with the Pipeline Modeler to join two data sets and
  write the result as CSV to the S3 blob store.

## Exercise 1.1: Explore the Input Data

1. Click the Metadata Explorer tile to open the application.
<br>![](./images/003_launchpad_metadata.png)
<br/>

2. Click the *Browse Connections* button on the left to open the browser.
<br>![](./images/004_metadata_overview.png)
<br/>

3. Open the *S3* connection.
<br>![](./images/005_metadata_browse_s3.png)
<br/>

4. Click on the *Factsheet* icon on of the *Product Reviews* data set to show details.
<br>![](./images/006_metadata_s3.png)
<br/>

5. In the Factsheet view choose the *Data Preview* Tab to see a sample of the actual data.
The review data set has a `PRODUCT_ID` to refer to the actual product in our master data.
The review in textual format is available in the `REVIEW_TEXT` column.
<br>![](./images/007_metadata_factsheet_product_reviews.png)
<br/>

6. Go back to the browsing view by clicking the *back* icon located top-left.
<br>![](./images/008_metadata_back.png)
<br/>

7. Open the *HANADB* connection.
<br>![](./images/009_metadata_browse_hanadb.png)
<br/>

8. Search for *DAT263* (the schema is used also by another exercise) and open the schema.
<br>![](./images/010_metadata_search_dat263.png)
<br/>

9. Open the Factsheet of the *PRODUCT* table.
<br>![](./images/011_metadata_browse_product.png)
<br/>

10. In the *Data Preview* tab you see a sample of the table. You recognize the `PRODUCTID` column
which we can use to join the product details with the reviews.
<br>![](./images/012_metadata_factsheet_products.png)
<br/>

## Exercise 1.2: Combine the Data Sets

11. Go back to the launchpad tab in the browser and open the *Modeler*
<br>![](./images/020_launchpad_modeler.png)
<br/>

12. The resource panel on the left will have the vertical graph tab selected. Here, you see a couple of
example graphs shipped with SAP DI. We will later also find our own graphs in this resource panel.
Click the `+` icon to create a new graph...
<br>![](./images/021_modeler_create_graph.png)
<br/>

13. Fill the graph name (unique) and the description similar to the screenshot (e.g., *data_preparation*).
<br>![](./images/022_modeler_save_graph.png)
<br/>

14. Now, select the *Operator* tab and search for `file consumer`. The file consumer
in the *Structured Data Operators* category will be shown. Select the operator and drag
into the graph.
<br>![](./images/023_modeler_search_file_consumer.png)
<br/>

15. By selecting the operator you will see that the *Configuration Panel* on the right
will switch to the operator specific parameters. For *Storage Type* choose `S3`, since we want
to consume the review file from a S3 connection. 
<br>![](./images/024_modeler_file_consumer_s3.png)
<br/>

16. Edit the *S3 Connection* parameter. 
<br>![](./images/025_modeler_file_consumer_connection_s3.png)
<br/>

17. Choose the connection named `S3` as shown in the screenshot and confirm the dialog.
<br>![](./images/026_modeler_file_consumer_s3_select.png)
<br/>

18. Now, click on the path parameter to choose the file. You will see a file browser
with a list of files. Choose the file `Product_Reviews`.
<br>![](./images/027_modeler_file_consumer_dataset.png)
<br/>

19. After confirming the file, you can click the *Data Preview* link to show a sample of the data
similar to the Factsheet in the Meta-data Explorer...
<br>![](./images/028_preview.png)
<br/>

20. by this, we can make sure we work with the correct data set.
<br>![](./images/029_preview.png)
<br/>

21. In the left panel, choose the *Operators* tab and search for `Table Consumer`.
<br>![](./images/030_save.png)
<br/>

22. Select the *Table Consumer* Operator under 
the *Structured Data Operators* category and drag into the graph.
<br>![](./images/031_table_consumer.png)
<br/>

23. For the new operator, configure the database type to be `HANA`.
<br>![](./images/032_hana_type.png)
<br/>

24. In the connections parameter dialog select the `HANADB` connection.
<br>![](./images/033_hana_connection.png)
<br/>

25. As input, double click the `DAT263` schema.
<br>![](./images/034_dataset_1.png)
<br/>

26. Select the `PRODUCT` table and confirm.
<br>![](./images/034_dataset_2.png)
<br/>

27. Click the `Data Preview` link to see a sample of the table.
<br>![](./images/035_preview.png)
<br/>

28. Make sure the product table is configured correctly by checking the data.
<br>![](./images/036_preview.png)
<br/>

29. Now, search for the `Data Transform` operator and drag into the graph.
<br>![](./images/037_data_transform.png)
<br/>

30. Connect the *Table Consumer* output with the *Data Transform* operator.
You will see a port created in the *Data Transform* operator and a link connecting
the operators.
<br>![](./images/038_connection.png)
<br/>

31. Connect the *File Consumer* output with the *Data Transform* operator.
<br>![](./images/039_connection.png)
<br/>

32. Double-click on the *Data Transform* operator to open the ETL Editor.
<br>![](./images/040_click.png)
<br/>

33. Drag the *Join* operator into the ETL editor.
<br>![](./images/041_join.png)
<br/>

34. Connect the upper input with the join operator. Note, the input name equals the
input port name of the *Data Transform* operator and is created automatically.
You can also create the port manually (show in later exercise).
<br>![](./images/042_join_connect.png)
<br/>

35. Connect the lower input with the join operator. Then, double-click on the *Join* operator
to open the parametrization.
<br>![](./images/043_join_connect.png)
<br/>

36. Click on the `PRODUCT_ID` column of the upper data set and drag a link to the `PRODUCTID` column
of the lower data set.
<br>![](./images/044_join_attributes.png)
<br/>

37. The join condition will be created and shown in the bottom panel.
Change the join to be *Left Outer*, to have also products in the resulting
data set that have no reviews.
<br>![](./images/045_left_outer.png)
<br/>

38. Click the column you want to have in the result. The column will be marked
by a blue circle.
<br>![](./images/046_select_attributes.png)
<br/>

39. Click the *back* button to go to the ETL view again.
<br>![](./images/046_z_back.png)
<br/>

40. Right-click on the ouput port of the join operator and select *Create Data Target*.
<br>![](./images/047_create_target.png)
<br/>

41. In case the formatting looks off, click the *Format* button in the top panel (as shown in screenshot).
<br>![](./images/048_layout.png)
<br/>

42. Save the changes and click the back button to go to back to the pipeline view.
<br>![](./images/049_save.png)
<br/>

43. You may need to confirm the saving of layout information in case you used the automated
layouting.
<br>![](./images/050_save_layout.png)
<br/>

44. In the pipeline view, search for the `Structured File Producer` and drag into the graph.
<br>![](./images/051_structured file producer.png)
<br/>

45. Connect the output of the *Data Transform* operator with the file producer.
<br>![](./images/052_connect.png)
<br>![](./images/053_connect.png)
<br/>

47. Configure `S3` as storage type. 
<br>![](./images/054_s3.png)
<br/>

48.Configure `S3` as connection, similar to what was configured for the input. 
<br>![](./images/055_s3.png)
<br/>

49. As output path, add the filename 
<br>![](./images/056_path.png)
<br>![](./images/057_path.png)
<br/>

51. Search for the `Wiretap` in the operators section and drag into the graph.
<br>![](./images/058_wiretap.png)
<br/>

52. Execute the graph by clicking the *Run* icon in the top panel. In the status
panel the pipeline will appear showing the status `pending`. This shows that
the graph is scheduled on the Kubernetes environment.
<br>![](./images/059_connect_run.png)
<br/>

53. Once the graph is running, you can click the *Wiretap* and choose the top icon to
open the debug view.
<br>![](./images/060_wiretap_open.png)
<br/>

54. You will see that a single file has been produced by the *File Producer*.
Note, that the graph keeps running until you explicitly stop by hitting the stop icon
on the top panel.
<br>![](./images/061_wiretap_show.png)
<br/>

## Exercise 1.3: Cleanup and Productize

55. If we want the graph to stop automatically once the data has been consuemd
we can add a *Graph Terminator* operator. Search for the operator, drag into the graph
and connect to the output of the file producer.
<br>![](./images/062_terminator.png)
<br/>

56. If you now execute the graph you will see that it will be completed automatically.
<br>![](./images/063_exec.png)
<br/>

57. You can now check for the produced file using the Meta-data Explorer.
For this, simply go to the browsing section again and look for the filename provided
by you in the file producer.
<br>![](./images/064_show_new_data.png)
<br/>

58. In the *Data Preview* tab you will see the joined data. Most likely, however, the
column names will not be shown.
<br>![](./images/065_factsheet.png)
<br/>

59. To have the names beeing added to the CSV file we need to go back to the graph
and go to the configuration panel of the file producer. 
<br>![](./images/066_adapt_file_writer.png)
<br/>

60. Open the *Additional Parameters* dialog and select *Header Included* to be `true`. 
<br>![](./images/067_with_header.png)
<br/>

61. After executing the graph again you can see the updated column names in the Meta-data Explorer.
<br>![](./images/068_factsheet.png)
<br/>

## Summary

Congratulations. You've created a re-usable pipeline to join the review with the product data and stored it for further analysis.

Continue to [Exercise 2](../ex2/README.md)
