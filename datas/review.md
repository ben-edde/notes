# review

## data

* attribute types
  * nominal
  * ordinal
  * interval
  * ratio
* dataset types
  * record data
  * transaction or market basket data
  * data matrix
  * sparse data matrix
* data quality
  * measurement
    * precision
    * bias
  * issue
    * noise
    * outlier
    * missing values
* data preprocessing
  * aggregation
  * sampling
  * dimensionality reduction
    * feature transformation
      * PCA
    * feature subset selection
      * embedded approaches
      * filter approaches
      * wrapper approaches
  * discretization
  * normalization
* similarity
  * nominal
  * ordinal
  * interval / ratio
* distance
  * properties
  * Euclidean distance
* summary statistics
  * relative frequency and mode
  * mean
  * median
  * range
  * variance
* multivariate summary statistics
  * covariance
  * correlation coefficient
* visualization
  * histogram
  * scatter plot

## decision tree

* classification
  * purpose
  * behavior
* measurement
  * confusion matrix
  * accuracy
  * error rate
* decision tree
  * what is it
  * how it work
  * why it work
  * assumption it uses
  * structure
  * construction algos
  * attribute test
  * impurity measures
    * information entropy
    * Gini index
    * classification error rate
  * gain ratio
  * handling continuous attributes
  * oblique decision tree

## classification evaluation

* classification error
  * training error
  * generalization error
* issues in training
  * overfitting
  * underfitting
* generalization error estimation
  * resubstitution estimate
  * estimates incorporating model complexity
  * using validation set
* handling overfitting in decision tree
  * prepruning
  * postpruning
* classifier evaluation
  * holdout
  * cross validation

## knn and naive Bayes

* knn
  * what is it
  * how it work
  * why it work
  * assumption it uses

* naive Bayes
  * Bayes theorem
  * what is it
  * how it work
  * why it work
  * assumption it uses
  * handling continuous attributes
    * normal distribution

## cluster analysis

* purpose
  * group data by similarity
* types
  * partitional vs hierarchical
    * partitional
      * division of datasets into subsets
    * hierarchical
      * nested clusters
      * tree structure
  * exclusive vs fuzzy
    * exclusive
      * 1 cluster for 1 object
    * fuzzy
      * measure on extends of belonging to each cluster
      * [0,1]
      * matrix (object X cluster)
      * can be convert to exclusive
  * complete vs partial
    * complete
      * every object get assignment
    * partial
      * skip some objects
      * skip noise / outliers

* k-means
  * what is it
    * prototype (representative)-based clustering
    * partitional
    * exclusive
    * complete
  * how it work
    * select k points as initial centroids
    * repeat
      * assign each object to closest centroids
      * update centroids by assigned objects
    * stop when centroids cannot be updated
  * why it work
    * centroid is updated with mean of objects, act as representative
    * centroids "move" to "correct" positions (centers of clusters)
    * natural grouping is provided when no more change in centroids
  * assumption it uses
    * no outliers
    * k is defined correctly
  * distance
    * Euclidean distance
      * distance between objects and centroids
    * sum of squared error (SSE)
      * measure quality of assignment
    * assign object to centroid with lowest SSE
  * choosing initial centroids
    * random initialization
      * may be poor
    * try several more time
      * try several sets of randomly chosen centroids
      * choose the one with minimum SSE
  * outlier
    * poor update of centroid
    * find outlier by track contribution of each object to SSE, the one with abnormal high contribution may be  outliers
  * post-processing
    * to decrease SSE by use more clusters
      * split a cluster
        * try to split cluster and find resultant SSE
        * find a split which lead to largest decrease in SSE
      * Introduce a new cluster centroid
        * use an object as new centroid
        * often use farthest one from its assigned centroid (in terms of contribution to SSE)
    * minimize the increase in SSE by using less clusters
      * disperse a cluster
        * try removing centroids and find resultant SSE
        * choose the one which lead to least increase in overall SSE
      * merge two clusters
        * try merging clusters
        * choose the 2 centroids which their merge lead to least increase in SSE
  * limitations
    * poor performance to non-spherical shapes clusters
    * good at globular clusters of similar sizes and
densities
    * good at well separated clusters

* hierarchical clustering
  * purpose
  * generation
    * agglomerative
      * what is it
        * algo to generate hierarchical clustering
      * how it work
        * merge cluster from more to less
        * merge closest 2 cluster
      * why it work
        * each merge maintain the hierarchical structure
    * divisive
      * what is it
        * algo to generate hierarchical clustering
      * how it work
        * split cluster from less to more
      * why it work
        * each split maintain the hierarchical structure
  * cluster distance measure
    * single link
      * min distance between 2 clusters
      * good for handling clusters with non-elliptical shape
    * complete link
      * max distance between 2 clusters
      * make globular shape clusters
    * group average
      * take mean of all pairs

## association analysis

* purpose
  * find relations between items
* data structure
  * transaction
    * unique id
    * set of items
  * representation
    * string
    * binary
* association rule
  * relation between itemsets
  * itemset X(antecedent) -> itemset Z(consequent) where X and Z are disjoint itemsets
  * support
    * occurrence of the rule in dataset
    * likelihood of rule
  * confidence
    * occurrence of rule while X occur
    * conditional probability
    * strength of rule
  * co-occurrence instead of causality
  * rules mining
    * find rules from dataset which fulfill requirement on support and confidence
    * stages
      * Frequent itemset generation
        * find all itemsets satisfy support threshold
        * as "frequent itemsets"
      * Rule generation
        * find high confidence rules generated from frequent itemsets
        * as "strong rules"
    * brute force approach
      * count occurrence of all itemsets in all transactions
      * generate and test all rules
    * Apriori algorithms
      * Apriori principle
        * if an itemset is frequent, all its subsets must be frequent
        * if an itemset is infrequent, all its supersets must be infrequent
      * support-based pruning
        * based on anti-monotone property of support
        * support of subset can be larger than the one of superset but not vice versa
      * what is it
        * a association rule mining algorithm which reduce complexity by skipping some itemsets and rules
      * how it work
        * Frequent itemset generation
          * start from 1-itemset and find support
          * discard itemsets fail to satisfy support threshold
          * repeat
            * generate candidate itemsets from remaining itemsets (use 1 more item from previous level)
            * discard itemsets contain infrequent subsets
            * find support of itemsets
            * discard itemsets fail to satisfy support threshold
          * stop when no more itemset can be generated
        * Rule generation
          * generate rules using frequent itemsets
          * partition frequent itemsets into antecedent itemset and consequent itemset
          * no need to filter by support (support of each rule is same as itemsets used for generation)
          * if a rule has low confidence, rules with subset of antecedent itemset as antecedent itemset cannot have higher confidence, skip all these rules
          * similarly, if a rule has low confidence, rules with superset of consequent itemset as consequent itemset cannot have higher confidence, skip all these rules
      * why it work
        * prune tasks tree by support/confidence to skip counting some itemsets or rules
        * lower complexity
