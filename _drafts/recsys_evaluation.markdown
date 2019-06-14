MAP Mean Average Precision

推薦システム評価の指標の一つ。

下記の三つの条件を満たすアルゴリズムが適用します：

- ランキング付きのアイテムリスト
- アイテムは当たる・当たってない2値がある
- 下のアイテムが使う可能性が低い

MAPは使える指標となる。

## 詳細

###

従来、二項分類のアルゴリズムを評価するために、適合率と再現率は二つの指標：

$$
p=\frac{\# correct\ positive}{\# predicted\ positive}
$$


Very Popular evaluation Metric for algorithms that do information retrieval, like google search.

If you have an algorithm that is

- returning a ranked ordering of items,
- each item is either hit or miss,
- items further down in the list are less likely to be used

then maybe MAP is the metric for you.


MAP computs the mean of the Average Precision over all users.
AP is a measure that takes in a ranked list of your N recommendations and compares it to a list of the true set of "correct", or "relevant" recommendations for that user.




# Details

For binary classification

$$
p=\frac{\# correct\ positive}{\# predicted\ positive}
$$

$$
r=\frac{\# correct\ positive}{\# with\ condition}
$$


### Precision and Recall of recomender system

$$
p=\frac{#\ of\ recommendations\ that\ are\ relevant}{#\ of\ items\ recommended}
$$

$$
r=\frac{#\ of recommendations that are relevant}{# of all the possible relevant items}
$$

### Precision and Recall at Cutoff k

Precision and Recall don't seem to care about ordering.


precision and recall at cutoff k

are simply the precision and recall calculatred by considering only the subset of your recommendations from rank 1 through k.

P(k)

### Average Precision


The number of relevant items in the full space of items is m, then:

$$
AP@N=\sum_{k=1}^{N}{(P(k) if k^{th} item was relevant)}=\frac{1}{m}\sum_{k=1}^{N}{P(k) \cdot rel(k)}
$$

rel(k) : indicator that says whether that k^{th} item was relevant

### Mean Average Precision

AP is for one recommend
for U users/recommend, take a mean

$$
MAP@N=\frac{1}{|U|}\sum_{u=1}^{|}{U|(AP@N)_u}
$$

### Recalls

$$
AP@N=\sum_{k=1}^{N}{(P(k) if k^{th} item was relevant)}=\sum_{k=1}^{N}{P(k) \Delta r(k)}
$$


# Reference

http://sdsawtelle.github.io/blog/output/mean-average-precision-MAP-for-recommender-systems.html
