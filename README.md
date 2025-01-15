# BIG-DATA-ANALYSIS-1


Name:Z.Zulfa Fathima

Company:CODTECH IT SOLUTIONS

ID:CT08DJE

Domain:Data Analytics

Duration:Dec 2024 to Jan 2025



Libraries Used

PySpark:

Used for distributed data processing.
SparkSession is utilized to create a Spark application and process the data efficiently.
PySpark SQL functions enable querying and grouping operations on data.
Provides methods to load and manipulate large datasets.

findspark:

Ensures that PySpark is easily located and used in the system's Python environment.

pandas:

Used for converting PySpark DataFrames to pandas DataFrames for visualization purposes.
Facilitates easier manipulation and plotting of data.

matplotlib:

Used for creating visualizations such as bar charts, line plots, and horizontal bar charts.
Helps in visualizing trends and insights from the IPL dataset.

seaborn:

Though imported, it is not explicitly used in this code but can complement matplotlib for enhanced visualizations.

Project Objectives

Data Exploration:

Load and explore IPL match data from a CSV file.
Display and understand the schema, structure, and basic statistics of the dataset.
Seasonal Analysis:

Analyze the number of matches played each IPL season and visualize the trend.
Team Performance Analysis:

Identify the number of matches won by each team across seasons.
Study the seasonal performance trends of teams over the years.
Player Performance Analysis:

Determine the top players with the highest "Player of the Match" awards.
Visualize and highlight the contribution of these players.
Venue Insights:

Analyze venues with the highest number of matches hosted.
Toss Decision Analysis:

Explore how toss decisions (bat or field) influenced the outcome of matches for teams.
Visualization:

Use pandas and matplotlib to generate interactive and informative charts for insights.
Code Explanation


Setup and Library Installation:

The required libraries (pyspark, findspark, pandas, matplotlib, and seaborn) are installed and imported.
A SparkSession is created to initialize the Spark application for data processing.

Data Loading:

IPL data is loaded into a PySpark DataFrame using the read.csv() method with headers and inferred schema.
The data is displayed and its schema is printed for understanding its structure.
Data Analysis Using PySpark:

Grouping and ordering operations (groupBy, count, orderBy) are used to analyze seasonal trends, team performance, and player contributions.
SQL queries (createOrReplaceTempView) are used for complex aggregations and queries on the dataset.
Visualization:

PySpark DataFrames are converted to pandas DataFrames for easy plotting.
Bar and horizontal bar charts are created to visualize:
Matches played per season.
Top players with the most "Player of the Match" awards.
Line plots depict team performance trends over the years.
Toss Decision Impact:

The influence of toss decisions on match outcomes is analyzed using a grouped aggregation.



PROGRAM CODE:


!pip install pyspark


!pip install findspark


import pyspark




from pyspark.sql import SparkSession




import findspark




findspark.init()



spark = SparkSession.builder.appName("IPL_Analysis").getOrCreate()



!pip install pandas
!pip install matplotlib seaborn
ipl_data_path = "/content/matches.csv"  # Update with your file path
ipl_df = spark.read.csv(ipl_data_path, header=True, inferSchema=True)
ipl_df.show()
ipl_df.printSchema()
ipl_df.show(5)
ipl_df.printSchema()
ipl_df.describe().show()
ipl_df.groupBy("season").count().orderBy("season").show()
ipl_df.groupBy("winner").count().orderBy("count", ascending=False).show()
ipl_df.groupBy("player_of_match").count().orderBy("count", ascending=False).show(10)
ipl_df.groupBy("player_of_match").count().orderBy("count", ascending=False).show(10)
ipl_df.createOrReplaceTempView("ipl_table")
spark.sql("""
    SELECT winner, COUNT(*) AS wins
    FROM ipl_table
    WHERE winner IS NOT NULL
    GROUP BY winner
    ORDER BY wins DESC
""").show()
spark.sql("""
    SELECT venue, COUNT(*) AS matches
    FROM ipl_table
    GROUP BY venue
    ORDER BY matches DESC
""").show()
import pandas as pd
import matplotlib.pyplot as plt

season_data = ipl_df.groupBy("season").count().toPandas()
season_data.plot(kind="bar", x="season", y="count", legend=False)
plt.title("Matches Played Each Season")
plt.xlabel("Season")
plt.ylabel("Number of Matches")
plt.show()
player_data = ipl_df.groupBy("player_of_match").count().orderBy("count", ascending=False).limit(10).toPandas()
player_data.plot(kind="barh", x="player_of_match", y="count", legend=False)
plt.title("Top 10 Player of the Match Awards")
plt.xlabel("Number of Awards")
plt.ylabel("Player")
plt.show()
performance_df = ipl_df.groupBy("season", "winner").count()
performance_df.orderBy("season").show()
import matplotlib.pyplot as plt

# Assuming 'performance_df' is already defined as in your previous code
toss_impact_df = ipl_df.groupBy("toss_decision", "winner").count()
toss_impact_df.show()

performance_pandas = performance_df.toPandas()

# Plotting the time series data
plt.figure(figsize=(12, 6))
for winner in performance_pandas['winner'].unique():
    winner_data = performance_pandas[performance_pandas['winner'] == winner]
    plt.plot(winner_data['season'], winner_data['count'], label=winner, marker='o')

plt.xlabel('Season')
plt.ylabel('Number of Wins')
plt.title('Team Performance Over Time')
plt.xticks(performance_pandas['season'].unique())  # Ensure all seasons are shown on x-axis
plt.legend(loc="center left")
plt.grid(True)
plt.show()


OUTPUT:

![image](https://github.com/user-attachments/assets/51991f45-eec0-4629-acda-cec59650f023)

![image](https://github.com/user-attachments/assets/c337c347-da91-4834-853c-bb8d98e35c47)

![image](https://github.com/user-attachments/assets/62c7d651-d5fd-4c10-ac7b-c630b755379a)
