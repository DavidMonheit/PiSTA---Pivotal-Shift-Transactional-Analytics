<h1>PiSTA - Pivotal Shift Transactional Analytics</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
Pivotal Shift Transactional Analytics (PiSTA) is a data-driven decision-making platform I designed specifically for the Israeli Defense Forces' Home Front Command (Pikud HaOref) and is currently being used. This innovative tool provides the ability of identifying and analyzing outlier transactional behaviors in urban areas, particularly focusing on changes around key dates and anomalies in spending habits. PiSTA employs advanced algorithms to segregate transaction data into distinct periods before and after specific events, thereby providing deeper insights into transactional dynamics and notable changes in spending patterns. It excels in pinpointing cities within vast datasets that display unusual transactional behaviors, which is crucial for the needs of the IDF. PiSTA's versatility is enhanced by its adaptable parameters, including analysis resolution (city, regional council, etc.), spending categories (pharmaceuticals, supermarkets, clothing, etc.), and various adjustable algorithm sensitivity parameters. This tool is distinguished by its ability to uncover hidden patterns and anomalies in complex datasets, making it an essential component for data-driven strategies in military contexts.

<h2>Key Features of PiSTA</h2>
<ul>
<li><b>Data Processing and Analysis:</b> PiSTA processes transaction data with a focus on changes occurring before and after a pivotal date, including transaction filtering, data normalization, and pivot table creation for detailed analysis.</li>
<li><b>Dimensionality Reduction and Clustering:</b> Utilizing Isomap for dimensionality reduction and DBSCAN for clustering, PiSTA identifies complex transactional patterns and anomalies.</li>
<li><b>Outlier Detection and Analysis:</b> Expert in detecting outliers, PiSTA is crucial for the Home Front Command to identify unusual activities within large datasets.</li>
<li><b>Visualization Capabilities:</b> Features robust functions for visualizing complex data, including plots of reduced data, clusters, and time series analysis of outliers.</li>
<li><b>Customization and Flexibility:</b> Adjustable parameters like pivot date, threshold percent, and transaction categories allow for tailored analysis based on IDF's specific needs.</li>
<li><b>Data Integrity and Management:</b> Accounts for missing data, ensuring reliable analysis and maintaining data integrity.</li>
</ul>

<h2>Languages and Utilities Used</h2>
<ul>
<li><b>Python:</b> The primary programming language for scripting and analysis.</li>
<li><b>numpy:</b> Utilized for numerical computations.</li>
<li><b>pandas:</b> Employed for data manipulation and analysis.</li>
<li><b>matplotlib:</b> Used for plotting and visualizing data.</li>
<li><b>math:</b> For mathematical functions like ceiling calculations.</li>
<li><b>os:</b> For operating system interactions, such as file path handling.</li>
<li><b>sklearn:</b> A machine learning library used for clustering, nearest neighbors, and dimensionality reduction.</li>
</ul>
<h2>Environments Used</h2>
<ul>
<li><b>Jupyter Environment:</b> The code is tailored for execution in a Jupyter Notebook environment.</li>
<li><b>Synapse System:</b> Intended for eventual deployment and running on the Synapse system, emphasizing data processing and visualization capabilities.</li>
</ul>
<h2>Algorithms Used</h2>
<ul>
<li><b>Pearson Distance Matrix Calculation:</b> Computes a distance matrix based on Pearson correlation coefficients, laying the foundation for understanding data relationships and distances.</li>
<li><b>Isomap (Isometric Mapping):</b> Reduces the dimensionality of the dataset while preserving geodesic distances, simplifying the data structure for further analysis.</li>
<li><b>DBSCAN (Density-Based Spatial Clustering of Applications with Noise):</b> Clusters the data based on density, effectively grouping closely packed points and identifying outliers in low-density regions.</li>
<li><b>Nearest Neighbors (Using NearestNeighbors from sklearn.neighbors):</b> Identifies the nearest points in the dataset to a specific point or set of points, useful for detailed analysis within clusters.</li>
</ul>

<h2>Parameters</h2>
<ul>
    <li><b>Pivot Date:</b> A critical date used to segment the transaction data for comparative analysis. Transactions are analyzed separately for periods before and after this date to understand changes over time as well as filter them.</li>
    <li><b>Threshold Percent for Missing Data:</b> A parameter defining the acceptable percentage of missing data in city transactions. Cities exceeding this threshold are excluded from the analysis to maintain data integrity.</li>
    <li><b>Transaction Category:</b> Focuses the analysis on a specific category of transactions, allowing for more targeted insights into spending patterns within that category.</li>
    <li><b>Clustering Sensitivity (EPS Value for DBSCAN):</b> Determines the sensitivity of the DBSCAN clustering algorithm. A crucial parameter for identifying clusters with varying densities in the data.</li>
    <li><b>Minimum Samples for DBSCAN:</b> Specifies the minimum number of samples (or total weight) in a neighborhood for a point to be considered a core point. This parameter is integral to the DBSCAN algorithm's ability to form clusters.</li>
    <li><b>Number of Components for Isomap:</b> Dictates the number of dimensions to which the data is reduced, influencing the granularity of the dimensionality reduction process.</li>
    <li><b>Number of Neighbors in Nearest Neighbors Analysis:</b> Sets the number of neighbors to consider in the nearest neighbors analysis, impacting the identification of closely related observations within the data.</li>
</ul>

<h2>Research Conducted</h2>
<ul>
    <li><b>Calculating City Distance Based on Time Series:</b> Thorough research was conducted to effectively calculate the distance matrix using various methods:
        <ul>
            <li><b>Euclidean Distance:</b> Found inadequate due to its focus on absolute differences in spending levels rather than trends. In cases where cities had proportional but different spending levels, Euclidean distance erroneously suggested high dissimilarity.</li>
            <li><b>Dynamic Time Warping (DTW):</b> An improvement but still not ideal. Although better at aligning time series with varying lengths, DTW couldn't adequately capture the similarity in spending trends when absolute values differed significantly.</li>
            <li><b>Cosine Similarity:</b> Provided better insights by focusing on the direction of spending trends, but still lacked in capturing the nuanced similarities in spending behavior.</li>
            <li><b>Pearson Correlation:</b> The final choice for its focus on the correlation of spending trends, making it highly suitable for this analysis.</li>
        </ul>
    </li>
    <li><b>Dimensionality Reduction:</b> Experimentation with several techniques to identify the most effective.
        <ul>
            <li><b>Principal Component Analysis (PCA):</b> Not optimal due to its linear nature, which could not capture the complex, nonlinear relationships in the transaction data.</li>
            <li><b>Multidimensional Scaling (MDS):</b> Although it considers distances, MDS was less effective in preserving the local neighborhoods of data points, crucial for transaction data analysis.</li>
            <li><b>Isomap:</b> Chosen as it effectively maintained geodesic distances in reduced dimensions, crucial for analyzing the nonlinear and complex structure of the transaction data.</li>
        </ul>
    </li>
    <li><b>Clustering Methods:</b> A variety of techniques were tested to find the most suitable one.
        <ul>
            <li><b>Hierarchical Clustering (Complete Linkage):</b> Found ineffective due to its tendency to be influenced by outliers and not suitably capturing the intrinsic data structure of city transactions.</li>
            <li><b>K-Means:</b> Not chosen due to its limitations in handling the non-spherical shapes and varying densities of clusters typical in transaction data.</li>
            <li><b>DBSCAN:</b> Selected for its proficiency in identifying clusters of arbitrary shapes and densities, which is essential in the context of transaction data.</li>
        </ul>
    </li>
 
   <li><b>Silhouette Method:</b> Utilized to optimize the clustering process. This method assesses the quality of clusters formed by the algorithms, guiding adjustments to parameters like the number of clusters or the distance threshold in DBSCAN.</li>
   <li><b>Optuna:</b> Employed for hyperparameter optimization. Optuna helps in fine-tuning various parameters, enhancing the performance and accuracy of algorithms like DBSCAN and Isomap.</li>
</ul>
<h2>Program walk-through:</h2>
<p align="center">
A snippet of the the dataset: <br/>
<img src="https://i.imgur.com/J2zErNc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/qAxm70G.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
A snippet if the distance matrix of dimenstion N*N calculated by Pearson timeseries distance algorithm: <br/>
<img src="https://i.imgur.com/WA5v2ox.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The Plot after dimension reduction to 2D using ISOmap reduction algorithm:  <br/>
<img src="https://i.imgur.com/Sm8CoDM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
An enlarged view of a dense area of cities, indicating strong spending pattern simmilarity:  <br/>
<img src="https://i.imgur.com/wDHsi36.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The outliers based on the 2d scatter resulting from the DBscan Cluster algorithm:  <br/>
<img src="https://i.imgur.com/xBKEr7p.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
A zoomed in view showing אשכול and מטה אשר are outliers:  <br/>
<img src="https://i.imgur.com/AoYnmLP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
Outliers and their corresponding k closest cities (cities comparable to the outlier city indicating where the outliers should have been):  <br/>
<img src="https://i.imgur.com/Z8brUdM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
After finding all outliers and their KNN's, each outlier's timeseries is compared to its neighbors for further examination. Here's some examples:  <br/>
<img src="https://i.imgur.com/p39B672.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br/>
<img src="https://i.imgur.com/RVDPzs9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <br/>
 A list of the outliers found and their KNN's:  <br/>
<img src="https://i.imgur.com/t2VegPT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
