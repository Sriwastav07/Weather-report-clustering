🌦️ Global Weather Pattern Clustering Dashboard
This project builds an interactive Power BI dashboard with machine learning and EDA to analyze global weather patterns. It clusters weather conditions using K-Means and visualizes seasonal and spatial trends in temperature, humidity, pressure, and precipitation.

📁 Dataset
File: GlobalWeatherRepository.csv

Columns Used:

Date, Region, Country, City

Temperature, Humidity, Pressure (inHg), Precipitation

Latitude, Longitude

Derived Fields:

Cluster (from K-Means)

ClusterLabel (Cluster 1, 2…)

Anomaly (Yes/No based on pressure)

🔍 Exploratory Data Analysis (EDA)
EDA was performed using Python (Pandas, Seaborn, Matplotlib) to understand trends and distributions before clustering:

✅ Key Insights from EDA:
Correlation Heatmap showed strong correlation between humidity and precipitation.

Boxplots helped detect outliers in temperature and pressure.

Distribution plots confirmed pressure values were centered around 29.9 inHg.

Missing Values were minimal and handled via row drops or mean imputation.

📊 EDA Techniques Used:
Histograms, Boxplots, Pairplots

.describe() and .info() for summary stats

sns.heatmap() for correlation matrix

Null value checks: df.isnull().sum()

💡 Objectives
Cluster weather profiles using unsupervised ML

Detect anomalies in pressure values

Visualize global and temporal patterns interactively

Provide data-driven storytelling through BI visuals

🧰 Tools Used
Tool	Purpose
Power BI	Visualization and dashboard design
Python (Pandas, Seaborn, Sklearn)	EDA and clustering logic
DAX	Custom KPIs, anomaly flags

🧠 ML + DAX Logic
K-Means Clustering:

python
Copy
Edit
scaler = StandardScaler()
scaled = scaler.fit_transform(df[['Temperature', 'Humidity', 'Pressure', 'Precipitation']])
kmeans = KMeans(n_clusters=4)
df['Cluster'] = kmeans.fit_predict(scaled)
df['ClusterLabel'] = "Cluster " + (df['Cluster'] + 1).astype(str)
Anomaly Detection (Pressure in inHg):

DAX
Copy
Edit
Anomaly = IF([Pressure] < 28.5 || [Pressure] > 30.7, "Yes", "No")
📊 Dashboard Features
Visual	Description
🌍 Map	Shows weather clusters across regions
📊 Bar Chart	Dynamic Y-axis: Compare temp/humidity/pressure by cluster
📈 Line Chart	Tracks weather metrics over time
⚠️ Anomaly KPIs	Cards and scatter plot for anomalies in pressure
🎛️ Slicers	Filters for Date, Region, Cluster, Metric

🚀 How to Use
Open WeatherDashboard.pbix in Power BI Desktop

Explore cluster profiles, patterns, and anomalies

Use slicers to filter by region, date, or weather feature

📌 Use Cases
Climate pattern monitoring

Regional weather zone discovery

Pressure anomaly tracking

Combining ML + BI for insights
