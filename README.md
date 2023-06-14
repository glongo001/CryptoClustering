# CryptoClustering
I used my knowledge of unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

## Prepare the Data
1. I used pandas and hvplot to work with the crypto_market_data file, and visualize the results. I used Scikit-learn (sklearn) for unsupervised machine learning, I specifically used KMeans, PCA and StandardScaler.
2. I created a dataframe with the information from the csv file and created a plot to visualize the data I have. 

![alt text](https://github.com/glongo001/CryptoClustering/blob/main/market_data_plot.png)

3. I used StandardScaler to normalize the data from the csv file. Then, I created a dataframe with the coin name as the index.

## Find the Best Value for k Using the Original Scaled DataFrame
4. I used the elbow method to find the best value for k. I used KMeans in a for loop to compute every possible value for k.
5. I created a dataframe with the obtained k and inertia values and created an elbow plot to determine the best possible value for k.
    - The best possible value for k was 3. After this point the plot seems to level off significantly.

![alt text](https://github.com/glongo001/CryptoClustering/blob/main/elbowplot.png)

## Cluster Cryptocurrencies with K-means Using the Original Scaled Data
6. I initialized the KMeans module with 3 as the best value for k, I fit the model using the scaled data I obtained with StandardScaler, and predicted the market clusters.
7. I created a scatter plot with the price_change_percentage_24h as the x values and price_change_percentage_7d as the y valued. I colored the graph points by market cluster and used hover_cols to display the coin name when hovering over each datapoint.

![alt text](https://github.com/glongo001/CryptoClustering/blob/main/market_data_scaled_predictions.png)

## Optimize Clusters with Principal Component Analysis
8. I created a PCA model that reduced the features to three principal components.
9. I obtained the explained variance ratio. The array I obtained was array([0.47862164, 0.26608254, 0.1684978 ]). Therefore, the explained variance ratio for the three principal components is 91.3%.
10. I created a new dataframe with the PCA data and the coin names in the index.

## Find the Best Value for k Using the PCA Data
11. I used the elbow method to find the best value for k. I used KMeans in a for loop to compute every possible value for k. This time I used the PCA data for the elbow method.
12. I created a dataframe with the obtained k and inertia values and created an elbow plot to determine the best possible value for k with the PCA data.
    - The best possible value for k was 4. After this point the plot flattens significantly.

![alt text](https://github.com/glongo001/CryptoClustering/blob/main/elbowpca.png)

## Cluster Cryptocurrencies with K-means Using the PCA Data
13. I initialized the KMeans module with 4 as the best value for k, I fit the model using the PCA data, and predicted the market clusters.
14. I created a scatter plot with PC1 as the x values and PC2 as the y valued. I colored the graph points by market cluster and used hover_cols to display the coin name when hovering over each datapoint.

![alt text](https://github.com/glongo001/CryptoClustering/blob/main/market_data_pca_predictions.png)

## Visualize and Compare the Results
15. I created a composite plot of the original data elbow plot and the PCA data elbow plot.
16. I also created a composite plot of the original data market clusters and the PCA data market clusters.
