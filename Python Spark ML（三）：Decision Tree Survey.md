# Python Spark ML（三）：Decision Tree Survey
## 決策樹 Decision tree

### 定義:
* 在機器學習中，決策樹是一個過程直覺單純、執行效率也相當高的監督式機器學習模型；他代表的是對象屬性與對象值之間的一種映射關係，樹中每個節點表示某個對象，而每個分叉路徑則代表某個可能的屬性值，
而每個葉節點則對應從根節點到該葉節點所經歷的路徑所表示的對象的值。
* 數據挖掘中決策樹是一種經常要用到的技術，可以用於分析數據，同樣也可以用來作預測。
### 類型:
* 分類樹分析是當預計結果可能為離散類型（例如三個種類的花，輸贏等）使用的概念。
* 回歸樹分析是當局域結果可能為實數（例如房價，患者住院時間等）使用的概念。
* CART分析是結合了上述二者的一個概念。CART是Classification And Regression Trees的縮寫。
### 優點:
* 決策樹易於理解和實現，人們在通過解釋後都有能力去理解決策樹所表達的意義。
* 對於決策樹，數據的準備往往是簡單或者是不必要的，其他的技術往往要求先把數據一般化，比如去掉多餘的或者空白的屬性。
* 能夠同時處理數據型和常規型屬性，其他的技術往往要求數據屬性的單一。
* 是一個白盒模型；如果給定一個觀察的模型，那麼根據所產生的決策樹很容易推導出相應的邏輯表達式。
* 易於通過靜態測試來對模型進行評測，表示有可能測量該模型的可信度。
* 在相對短的時間內能夠對大型數據源做出可行且效果良好的結果。
### 缺點:
* 對於那些各類別樣本數量不一致的數據，在決策樹當中信息增益的結果偏向於那些具有更多數值的特徵。
* 對連續性的欄位比較難預測。
* 「Overfitting（過度擬合）」的問題，因為我們如果沒有對樹的成長作限制，演算法最後就會為每個不同特徵值創建新的分類節點，最後將所有資料作到100%正確的分類，因此為了預防Overfitting，我們會採取下列兩種方式：設限及剪枝。
> - 設限
>> 1. Minimum samples for a node split：資料數目不得小於多少才能再產生新節點。
>> 2. Minimum samples for a terminal node (leaf)：要成為葉節點，最少需要多少資料。
>> 3. Maximum depth of tree (vertical depth)：限制樹的高度最多幾層。
>> 4. Maximum number of terminal nodes：限制最終葉節點的數目
>> 5. Maximum features to consider for split：在分離節點時，最多考慮幾種特徵值。
> - 剪枝
>> 1. 針對樹設定一個適當的深度。
>> 2. 從底部開始，移除所有回傳為負值（與上一層相比）的節點葉子。
>> 3. 如果有一分枝回覆值為-10，但下一個分枝回覆+20，整體加總為+10，因此Tree pruning仍會保留該分枝
### 例子:
* 假設我們想要分類三種主題的相片：火山、海洋、森林，很明顯的，這三大類圖片有著不同的主色，例如火山偏紅、海洋偏藍、森林偏綠，那麼，我們的決策樹可設計並運作如下：
![](https://dl.dropbox.com/s/s5jfknq4j2msju1/Decisiontree.png)Decision tree

### 程式範例(Python):
```python
# Import the necessary modules and libraries
import numpy as np
from sklearn.tree import DecisionTreeRegressor
import matplotlib.pyplot as plt

# Create a random dataset
rng = np.random.RandomState(1)
X = np.sort(5 * rng.rand(80, 1), axis=0)
y = np.sin(X).ravel()
y[::5] += 3 * (0.5 - rng.rand(16))

# Fit regression model
regr_1 = DecisionTreeRegressor(max_depth=2)
regr_2 = DecisionTreeRegressor(max_depth=5)
regr_1.fit(X, y)
regr_2.fit(X, y)

# Predict
X_test = np.arange(0.0, 5.0, 0.01)[:, np.newaxis]
y_1 = regr_1.predict(X_test)
y_2 = regr_2.predict(X_test)

# Plot the results
plt.figure()
plt.scatter(X, y, c="darkorange", label="data")
plt.plot(X_test, y_1, color="cornflowerblue", label="max_depth=2", linewidth=2)
plt.plot(X_test, y_2, color="yellowgreen", label="max_depth=5", linewidth=2)
plt.xlabel("data")
plt.ylabel("target")
plt.title("Decision Tree Regression")
plt.legend()
plt.show()
```
![](https://dl.dropbox.com/s/benni4tfilseohk/DecisionTreeRegression.png)
---

References

[1]決策樹-維基百科
https://zh.wikipedia.org/wiki/%E5%86%B3%E7%AD%96%E6%A0%91

[2]決策樹-MBA 智庫百科
http://wiki.mbalib.com/zh-tw/%E5%86%B3%E7%AD%96%E6%A0%91

[3]決策樹 Decision trees - CH.Tseng
https://chtseng.wordpress.com/2017/02/10/%E6%B1%BA%E7%AD%96%E6%A8%B9-decision-trees/

[4]機器學習：使用Python - Contributor: 陳巧寧、曾裕勝、黃騰毅 、蔡奕甫
https://machine-learning-python.kspax.io/Decision_trees/ex1_Decision_tree_regression.html
