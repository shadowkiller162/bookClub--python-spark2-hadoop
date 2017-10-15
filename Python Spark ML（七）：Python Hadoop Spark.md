# Python Spark ML（七）：Python Hadoop Spark
## Python + Spark2.0 + Hadoop 的機器學習與大數據架構
![](https://dl.dropbox.com/s/e9l1o54uyhwane1/p0.PNG)
> 個人對上圖架構的理解，大數據架構可以分成三個部分來談論：
> * 大數據存儲平台：
> 大數據最重要的部份是要有足夠大量的數據供資料分析或是機器學習使用，因此如何存取如此大量的數據成為大數據的基礎建設要件，例如分片(sharding)、
> 副本集(replica set)、分散式儲存等相關概念被提出並實現，而以數據的存儲模式(Schema)強度我概分為以下三種：
>> * 檔案系統(File System)或是資料格式(Data format)：以分散式儲存為概念，可以儲存大量的資料，並且能夠對資料做運算。例如HDFS、Parquet、JSON等。
>> * Nosql資料庫：不同於RDB資料庫對於數據存儲模式(Schema)有強制要求，Nosql資料庫可以不需要固定的Schema，易於實現分片、水平擴展，例如：HBase、MongoDB、Redis等等
>> * RDB資料庫：對於數據存儲模式(Schema)有強制要求，例如：Oracle、Mysql、MS-SQL等
> * 大數據運算平台：
> 當有了大數據存儲的平台之後，接著便是位於存儲平台之上的運算平台，我概分為以下三種：
>> * Map-Reduce：最基本的運算框架，可以配合分散式儲存的檔案系統，如HDFS進行分散式運算，缺點是透過硬碟I/O速度很慢。
>> * Batch：利用記憶體比硬碟更快的特性，將數據批次拉到記憶體中運算，Spark就是知名的記憶體運算框架。
>> * Streaming：流運算，一樣是將數據拉到記憶體中運算，但是透過實時的運算處理每一筆數據，例如：Flink、Storm
> * 演算法：
> 有了大數據平台後，就可以透過演算法來完成機器學習，而Python語言的Pandas、Scikit-learn等套件就可以提供許多演算法來訓練數據、建立模型。

## Python Spark 機器學習與 Hadoop 大數據 Chapter 01 摘要
* 機器學習：透過演算法，利用歷史資料來進行訓練，建立模型，當有新的資料時，就可以運用模型來進行預測，可以分成兩階段：
> * 訓練(Training)：訓練的資料由特徵(features)及標籤(label)所組成。
> * 預測(Predict)：新輸入的資料，透過特徵萃取，利用訓練出來的模型進行預測。
* 機器學習分類：
> * 監督式學習：二元分類、多元分類、迴歸分析
> * 非監督式學習：分群
* Spark 介紹：是一種基於記憶體的分散式叢集運算框架，核心是RDD(Resilient Distributed Dataset)彈性分散式資料集，可以與其他系統相容，
能夠匯入外部儲存系統的資料集，例如HDFS、Hbase、MongoDB。
* Spark 主要功能：
> * Spark RDD：RDD(Resilient Distributed Dataset)彈性分散式資料集，基於記憶體的運算框架。
> * Spark SQL：具備Schema的RDD，可以使用類SQL語法查詢，執行數據分析。
> * Spark Streaming：使用Micro Batch的概念執行即時資料串流的處理。
> * Spark ML：Spark機器學習庫，可以使用許多常見的機器學習演算法。
> * Spark GraphX：分散式圖形處理架構。
* Python Spark 機器學習：Python是資料分析常用語言，同時資料分析的相關模組很多，且方便開發爬蟲、網站。
> * Spark MLlib：RDD-based 機器學習API
> * Spark ML pipeline：Dataframes-based 機器學習API
* Hadoop 介紹：HDFS + Map-Reduce
> Spark與Hadoop的結合，Spark取代了Map-Reduce的運算框架位置，利用HDFS分散式檔案系統來存取數據，可以搭配YARN，將資源管理交給YARN，Spark專注處理運算工作。
