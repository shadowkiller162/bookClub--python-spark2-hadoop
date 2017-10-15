# Python Spark ML（六）：Decision Tree Algorithm Survey
## Comparison of classification tree methods
![](https://dl.dropbox.com/s/n5vn4463kf93cxg/Comparison%20of%20Classification%20Tree%20Methods.png)

* Unbiased splits(無偏差分割)
> 傳統的遞迴分割方法，使用基於熵(Entropy)的措施，如吉尼增益(Gini gain)或信息增益(Information gain)，作為分類選擇標準。
> 但是在演算法中會傾向於選擇那些「能夠提供更多分裂可能性的變量」，例如，如果預測變量是序數或名義比例的分類變量， 變量會選擇偏向有利於具有更多類別的分類變量。
> 因此，Unbiased splits(無偏差分割)試圖處理變量選擇偏差問題。[1]

* Split type(分割類型)
> 分割方式(對線性變量做有序分割或是對單一變量做分割)。

* Branches/split(分支)
> 意指決策樹分支，每個分支均代表一組合理的邏輯。

* Interaction test(互動測試)
> 決策樹中的變數進行兩兩測試，檢驗是否互相獨立。

* Pruning(修剪)
> 決策樹生成之後，刪除不符合設定條件的葉節點。

* User-specified Costs
> 使用者設定分類的成本花費。

* User-specified Priors
> 使用者設定容許預測錯誤的機率。

* Variable Ranking
> 變量值域範圍

* Node Models
> 決策樹各單獨分支節點模型

* Bagging & Ensembles
> * 整體學習演算法(ensemble learning algorithms)，整體學習演算法不會像決策樹學習演算法只是去尋找一個最好的假說來解釋數據，而是建造一組由多個假說組合而成的整體假說，然後再採用一些模式讓這些多個假說進行"投票"，以推測(predict)新增資料點的合理標籤。
> * Bagging(Bootstrap Aggregating)方法，Bagging方法在每次迭代過程中，透過來自 m 個訓練的資料點均勻取樣所得到的資料點替換原先的資料點，而建立新的、重新取樣過的訓練資料。在這些新造的訓練資料中，可能有些資料點是重複出現許多次，也可能有一些原本的資料點根本不再出現。如果學習演算法具有不穩定(unstable)的性質的話，在這種情況下，使用Bagging的方法將會產生一個包含多樣化特性的整體假說（即單一假說和假說之間的差異大）。

* Missing values
> 遺失值處理方式
> * missing value branch
>> 發現分支變數含有缺失值的節點很多時，可以把缺失值作為一個單獨的分支來進行搜索。
> * missing value imputation
>> 用替代值插補(imputation)丟失的數據。
> * missing value category
>> Predictors can be nominal or ordinal and there is usually provision for a missing-value category.
> * surrogate splits
>> 替代分割，以與主變量相同或是近似的方式來進行分割。
> * probability weights
>> 依據概率權重來補缺失值

---
References

[1]Strobl, Boulesteix, Augustin."Unbiased split selection for classification trees based on the Gini Index"：Sonderforschungsbereich (2005)

[2]Bagging, boosting and stacking in machine learning - Stack Exchange
https://stats.stackexchange.com/questions/18891/bagging-boosting-and-stacking-in-machine-learning

[3]整體學習(Ensemble Learning)入門 - CMLab

[4]Imputation (statistics) - 維基百科
https://en.wikipedia.org/wiki/Imputation_(statistics)

[5]Surrogate Splits (CART algorithms) -IBM
https://www.ibm.com/support/knowledgecenter/ja/SSLVMB_21.0.0/com.ibm.spss.statistics.help/alg_tree-cart_surrogate-split.htm

