# BIG-DATA-ANALYSIS-1


Name:Z.Zulfa Fathima

Company:CODTECH IT SOLUTIONS

ID:CT08DJE

Domain:Data Analytics

Duration:Dec 2024 to Jan 2025



## Libraries Used

# PySpark:

Used for distributed data processing.
SparkSession is utilized to create a Spark application and process the data efficiently.
PySpark SQL functions enable querying and grouping operations on data.
Provides methods to load and manipulate large datasets.

# findspark:

Ensures that PySpark is easily located and used in the system's Python environment.

# pandas:

Used for converting PySpark DataFrames to pandas DataFrames for visualization purposes.
Facilitates easier manipulation and plotting of data.

# matplotlib:

Used for creating visualizations such as bar charts, line plots, and horizontal bar charts.
Helps in visualizing trends and insights from the IPL dataset.

# seaborn:

Though imported, it is not explicitly used in this code but can complement matplotlib for enhanced visualizations.

# Project Objectives

# Data Exploration:

Load and explore IPL match data from a CSV file.
Display and understand the schema, structure, and basic statistics of the dataset.
# Seasonal Analysis:

Analyze the number of matches played each IPL season and visualize the trend.
# Team Performance Analysis:

Identify the number of matches won by each team across seasons.
Study the seasonal performance trends of teams over the years.
# Player Performance Analysis:

Determine the top players with the highest "Player of the Match" awards.
Visualize and highlight the contribution of these players.
# Venue Insights:

Analyze venues with the highest number of matches hosted.
# Toss Decision Analysis:

Explore how toss decisions (bat or field) influenced the outcome of matches for teams.
# Visualization:

Use pandas and matplotlib to generate interactive and informative charts for insights.
# Code Explanation


# Setup and Library Installation:

The required libraries (pyspark, findspark, pandas, matplotlib, and seaborn) are installed and imported.
A SparkSession is created to initialize the Spark application for data processing.

# Data Loading:

IPL data is loaded into a PySpark DataFrame using the read.csv() method with headers and inferred schema.
The data is displayed and its schema is printed for understanding its structure.
# Data Analysis Using PySpark:

Grouping and ordering operations (groupBy, count, orderBy) are used to analyze seasonal trends, team performance, and player contributions.
SQL queries (createOrReplaceTempView) are used for complex aggregations and queries on the dataset.
# Visualization:

PySpark DataFrames are converted to pandas DataFrames for easy plotting.
Bar and horizontal bar charts are created to visualize:
Matches played per season.
Top players with the most "Player of the Match" awards.
Line plots depict team performance trends over the years.
# Toss Decision Impact:

The influence of toss decisions on match outcomes is analyzed using a grouped aggregation.



# OUTPUT:

![image](https://github.com/user-attachments/assets/51991f45-eec0-4629-acda-cec59650f023)

![image](https://github.com/user-attachments/assets/c337c347-da91-4834-853c-bb8d98e35c47)

![image](https://github.com/user-attachments/assets/62c7d651-d5fd-4c10-ac7b-c630b755379a)
