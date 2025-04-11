# Power BI


* **How would you define Power BI as an effective solution?**
  * Power BI is a strong business analytical tool that creates useful insights and reports by collating data from unrelated sources. 
  * This data can be extracted from any source like Microsoft Excel or hybrid data warehouses. we can create reports using the Excel BI toolkit and share them on-cloud with the co-workers.

* **What are the major components of Power BI?**
  * Power BI has 8 major components: 
    * **Power Query**: A data connection technology that enables users to discover, connect, combine, and refine data from various sources.
    * **Power Pivot**: A data modeling tool that allows users to create complex data models, establish relationships, and perform calculations for deeper data analysis.
    * **Power View**: A data visualization tool that enables users to create interactive charts, graphs, and maps for dynamic data exploration.
    * **Power Map**: A 3D data visualization tool for mapping, exploring, and interacting with geographic and temporal data within Excel.
    * **Power Q&A**: A natural language query tool that allows users to ask questions about their data in plain language and receive instant answers in the form of visualizations
    * **Power BI Desktop**: A Windows application for creating reports and visualizations by connecting to multiple data sources and building data models.
    * **Power BI Website/ Power BI Service / Power BI Online**: An online platform for sharing, collaborating on, and accessing reports and dashboards created in Power BI Desktop.
    * **Power BI Mobile Apps**: Mobile applications for iOS, Android, and Windows devices that allow users to access and interact with Power BI reports and dashboards on the go.

* **What are the various dataset refresh options available in Power BI?**
  * The various refresh options available in Power BI are: 
    * **Data Refresh**: The process of updating a dataset with the latest data from the connected data sources to ensure that reports and dashboards reflect the most current information.
    * **OneDrive Refresh**: Automatically updates the Power BI dataset and reports with changes made to Excel or Power BI Desktop files stored on OneDrive or SharePoint Online.
    * **Query Caches**: Caches query results to improve the performance of report visuals by reducing the need to repeatedly query the underlying data sources.
    * **Tile Refresh**: Updates dashboard tiles automatically every 15 minutes to reflect changes in the underlying dataset, ensuring that dashboard visuals remain current.
    * **Report Visuals**: Refreshes the visuals within a report to reflect the most recent data from the dataset, ensuring accurate and up-to-date information is displayed.

* **What are the different kinds of views in Power BI?**
  * The primary views are: 
    * **Report View**: The report view displays the tables in an interactive format to simplify data analysis. You can create n number of reports, provide visualizations, merge them, or apply any such functionality. 
    * **Data View**: Curating, exploring, and viewing data tables in the data set. Unlike, Power Query editor, with data view, you are looking at the data after it has been fed to the model. 
    * **Model View**: This view shows you all the tables along with their complex relationships. With this, you can break these complex models into simplified diagrams or set properties for them at once. 

* **What are the data sources Power BI can connect?**
  * The data source is the point from which the data has been retrieved. 
  * It can be files in various formats like .xlsx, .csv, .pbix, .xml, .txt etc, and databases like SQL database, SQL Data Warehouse, Spark on Azure HDInsight, or form content packets like Google Analytics, etc.

* **How do you set-up data import in Power BI?**
  * Key steps to follow when importing data in Power BI:
    * **Get Data**: Access the "Get Data" option on the Home tab in Power BI Desktop to connect to a wide range of data sources.
    * **Select Data source**: Choose the appropriate data source from the list. Power BI supports numerous data sources, including files, databases, Azure services, online services, and others.
    * **Connect and Load**: After selecting the data source, enter the necessary connection details (e.g., server name, database name, credentials). Then, choose whether to load the data directly or transform it first using Power Query.
    * **Transform Data**: Use Power Query Editor to clean, transform, and shape the data.
    * **Load Data into Power BI**: Once the data is prepared, load it into Power BI Desktop.

* **What will you do for data cleaning at the time of loading data in Power BI?**
  * Some common techniques for data cleaning in Power BI:
    * *Removing Duplicates*
    * *Handling Missing Values*
    * *Trimming and Cleaning Text*
    * *Filtering Data*
    * *Changing Data Types*
    * *Splitting and Merging Columns* 
    * *Removing Unnecessary Columns*

* **How do you establish relationships between tables in Power BI?** 
  * Relationships between tables in Power BI can be established in the Model view. 
  * Users can drag and drop fields from one table to another to create relationships. 
  * Power BI supports different types of relationships, including one-to-one, one-to-many, and many-to-many, which help in creating a cohesive data model.

* **What is Data Analysis Expression (DAX)?**
  * **Data Analysis Expression (DAX)** is a library of formulas used for calculations and data analysis. 
  * This library comprises functions, constants, and operators to perform calculations and give results. 
  * DAX is a functional language containing conditional statements, nested functions, value references, and much more. 
  * The formulas are either numeric (integers, decimals, etc.) or non-numeric (string, binary).

* **What is an aggregation in DAX, and how is it used in Power BI?**
  * Aggregation in DAX refers to the process of summarizing data by applying functions like SUM, AVERAGE, COUNT, MIN, and MAX to groups of data. 
  * Aggregations are used to create summary metrics such as total sales or average revenue, which are crucial for reporting and analysis.

* **What does the CALCULATE function do in DAX?**
  * The CALCULATE function in DAX evaluates an expression in a modified filter context. 
  * It allows users to apply filters or modify existing filters on a calculation to generate more specific results. It is a powerful function for creating complex measures.

* **What are some best practices for designing effective Power BI reports?**
  * Best practices include:
    * Use clear and consistent visualizations that effectively communicate data insights.
    * Organize data into logical sections and use headings for clarity.
    * Apply filters and slicers to allow users to interact with the data.
    * Ensure that visualizations are not overloaded with information and maintain a clean design.
    * Use tooltips and data labels to provide additional context.

* **What are custom visuals in Power BI?**
  * Custom visuals are specialized visualizations that go beyond the built-in options provided by Power BI. 
  * They can be added from the Power BI Visuals Marketplace. 
  * To add a custom visual, go to the **"Visualizations"** pane in Power BI Desktop, click on the **ellipsis (three dots)**, and choose **"Get more visuals"** to browse and import custom visuals from the marketplace.

* **How do you use slicers in Power BI reports?**
  * Slicers are used to create interactive filters that allow users to select values and filter data across multiple visualizations. 
  * To add a slicer, select the **"Slicer"** visual from the **"Visualizations"** pane, **drag a field** into the slicer, and customize its settings to provide users with filtering options.

* **What are the types of filters that can be created in Power BI?**
  * There are standard 4 types of filters:
    * **Visual Filter**: applies to a single visual on a report page.
    * **Page Filter**: applies to all the visuals on the report page.
    * **Report Filter**: applies to all pages in the report.
    * **Drillthrough Filter**: allows users to explore detailed data by drilling through to a new report page that provides more in-depth information related to a specific data point or selection. 

* **What is the difference between report-level filters and page-level filters in Power BI?**
  * Report-level filters apply to all pages of a report, ensuring consistency across the entire report. 
  * Page-level filters apply to all the visuals of the current page of the report, allowing different pages to display different subsets of data.

* **What are some use cases for conditional formatting in Power BI?**
  * Conditional formatting can be used to highlight important data trends, such as:
    * Highlighting cells with values above or below a certain threshold.
    * Applying color gradients to show variations in data values.
    * Using data bars or color scales to visually represent data distribution and intensity.
    * Indicating performance metrics with color-coded visual cues for quick assessment.

* **What is the "Analyze" feature in Power BI?** 
  * The **Analyze** feature in Power BI provides tools for in-depth data exploration and analysis directly from your reports. 
  * It includes options like **“Explain the Increase”, “Explain the Decrease”, and “Explain the Difference”** which help users understand data trends, identify causes of changes, and perform advanced analysis.

* **How can you detect outliers in Power BI?**
  * Outliers can be detected using various visualization techniques such as scatter plots or box plots. 
  * In Power BI, you can use the "Analytics" pane within visuals to add reference lines, trendlines, or error bars to highlight unusual data points. 
  * Additionally, custom DAX measures can be created to identify and flag outliers based on statistical criteria.

* **What is a Power BI dashboard, and how do you create one?**
  * A Power BI dashboard is a single-page, interactive view that consolidates key metrics and visualizations from multiple reports into one interface. 
  * To create a dashboard, **pin visualizations from reports** to a **new or existing dashboard** in the Power BI Service. 
  * Arrange and resize the tiles to provide a cohesive and informative overview.

* **What are data alerts in Power BI, and how do you set them up?**
  * Data alerts are notifications triggered when data in a dashboard reaches certain thresholds or conditions. 
  * To set up data alerts, go to the **Power BI Service**, select a **tile in a dashboard**, and click on the **ellipsis (three dots) > "Manage alerts."** 
  * Define the **alert conditions**, such as values exceeding a threshold, and configure how and when you receive notifications.