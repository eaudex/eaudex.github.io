# SparkML

## DataFrame
* Abstrasts the concept of how the data is stored distriutedly.

## Transformer
* Transforms one **DataFrame** into another **DataFrame**
* Key API: ```def transform(DataFrame): DataFrame = {}```
* Use cases:
    * Feature transfomer
        * Take DataFrame columns as input (e.g. text)
        * Map the input into new DataFrame columns as output (e.g. vector)
    * ML model
        * Transform a DataFrame with **features** into a DataFrame with **predictions**

## Estimator
* Fits/trains a Tranformer(output) to a DataFrame(input)
* API: ```fit(DataFrame): Transformer```
* e.g. an ML algo is an estimator that fits an ML model(a Transformer) to the
  given DataFrame
* e.g. a feature extraction algo can be an estimator that fits an feature
  extraction model(a Transformer) to the given DataFrame

## Model
* A transformer fitted by an estimator


## Parameter

# Implementing ```Estimator``` and ```Model```
## Implementing ```Estimator```
```
class XXX(override val uid: String)
    extends Estimator[XXXModel] with XXXParams {

    def this() = this(Identifiable.randomUID("xxx"))

    override def transformSchema(schema: StructType): StructType = {
    }

    override def fit(dataset: DataFrame): XXXModel = {
    }

    override def copy(extra: ParamMap): XXX = {
    }
}
```

## Implementing ```Model```
```
class XXXModel(override val uid: String, ...)
    extends Model[XXXModel] with XXXParams {

    override def transformSchema(schema: StructType): StructType = {
    }

    override def transform(dataset: DataFrame): DataFrame = {
    }

    override def copy(extra: ParamMap): XXXModel = {
    }
}
```


# Spark Feature Extraction

## Data
```
val df = Seq(
  (Some(2), Some(2), Some(3)),
  (Some(4), Some(3), Some(3)),
  (Some(6), Some(4), Some(1)),
  (Some(8), Some(5), Some(2)),
  (Some(10), Some(6), Some(2)),
  (Some(5), Some(2), Some(2))
).toDF("col1", "col2", "col3").alias("df")

df.printSchema()
df.show()
```
```
root
 |-- col1: integer (nullable = true)
 |-- col2: integer (nullable = true)
 |-- col3: integer (nullable = true)

+----+----+----+
|col1|col2|col3|
+----+----+----+
|   2|   2|   3|
|   4|   3|   3|
|   6|   4|   1|
|   8|   5|   2|
|  10|   6|   2|
|   5|   2|   2|
+----+----+----+
```

---

## [StringIndexer](https://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.ml.feature.StringIndexer)
* Index a categorical value (of String type)
* Input: String
* Output: Double


## [OneHotEncoder](https://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.ml.feature.OneHotEncoder)
* Transform a categorical index (of Double type) to a vector in one hot encoding
* Input: Double
* Output: Vector


## [VectorAssembler](https://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.ml.feature.VectorAssembler)
* Input: a set of columns: Double or Vector
* Output: features: Vector

### Example
```
>>>>>>>>>>=============== Input ===============>>>>>>>>>>
root
 |-- col1: integer (nullable = true)
 |-- col2: integer (nullable = true)
 |-- col3: integer (nullable = true)

+----+----+----+
|col1|col2|col3|
+----+----+----+
|   2|   2|   3|
|   4|   3|   3|
|   6|   4|   1|
|   8|   5|   2|
|  10|   6|   2|
|   5|   2|   2|
+----+----+----+
```

```
import org.apache.spark.ml.feature.VectorAssembler

val df: DataFrame = .... // input

val assembler = new VectorAssembler()
  .setInputCols(Array("col1", "col2", "col3"))
  .setOutputCol("features")
val dfg = assembler.transform(df)

dfg.printSchema()
dfg.show()
```

```
>>>>>>>>>>=============== VectorAssembler ===============>>>>>>>>>>
root
 |-- col1: integer (nullable = true)
 |-- col2: integer (nullable = true)
 |-- col3: integer (nullable = true)
 |-- features: vector (nullable = true)

+----+----+----+--------------+
|col1|col2|col3|      features|
+----+----+----+--------------+
|   2|   2|   3| [2.0,2.0,3.0]|
|   4|   3|   3| [4.0,3.0,3.0]|
|   6|   4|   1| [6.0,4.0,1.0]|
|   8|   5|   2| [8.0,5.0,2.0]|
|  10|   6|   2|[10.0,6.0,2.0]|
|   5|   2|   2| [5.0,2.0,2.0]|
+----+----+----+--------------+
```


## [VectorIndexer](https://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.ml.feature.VectorIndexer)
* Input: features: Vector
* Output: indexed_features: Vector

### Example
```
>>>>>>>>>>=============== Input ===============>>>>>>>>>>
root
 |-- col1: integer (nullable = true)
 |-- col2: integer (nullable = true)
 |-- col3: integer (nullable = true)
 |-- features: vector (nullable = true)

+----+----+----+--------------+
|col1|col2|col3|      features|
+----+----+----+--------------+
|   2|   2|   3| [2.0,2.0,3.0]|
|   4|   3|   3| [4.0,3.0,3.0]|
|   6|   4|   1| [6.0,4.0,1.0]|
|   8|   5|   2| [8.0,5.0,2.0]|
|  10|   6|   2|[10.0,6.0,2.0]|
|   5|   2|   2| [5.0,2.0,2.0]|
+----+----+----+--------------+
```

```
import org.apache.spark.ml.feature.VectorIndexer

val dfg: DataFrame = .... // input

val indexer = new VectorIndexer()
  .setInputCol("features")
  .setOutputCol("indexed_features")
  .setMaxCategories(5)
val indexerModel = indexer.fit(dfg)
val categoricalFeatures: Set[Int] = indexerModel.categoryMaps.keys.toSet
println("Categorical features: " + categoricalFeatures.mkString(", "))

val indexedData = indexerModel.transform(dfg)
indexedData.show()
```

```
>>>>>>>>>>=============== VectorIndexer ===============>>>>>>>>>>
Categorical features: 1, 2

+----+----+----+--------------+----------------+
|col1|col2|col3|      features|indexed_features|
+----+----+----+--------------+----------------+
|   2|   2|   3| [2.0,2.0,3.0]|   [2.0,0.0,2.0]|
|   4|   3|   3| [4.0,3.0,3.0]|   [4.0,1.0,2.0]|
|   6|   4|   1| [6.0,4.0,1.0]|   [6.0,2.0,0.0]|
|   8|   5|   2| [8.0,5.0,2.0]|   [8.0,3.0,1.0]|
|  10|   6|   2|[10.0,6.0,2.0]|  [10.0,4.0,1.0]|
|   5|   2|   2| [5.0,2.0,2.0]|   [5.0,0.0,1.0]|
+----+----+----+--------------+----------------+
```


# Feature Scaling
## StandardScaler
$$(f-\mu)/\sigma$$
where $$\mu$$ is the feature mean; $$\sigma$$ is the feature standard deviation.
* $$-\mu$$ is sometimes ignored because centering will destroy data sparsity.

## MinMaxScaler
$$(f-m)/(M-m) \in [0,+1]$$
* Centering will destroy sparsity

## MaxAbsScaler
$$f/M \in [-1,+1]$$
where $$M$$ is the maximum absolute value in the feature.


# Numerical => Categorical
## Binarizer
    * Given a threshold, t
        * v > t -> 1.0
        * v <= t -> 0.0
## Bucketizer
    * Given splits
## QuantileDiscretizer
    * Auto determine splits


# Q & A
* Fix ```.toDF()``` error?
Add the following line to the code.
```
import sqlContext.implicits._
```

* Sample LIBSVM Data?
* [https://raw.githubusercontent.com/apache/spark/master/data/mllib/sample_libsvm_data.txt](https://raw.githubusercontent.com/apache/spark/master/data/mllib/sample_libsvm_data.txt)









