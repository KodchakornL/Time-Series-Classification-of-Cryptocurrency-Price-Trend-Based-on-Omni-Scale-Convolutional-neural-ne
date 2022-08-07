# Time Series Classification of Cryptocurrency Price Trend Based on Omni-Scale Convolutional neural network
Independence study in university Topic : Time Series Classification of Cryptocurrency Price Trend Based on Omni Scale-Convolutional neural networks 

## Introduction  
Digital currency Cryptocurrency has been around since 2009, when a developer known as Satoshi Nakamoto [1] developed a blockchain system that is not regulated by governments and central banks. Cryptocurrency plays a role as a financial intermediary. Anonymous transactions using transaction security encryption. And new units are created under the supervision of every computer network user or stored node. The data is shared and recorded on the blockchain. Today, exchanges using these 'coins' are on the rise, despite initial suspicions of using cryptocurrencies for trading as a source of illegal money laundering, sparking resistance from the government. But there is continuous development such as Smart contracts, Decentralized finance, Non-Fungible Token (NFT), Property Technology, etc.

Data analysis for investment planning to keep up with the high volatility market situation is essential. Therefore, using data to analyze cryptocurrency price trends to make investment decisions requires a large amount of decision-making information in order to make accurate predictions or forecasts that affect risk management. Risk can be done better. To analyze the trend of rising, falling, and static indices of the cryptocurrency market is based on very complex data. amount of purchase demand According to Alexandrov et al. [2], the data for cryptocurrency price analysis is a time-series type of data that is constantly flowing in real-time. These time series data are related to the time of each currency's price index. Therefore, it is an important issue for investors to analyze this massive data on their own. This causes inaccuracies and delays in trading in the online market.

This study analyzes the time-series classification of cryptocurrency price trends. Wensi Tang et al. [3] compared the performance with the CNN time-series deep learning model. -based models developed before Deep learning performance depends on the selection of hyperparameters such as the kernel size, pooling size, and the shrink ratio of the Omni-scale (OS) block data. 1.No need to adjust tune feature extraction scales 2. In general, better performance can be achieved OS block consisting of 2.1 OS layer that can be automatically configured with kernel size list by nesting OS layer 2.2 open field (RF: receptive field) of the OS block can cover the total length of the input. With fewer model parameters and less memory usage than CNN-based models, it also demonstrates a more scalable and efficient model. They can be created by stacking or ensembling multiple OS layers, or provide the rest of the connections suitable for use in time-series cryptocurrency trend analysis. Where cryptocurrencies are multi-currency, multi-currency trend analysis requires selecting the appropriate hyper-parameters for each data for its performance. while creating an OS block without selecting a hyperparameter Can be set up only once, can be used in different tasks.

## Research Methodology
This study was conducted to analyze cryptocurrency data. Its objective is to find the trend of up or down and fixed cryptocurrency prices by using convolutional neural network (OS-CNN) all-size integration as the main model. R&D based on Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz 1.99 GHz GPU: Tesla K80, T4 and P100-PCIE-16GB. Developed using Python  
  
**1.Data sources**  
Take the digital currency time series data from the website. www.cryptodatadownload.com The data is frequency in minutes, in terms of individual cryptocurrencies per US dollar. Volume data for the past 5 years, from January 1, 2017 at 00.00 to March 21, 2022 at 11.44 AM, with a data frequency of 1 minute, as shown in Figure 2, showing BTC data. The horizontal axis is time. and the vertical axis is the price of the cryptocurrency. Research scope, the researcher uses cryptocurrencies: 1.BTC 2.ETH 3.XRP 4.LTC 5.BNB 6.ADA 7.DOT 8.LINK shows the OHLC price time series (open price, highest price, lowest price, closing price).  
  
<img src="https://github.com/KodchakornL/Time-Series-Classification-of-Cryptocurrency-Price-Trend-Based-on-Omni-Scale-CNN/blob/main/Slide_ppt/Picture1.png" width="350" height="300" />  
  
  
**2.Data preparation (Preprocessing of Data)**
  
2.1 Input takes the closing price time series data of the cryptocurrency. Each input sequence has length j = 32, since the closing price time series of cryptocurrencies is not fixed. therefore separate the sequence from the data set first. and then apply Min-max normalization. Equation 1 xti is the data iththe closing price of
Cryptocurrency in the input sequence of the tth time point as in Equation 1.

where operations from min and max values ​​are applied to the xti components for all i = 1, ... . in the interval [t − 31, . . . , t].

2.2 Target
Clean data (Data Cleaning) that is abnormal by using an isolation forest from the data set to format the data in an appropriate format. by taking the closing price information of cryptocurrencies
The target is displayed as one hot vector, if it is 1 it is trending up and if it is 0 it is trending down or stable. The model is trained so that the cross-entropy loss function (minimize the cross-entropy loss function) is represented by mt. Average price over window sized movement T = 30 min. before t, then target labeling follows equation 2.

**3.Data preparation**
The data preparation method was used Method 1. Separate training data 70%, check data 15%, test data 15%. Method 2. Walk-forward optimization method as shown in Figure 2.

From Takuya Shintate, Lukáš Pichl [9] contains l , each span of width that will move continuously. Set equal to 10,080 minutes. Within this range, k is Window size equals 30, where t is the current time. Using the data points in the Train window, represented by a green box and a Test window with a red box, one by one. Both windows will move to the right. and then start training again until the end of the time series window. By separating 15% of the previous test data and using the walk-forward method above with 70% of the practice data and 15% of the check data.
  
**4.OS-CNN model
In a time-series classification of cryptocurrency price trends using omni-scales with a CNN model based on a study by Wensi Tang et al. [3].

From Figure 5, the OS layer retrieves data with Convolutional kernel sizes. Generally, any kernel size element designed to achieve the entire neural net is the OS layer. The kernel size configuration used is a list of prime numbers from 1 to M. The value of M is the smallest prime. That allows the OS block shown in Figure 4 to cover RF from 1 to [N/2], where N is the length of the input data. This unique number list configuration allows the OS block to fetch data of any particular size based on the Goldbach Conjecture (predicted). Can consist of two primes, if there is a kernel of all prime sizes in the first two layers, the RF of the first two layers can be any positive even number (odd -1 for the stride layer. The model requires a kernel size 1 and 2 on the third floor. Since all integers can be generated by adding 1 or 2 to all even numbers, configuring the kernel with a specific sequence
In order to avoid scaling of pooling size tuning, the GAP (global average pooling) layer is used before the FC (Fully connected) layer and no other pooling layers to reduce the length over time dimensions. The use of GAP is averaged. The value in the field is a single value, which will cause the location data to be lost. To solve this problem, a larger kernel was used to take the relative position of the two features as a new feature.

Modeling with an OS block The OS-CNN model consists of 1. OS block with one GAP layer 2. FC layer as Classification module. The architecture is flexible and can be expanded to more layers. Close 8 cryptocurrencies, single variable, data frequency is 1 minute, window is 30, number of classes is 2, 0 and 1, if 0 is downtrend and stable, if 1 is uptrend, use epoch. equal to 500, the size of the receptive field is defined as the length of the input data window divided by 4 equals 7 by the model. 1. The total number of variables is equal to [1024, 229376]. The kernels structure of the layer is obtained (number of input channels, number of output channels, kernel size). The kernels of the three layers of the digital currency are as follows: the kernels of the layer are [( 1, 56, 1), (1, 56, 2), (1, 56, 3), (1, 56, 5), (1, 56, 7)] kernels of layer 2 are equal to [(280, 45, 1), (280, 45, 2), (280, 45, 3), (280, 45, 5), (280, 45, 7)] Kernels of layer 3 are equal to [(225, 280, 1), ( 225, 280, 2)]

## Research results
For model comparison, the investigator did not use hyperparameter adjustments in the validation set or test set for fair comparison. The researchers used the same hyperparameters as the basic 1D-CNN model FCN, unified for the entire dataset. In order to make the OS block model size the same as the FCN (Fully convolutional network) convolution layer model size, the OS-CNN experiment found no overfitting of all coins from the sample of both data preparation methods 1. Separate training data. 70 % Inspection data 15 % Test data 15% Method 2. Walk-forward optimization method is used as shown in Figure 6.

Of the two methods, an epoch of 500 was used according to research by Wensi Tang et al. [3] Fig. 6 increased accuracy and reduced loss compared to other TSC deep learning models on the dataset. Single variable data (Univariate dataset baselines) are 1. MACNN 2. INCEPTIONTIME 3. RESNET 4. ROCKET 5. FCN 6. FCN sets Receptive field to 16 (represented by FCN(16)) 7. FCN sets Receptive field to 50. (Represented by FCN(50)) To evaluate the time series model using the Critical difference diagram Wilcoxon signed rank test diagram with Holm's correction of Holm's alpha (5%). The resulting classifier differences are rounded to eight decimal places. (And if all predictions of the test set are correct The result will be 1)

From Figure 7, the critical difference diagram by data separation method shows that OS-CNN is the 3rd efficient after ROCKET and FCN (50), and the Walk forward method shows that OS-CNN is the fifth efficient after FCN (16), InceptionTime, , FCN (50), ROCKET

Figure 8 compares the accuracy of the 8 crypto currencies OS-CNN model with the FCN(16), InceptionTime, ROCKET, FCN(50) models in the Critical difference diagram that ranks higher than OS-. Model 1 CNN was FCN (16). From Method 1, the extraction showed that OS-CNN was better than 1 dataset, while Method 2 Walk forward showed that FCN (16) was better than Model 3. is InceptionTime. From Method 1, data extraction found that InceptionTime was better than 1 dataset, while Method 2 Walk forward found that InceptionTime was better than Method 3, ROCKET. Based on Method 1, extracting data, ROCKET was better than Method 2, whereas Method 2 Walk forward. It was found that ROCKET was better than 6 data sets. Model 4 was FCN (50). From Method 1, data extraction showed that FCN (50) was better than 4 data sets, while Method 2, Walk forward showed that FCN (50) was good. More than 5 data sets

Table 1 shows the Wilcoxon signed rank test with Holm's alpha (5%) Pairwise counts of wins to test the accuracy of model differences.

From Table 2, the accuracy f1-score precision recall roc auc shows that the model performed very well in some currencies: XRP, LTC, DOT, LINK.

## Suggestions
The OS-block can be applied to other TSC models such as the OS-CNN ensemble, for example, and if you add Open Price, Max Price, Min Price, you can add dimensions to other multivariate TSC model analysis.

## Conclusion
In overall comparison, the walk forward data preparation method performed better than the data preparation method. Normal data extraction that extracts train, validation, test data. Experiments show that OS-CNN can perform better without tuning of feature extraction scales based on OS block and OS layer OS-CNN. Based on accuracy f1-score precision recall roc auc, in some cryptocurrencies XRP, LTC, DOT, LINK, when evaluating each replica accuracy using a Critical difference diagram, the OS-CNN model is in 3rd and 5th divisions. 1st and 2nd place were the FCN (50) vs ROCKET models. In the Wilcoxon signed rank test, the FCN (50) model won every model in all of the datasets' measurements.


