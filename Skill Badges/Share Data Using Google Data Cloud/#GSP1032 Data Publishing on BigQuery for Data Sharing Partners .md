
# #GSP1032 Data Publishing on BigQuery for Data Sharing Partners 

## Overview
<p> A common scenario is where a Google Cloud Data Sharing Partner has proprietary datasets that customers can use for their analytics use cases. Customers need to subscribe to this data, query it within their own platform, then augment it with their own datasets and use their visualization tools for their customer facing dashboards. This enables Data Sharing Partners to simplify and accelerate how they build and deliver value from data-driven solutions.

![img](/images/data%20sharing%20partner%20publishing%20diagram.png)

Through integration with Google Cloud IAM, you can set permissions on BigQuery objects to enable access by users inside or outside of organizations. In this lab, you will learn how to create datasets in BigQuery to share externally. You will be given three projects: the Data Sharing Partner project and two customer projects. You will create and share the dataset inside of the Data Sharing Partner project, and then test the sharing capabilities from the other two customer projects. </p>

## Objectives
<p> In this lab, you will:

- Grant permissions via IAM for data access
- Create a new dataset within an existing project
- Copying an existing table to newly created dataset
- Grant permission to the users to access a table
- Authorize and grant permissions to a dataset
- Verify dataset sharing capabilities for customer projects </p>

## Task 1. Grant permissions via IAM for data access
1. Open the Data Sharing Partner Project Console. Log in with the associated credentials.

2. From the Navigation Menu, go to IAM & Admin > IAM.

3. Click + GRANT ACCESS at the top to assign a role to principals who needs to access the data.

4. In the New principals field, enter the customer service account IDs:

- Customer 1 username
- Customer 2 username

5. In the Select a role field, select the BigQuery User role.

![img2](/images/add%20bigquery%20user%20role%20to%20service%20account.png)

## Task 2. Create a new dataset within an existing project
1. From the Navigation Menu, go to BigQuery > Studio.

2. In the Classic Explorer panel, select the project where you want to create the dataset. Expand the three dots Actions option and click Create dataset.

![create dataset](/images/create%20dataset.png)

3. For Dataset ID, enter demo_dataset.

4. For Location type choose Multi-region and select US (multiple regions in United States) from dropdown..

5. Click Create Dataset.

## Task 3. Copy an existing table to newly created dataset
For the purposes of this lab, you will use a public dataset that you will then copy into a table inside of your project.

1. Go to the Explorer tab at the top left, then click on + Add data.
The Add window opens.

2. Click Public Datasets under Additional sources.

3. In the search bar, type Google Trends.

4. Select the Google Trends dataset. Make sure it is not the international dataset.

5. Click View dataset. The dataset information page should show up.

![trends dataset info](/images/trends%20dataset%20info.png)

6. Click Copy.

7. For the Destination dataset, click in the box and search/select Data Sharing Partner Project ID.demo_dataset.

8. For Location select us (multiple regions in United States).

9. Click Copy.

A popup window asking to authorize the BigQuery Data Transfer Service should appear. Select the student account and click Allow.
enable data transfer service

## Task 4. Grant permission to the users to access the table
For the purposes of this lab, a dataset and table have been provided for you in BigQuery.

1. From the Navigation Menu, go to BigQuery > Studio.

2. Under your project, inside of demo_dataset, open the top_terms table.

![top-terms-table](/images/top-terms-table.png)

3. Click + Share > Manage permissions.

4. Click on Add Principal and add the two customer users:

- Customer 1 username
Customer 2 username- 
5. Select the BigQuery Data Viewer role.

![add bigquery data viewer principal](/images/add%20bigquery%20data%20viewer%20principal.png)

6. Click Save.

## Task 5. Authorize a dataset and grant permission to the users
1. Open the demo_dataset and click + Share > Authorize Datasets.

![authorize datasets](/images/authorize%20datasets.png)

2. Search and select the Dataset ID that needs to be authorized to share: Data Sharing Partner Project ID.demo_dataset.

![select dataset ID](/images/select%20dataset%20ID.png)

3. Click Add Authorization.

4. Click on + Share > Manage permissions > Add Principal and add the two customer users:

- Customer 1 username
- Customer 2 username
5. Select the BigQuery User role.

![add principals to shared dataset](/images/add%20principals%20to%20shared%20dataset.png)

6. Click Save.
Great! You have successfully shared the dataset and table with the two customer users.

## Task 6. Verify dataset sharing for customer projects
In this section, you will verify the datasets and tables were shared for each customer user.

### Verify dataset sharing for customer 1
1. Close the Data Sharing Partner Project Console and open the Customer Project 1 Console. Log in with the associated credentials.

2. From the Navigation Menu, go to BigQuery > Studio.

3. Run the following query, which selects all columns from the demo_dataset.top_terms table from the Data Sharing Partner project:
```text
SELECT * FROM `Project ID.demo_dataset.top_terms`
```
You should now see the results populated.

4. On the query toolbar, select Save > Save View.

5. Click in the Dataset field and select Create New Dataset.

- For the Dataset ID, type customer_1_dataset
- For Location type choose Multi-region and select US (multiple regions in United States) from dropdown.
6. Click Create Dataset.

7. In the Table field, type customer_1_table.

![save consumer 1 view](/images/save%20consumer%201%20view.png)

8. Click Save.

9. Refresh your window.

You should now be able to see the dataset and table, as well as query it.

### Verify dataset sharing for customer 2
1. Close the Customer Project 1 Console and open the Customer Project 2 Console. Log in with the associated credentials.

2. From the Navigation Menu, go to BigQuery > Studio.

3. Run the following query, which selects all columns from the demo_dataset.top_terms table from the Data Sharing Partner project:
```text
SELECT * FROM `Project ID.demo_dataset.top_terms`
```
You should now see the results populated.

4. On the query toolbar, select Save > Save View.

5. Click in the Dataset field and select Create New Dataset.

- For the Dataset ID, type customer_2_dataset
- For Location type choose Multi-region and select US (multiple regions in United States) from dropdown.
6. Click Create Dataset.

7. In the Table field, type customer_2_table.

![save customer 1 view](/images/save%20customer%201%20view.png)

8. Click Save.

9. Refresh your window.

You should now be able to see the dataset and table, as well as query it.

<p>Congratulations!
In this lab, you learned how to use BigQuery to publish datasets to share externally. You first granted permissions via IAM for data access, copied an existing table to a newly created dataset, then authorized a dataset and granted permissions to the users to access a table. Lastly, you verified the dataset and table were shared properly for both of the customer projects.</p>