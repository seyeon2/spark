---
레이아웃: 전역
제목: 기초 통계 - RDD 기반 API
displayTitle: 기초 통계 - RDD 기반 API
라이센스: |
  하나 이상의 기여자 라이센스 계약에 따라 ASF(Apache Software Foundation)에 라이센스가 부여됩니다. 저작권 소유에 대한 추가 정보는 본 작업과 함께 배포된 NOTICE 파일을 참조하십시오. ASF는 Apache License 버전 2.0("License")에 따라 이 파일에 라이센스를 부여하며, 라이센스를 준수하지 않는 한 이 파일을 사용할 수 없습니다. 귀하는 http://www.apache.org/licenses/LICENSE-2.0에서 라이센스 복사본을 얻을 수 있습니다. 관련 법률에서 요구하거나 서면으로 동의하지 않는 한 라이센스에 따라 배포되는 소프트웨어는 명시적 또는 묵시적 보증 또는 조건 없이 "있는 그대로" 배포됩니다. 라이센스 아래의 사용 권한 및 제한 사항을 관리하는 특정 언어는 라이센스를 참조하십시오.
  
---

* Table of contents
{:toc}


`\[
\newcommand{\R}{\mathbb{R}}
\newcommand{\E}{\mathbb{E}}
\newcommand{\x}{\mathbf{x}}
\newcommand{\y}{\mathbf{y}}
\newcommand{\wv}{\mathbf{w}}
\newcommand{\av}{\mathbf{\alpha}}
\newcommand{\bv}{\mathbf{b}}
\newcommand{\N}{\mathbb{N}}
\newcommand{\id}{\mathbf{I}}
\newcommand{\ind}{\mathbf{1}}
\newcommand{\0}{\mathbf{0}}
\newcommand{\unit}{\mathbf{e}}
\newcommand{\one}{\mathbf{1}}
\newcommand{\zero}{\mathbf{0}}
\]`

## Statistics 요약

우리는 'Statistics'에서 사용할 수 있는 함수 'colStats'를 통해 'RDD[Vector]'에 대한 열 요약 통계를 제공한다.

<div class="codetabs">
<div data-lang="scala" markdown="1">

[`colStats()`](api/scala/org/apache/spark/mllib/stat/Statistics$.html)는
[`MultivariateStatisticalSummary`](api/scala/org/apache/spark/mllib/stat/MultivariateStatisticalSummary.html)의 인스턴스 값을 반환합니다. 이것은 열 단위 최대값, 최소값, 평균, 분산 및 0이 아닌 수를 포함합니다.
  
API에 대한 자세한 내용은 [`MultivariateStatisticalSummary` Scala docs](api/scala/org/apache/spark/mllib/stat/MultivariateStatisticalSummary.html) 를 참조하십시오.

{% include_example scala/org/apache/spark/examples/mllib/SummaryStatisticsExample.scala %}
</div>

<div data-lang="java" markdown="1">

[`colStats()`](api/java/org/apache/spark/mllib/stat/Statistics.html)는
[`MultivariateStatisticalSummary`](api/java/org/apache/spark/mllib/stat/MultivariateStatisticalSummary.html)의 인스턴스를 반환합니다. 여기에는 열 단위 최대값, 최소값, 평균, 분산 및 0이 아닌 수와 총 카운트가 포함됩니다.

API에 대한 자세한 내용은 [`MultivariateStatisticalSummary` Java docs](api/java/org/apache/spark/mllib/stat/MultivariateStatisticalSummary.html) 를 참조하십시오.

{% include_example java/org/apache/spark/examples/mllib/JavaSummaryStatisticsExample.java %}
</div>

<div data-lang="python" markdown="1">
  
[`colStats()`](api/python/reference/api/pyspark.mllib.stat.Statistics.html#pyspark.mllib.stat.Statistics.colStats)는
[`MultivariateStatisticalSummary`](api/python/reference/api/pyspark.mllib.stat.MultivariateStatisticalSummary.html)의 인스턴스를 반환합니다. 여기에는 열 단위 최대값, 최소값, 평균, 분산 및 0이 아닌 수와 총 카운트가 포함됩니다.

API에 대한 자세한 내용은 [`MultivariateStatisticalSummary` Python docs](api/python/reference/api/pyspark.mllib.stat.MultivariateStatisticalSummary.html) 를 참조하십시오.

{% include_example python/mllib/summary_statistics_example.py %}
</div>

</div>

## 상관관계

두 데이터 열 사이의 상관 관계를 계산하는 것은 통계량에서 일반적인 작업입니다. `spark.mllib`에서 우리는 많은 시리즈 사이의 쌍방향 상관 관계를 계산할 수 있는 유연성을 제공한다. 지원되는 상관 방법은 현재 Pearson과 Spearman의 상관 관계입니다.

<div class="codetabs">
<div data-lang="scala" markdown="1">

  
  [`Statistics`](api/scala/org/apache/spark/mllib/stat/Statistics$.html) 는 시리즈 간의 상관 관계를 계산하는 방법을 제공한다. 입력 유형에 따라 2개의 RDD[Double] 또는 1개의 RDD[Vector]는 각각 더블 또는 상관관계인 매트릭스가 된다.

API에 대한 자세한 내용은 [`Statistics` Scala docs](api/scala/org/apache/spark/mllib/stat/Statistics$.html)를 참조하십시오.

{% include_example scala/org/apache/spark/examples/mllib/CorrelationsExample.scala %}
</div>

<div data-lang="java" markdown="1">
  
[`Statistics`](api/java/org/apache/spark/mllib/stat/Statistics.html) 는 다음과 같은 방법을 제공한다.
시계열 간의 상관 관계를 계산합니다. 
입력 유형에 따라 두 개의 'JavaDouble'이 있습니다.RDD 또는 자바RDD<벡터>는 출력이 각각 더블 또는 상관관계 매트릭스가 될 것이라고 밝혔다

API에 대한 자세한 내용은 [`Statistics` Java docs](api/java/org/apache/spark/mlib/stat/statistics.html)를 참조하십시오.
  
{% include_example java/org/apache/spark/examples/mllib/JavaCorrelationsExample.java %}
</div>

<div data-lang="python" markdown="1">
  
[`Statistics`](api/python/참조/api/pyspark.mlib.stat).Statistics.html)는 열 간의 상관 관계를 계산하는 방법을 제공합니다. 입력 유형에 따라 2개의 RDD[Double] 또는 1개의 RDD[Vector]는 각각 더블 또는 상관관계인 매트릭스가 된다.

[`Statistics` Python docs](api/python/reference/api/pyspark.mllib.stat.Statistics.html)에서 API에 대한 자세한 내용을 확인하십시오. 
  
{% include_example python/mllib/correlations_example.py %}
</div>

</div>

## 층화 표본

'spark.mllib'에 상주하는 다른 통계 함수와 달리 계층화된 샘플링 방법인 'sampleByKey'와 'sampleByKeyExact'는 키-값 쌍의 RDD에서 수행할 수 있다. 계층화된 샘플링의 경우 키는 레이블로, 값은 특정 속성으로 생각할 수 있습니다. 예를 들어, 키는 남성 또는 여성 또는 문서 ID가 될 수 있으며, 각 값은 모집단의 연령 목록 또는 문서에 있는 단어 목록이 될 수 있습니다. 'sampleByKey' 방법은 관찰이 샘플링될지 여부를 결정하기 위해 코인을 플립하므로 데이터에 대한 한 번의 패스가 필요하며 *expected* 샘플 크기를 제공한다. 'sampleByKeyExact'는 'sampleByKey'에 사용되는 계층당 단순 무작위 샘플링보다 훨씬 많은 자원을 필요로 하지만 99.99%의 신뢰도로 정확한 샘플링 크기를 제공할 것이다. 'sample ByKeyExact'는 현재 python에서 지원되지 않습니다.

<div class="codetabs">
<div data-lang="scala" markdown="1">

[`sampleByKeyExact()`](api/scala/org/apache/spark/rdd/PairRDDFunctions.html) 사용자는 $f_k$에 대해 $lceil f_k \cdot n_k \rceil \, \rceil \, \forall k \in K$ 항목을 정확하게 샘플링할 수 있습니다. 대체되지 않은 샘플링은 샘플 크기를 보장하기 위해 RDD에 대한 추가 패스를 1회 필요로 하는 반면 대체 샘플링은 2회의 추가 패스를 필요로 합니다.

{% include_example scala/org/apache/spark/examples/mllib/StratifiedSamplingExample.scala %}
</div>

<div data-lang="java" markdown="1">
[`sampleByKeyExact()`](api/java/org/apache/spark/api/java/JavaPairRDD.html) 사용자는 $f_k$에 대해 $lceil f_k \cdot n_k \rceil \, \rceil \, \forall k \in K$ 항목을 정확하게 샘플링할 수 있습니다. 대체되지 않은 샘플링은 샘플 크기를 보장하기 위해 RDD에 대한 추가 패스를 1회 필요로 하는 반면 대체 샘플링은 2회의 추가 패스를 필요로 합니다.

{% include_example java/org/apache/spark/examples/mllib/JavaStratifiedSamplingExample.java %}
</div>
<div data-lang="python" markdown="1">
  
[`sampleByKey()`](api/python/reference/api/pyspark.RDD.sampleByKey.html#pyspark.RDD.sampleByKey) 를 통해 사용자는 약 \lceil f_k \cdot n_k \rceil \, \forall k \in K$ 항목을 샘플링할 수 있다. 여기서 $f_k$는 키 $k$에 대한 키-값 쌍의 수이고 $K$는 키의 집합이다.
 
*Note:* `sampleByKeyExact()` 는 현재 파이썬에서 지원되지 않습니다.

{% include_example python/mllib/stratified_sampling_example.py %}
</div>

</div>

## 가설 검증

가설 검정은 결과가 통계적으로 유의한지, 결과가 우연히 발생했는지 여부를 판별하는 강력한 통계 도구입니다. `spark.mllib`은 현재 적합성과 독립성에 대한 Pearson의 카이 제곱(\chi^2$) 테스트를 지원한다. 입력 데이터 유형에 따라 적합도 검정이 수행되는지 독립성 검정이 수행되는지 여부가 결정됩니다. 적합도 검사에는 벡터의 입력 유형이 필요한 반면 독립성 검사에는 매트릭스가 입력으로 필요합니다.

`spark.mllib`은 또한 카이 제곱 독립성 테스트를 통한 형상 선택이 가능하도록 입력 유형 'RDD[LabelPoint]'를 지원합니다.

<div class="codetabs">
<div data-lang="scala" markdown="1">

[`Statistics`](api/scala/org/apache/spark/mllib/stat/Statistics$.html) 는 Pearson의 카이 제곱 테스트를 실행하는 방법을 제공한다. 다음 예제에서는 가설 검정을 실행하고 해석하는 방법을 보여 줍니다.
  
{% include_example scala/org/apache/spark/examples/mllib/HypothesisTestingExample.scala %}
</div>

<div data-lang="java" markdown="1">
  
[`Statistics`](api/java/org/apache/spark/mllib/stat/Statistics.html) Pearson의 카이 제곱 검정을 실행하는 방법을 제공합니다. 다음 예제에서는 가설 검정을 실행하고 해석하는 방법을 보여 줍니다.

API에 대한 자세한 내용은 [`ChiSqTestResult` Java docs](api/java/org/apache/spark/mllib/stat/test/ChiSqTestResult.html) 를 참조하십시오.

{% include_example java/org/apache/spark/examples/mllib/JavaHypothesisTestingExample.java %}
</div>

<div data-lang="python" markdown="1">
  
[`Statistics`](api/python/reference/api/pyspark.mllib.stat.Statistics.html) 는 Pearson의 카이 제곱 검정을 실행하는 방법을 제공합니다. 다음 예제에서는 가설 검정을 실행하고 해석하는 방법을 보여 줍니다.

[`Statistics` Python docs](api/python/reference/api/pyspark.mllib.stat.Statistics.html) 에서 API에 대한 자세한 내용을 확인하십시오.

{% include_example python/mllib/hypothesis_testing_example.py %}
</div>

</div>

또한 'spark.mllib'은 확률 분포의 동일성에 대한 콜모고로프-스미르노프(KS) 검정의 1-샘플 양방향 구현을 제공한다. 이론적인 분포(현재 정규 분포에 대해서만 지원됨)와 그 매개변수, 또는 주어진 이론적 분포에 따라 누적 분포를 계산하는 함수를 제공함으로써, 사용자는 그들의 표본이 그 분포에서 추출되었다는 귀무 가설을 테스트할 수 있다. 사용자가 정규 분포에 대해 테스트하지만('distName="norm")' 분포 매개 변수를 제공하지 않는 경우 테스트가 표준 정규 분포로 초기화되고 적절한 메시지를 기록합니다.

<div class="codetabs">
<div data-lang="scala" markdown="1">
  
[`Statistics`](api/scala/org/apache/spark/mllib/stat/Statistics$.html) p는 다음에 대한 방법을 제공한다.
1-표본, 양측 콜모고로프-스미르노프 검정을 실행합니다. 다음 예제에서는 가설 검정을 실행하고 해석하는 방법을 보여 줍니다.
  
API에 대한 자세한 내용은 [`Statistics` Scala docs](api/scala/org/apache/spark/mllib/stat/Statistics$.html) 를 참조하십시오.

{% include_example scala/org/apache/spark/examples/mllib/HypothesisTestingKolmogorovSmirnovTestExample.scala %}
</div>

<div data-lang="java" markdown="1">
  
[`Statistics`](api/java/org/apache/spark/mllib/stat/Statistics.html) 는 1-표본, 양측면 콜모고로프-스미르노프 검정을 실행하는 방법을 제공합니다. 다음 예제에서는 가설 검정을 실행하고 해석하는 방법을 보여 줍니다.

API에 대한 자세한 내용은 [`Statistics` Java docs](api/java/org/apache/spark/mllib/stat/Statistics.html) 를 참조하십시오.

{% include_example java/org/apache/spark/examples/mllib/JavaHypothesisTestingKolmogorovSmirnovTestExample.java %}
</div>

<div data-lang="python" markdown="1">
  
[`Statistics`](api/python/reference/api/pyspark.mllib.stat.Statistics.html) 표본, 양측 콜모고로프-스미르노프 검정을 실행하는 방법을 제공합니다. 다음 예제에서는 가설 검정을 실행하고 해석하는 방법을 보여 줍니다.

API에 대한 자세한 내용은 [`Statistics` Python docs](api/python/reference/api/pyspark.mllib.stat.Statistics.html) 를 참조하십시오.

{% include_example python/mllib/hypothesis_testing_kolmogorov_smirnov_test_example.py %}
</div>
</div>

### Streaming Significance Testing
`spark.mllib` provides online implementations of some tests to support use cases
like A/B testing. These tests may be performed on a Spark Streaming
`DStream[(Boolean, Double)]` where the first element of each tuple
indicates control group (`false`) or treatment group (`true`) and the
second element is the value of an observation.
  
### 스트리밍 중요도 테스트
`spark.mllib`은 A/B 테스트와 같은 사용 사례를 지원하기 위해 일부 테스트의 온라인 구현을 제공합니다. 이러한 테스트는 스파크 스트리밍 `DStream[(Boolean, Double)]`에서 수행할 수 있으며, 여기서 각 튜플의 첫 번째 요소는 제어군('false') 또는 처리군('true')을 나타내고 두 번째 요소는 관찰값이다.

스트리밍 중요도 테스트는 다음 매개 변수를 지원합니다:

* `peacePeriod` - 스트림에서 새로움 효과를 줄이는 데 사용되는 초기 데이터 지점 수입니다
* `windowSize` - 가설 검정을 수행할 과거 배치의 수입니다. '0'으로 설정하면 모든 이전 배치를 사용하여 누적 처리가 수행됩니다.


<div class="codetabs">
<div data-lang="scala" markdown="1">
[`StreamingTest`](api/scala/org/apache/spark/mllib/stat/test/StreamingTest.html)
에서는 스트리밍 가설 검정을 제공합니다.

{% include_example scala/org/apache/spark/examples/mllib/StreamingTestExample.scala %}
</div>

<div data-lang="java" markdown="1">
[`StreamingTest`](api/java/index.html#org.apache.spark.mllib.stat.test.StreamingTest)
에서는 스트리밍 가설 검정을 제공합니다.

{% include_example java/org/apache/spark/examples/mllib/JavaStreamingTestExample.java %}
</div>
</div>

## 랜덤 데이터 생성

랜덤 데이터 생성은 랜덤화된 알고리즘, 프로토타이핑 및 성능 테스트에 유용합니다. 'spark.mllib'은 주어진 분포에서 도출된 i.i.d. 값(균일 분포, 표준 정규 분포 또는 포아송 분포)으로 무작위 RDD 생성을 지원한다.

<div class="codetabs">
<div data-lang="scala" markdown="1">
  
[`RandomRDDs`](api/scala/org/apache/spark/mllib/random/RandomRDDs$.html) 는 무작위 이중 RDD 또는 벡터 RDD를 생성하는 공장 방법을 제공한다.
다음 예제는 무작위 이중 RDD를 생성하는데, 그 값은 표준 정규 분포 'N(0, 1)'을 따른 다음 'N(1, 4)'에 매핑한다.

API에 대한 자세한 내용은 [`RandomRDDs` Scala docs](api/scala/org/apache/spark/mllib/random/RandomRDDs$.html) 를 참조하세요.

{% highlight scala %}
import org.apache.spark.SparkContext
import org.apache.spark.mllib.random.RandomRDDs._

val sc: SparkContext = ...

// 다음에서 추출한 백만 개의 I.i.d. 값을 포함하는 임의의 이중 RDD를 생성합니다.
// 표준 정규 분포 'N(0, 1)'은 10개의 파티션에 고르게 분포되어 있다.
val u = normalRDD(sc, 1000000L, 10)
// Apply a transform to get a random double RDD following `N(1, 4)`.
val v = u.map(x => 1.0 + 2.0 * x)
{% endhighlight %}
</div>

<div data-lang="java" markdown="1">
  
[`RandomRDDs`](api/java/index.html#org.apache.spark.mllib.random.RandomRDDs) 는 랜덤 이중 RDD 또는 벡터 RDD를 생성하는 공장 방법을 제공한다.
다음 예제는 무작위 이중 RDD를 생성하는데, 그 값은 표준 정규 분포 'N(0, 1)'을 따른 다음 'N(1, 4)'에 매핑한다.

API에 대한 자세한 내용은 [`RandomRDDs` Java docs](api/java/org/apache/spark/mllib/random/RandomRDDs) 를 참조하세요.

{% highlight java %}
import org.apache.spark.SparkContext;
import org.apache.spark.api.JavaDoubleRDD;
import static org.apache.spark.mllib.random.RandomRDDs.*;

JavaSparkContext jsc = ...

// 다음에서 추출한 백만 개의 I.i.d. 값을 포함하는 임의의 이중 RDD를 생성합니다.
// 표준 정규 분포 'N(0, 1)'은 10개의 파티션에 고르게 분포되어 있다.
JavaDoubleRDD u = normalJavaRDD(jsc, 1000000L, 10);
// Apply a transform to get a random double RDD following `N(1, 4)`.
JavaDoubleRDD v = u.mapToDouble(x -> 1.0 + 2.0 * x);
{% endhighlight %}
</div>

<div data-lang="python" markdown="1">
  
[`RandomRDDs`](api/python/reference/api/pyspark.mllib.random.RandomRDDs.html) 는 랜덤 이중 RDD 또는 벡터 RDD를 생성하는 공장 방법을 제공한다.
다음 예제는 무작위 이중 RDD를 생성하는데, 그 값은 표준 정규 분포 'N(0, 1)'을 따른 다음 'N(1, 4)'에 매핑한다.

API에 대한 자세한 내용은 [`RandomRDDs` Python docs](api/python/reference/api/pyspark.mllib.random.RandomRDDs.html) 를 참조하세요.

{% highlight python %}
from pyspark.mllib.random import RandomRDDs

sc = ... # SparkContext

# 다음에서 추출한 백만 개의 I.i.d. 값을 포함하는 임의의 이중 RDD를 생성합니다.
# 표준 정규 분포 'N(0, 1)'은 10개의 파티션에 고르게 분포되어 있다.
u = RandomRDDs.normalRDD(sc, 1000000L, 10)
# 변환을 적용하여 'N(1, 4)' 뒤에 오는 임의의 이중 RDD를 구한다.
v = u.map(lambda x: 1.0 + 2.0 * x)
{% endhighlight %}
</div>
</div>

## 커널 밀도 추정

[Kernel density estimation](https://en.wikipedia.org/wiki/Kernel_density_estimation) 은 관측된 표본이 추출된 특정 분포에 대한 가정을 요구하지 않고 경험적 확률 분포를 시각화하는 데 유용한 기술이다. 주어진 점 집합에서 평가되는 랜덤 변수의 확률 밀도 함수의 추정치를 계산합니다. 특정 지점에서 경험적 분포의 PDF를 각 표본을 중심으로 한 정규 분포의 PDF 평균으로 표현함으로써 이 추정치를 달성할 수 있습니다.

<div class="codetabs">

<div data-lang="scala" markdown="1">
  
[`KernelDensity`](api/scala/org/apache/spark/mllib/stat/KernelDensity.html)는 샘플의 RDD에서 커널 밀도 추정치를 계산하는 방법을 제공합니다. 다음 예에서는 이 작업을 수행하는 방법을 보여 줍니다.

API에 대한 자세한 내용은 [`KernelDensity` Scala docs](api/scala/org/apache/spark/mllib/stat/KernelDensity.html)를 참조하세요.

{% include_example scala/org/apache/spark/examples/mllib/KernelDensityEstimationExample.scala %}
</div>

<div data-lang="java" markdown="1">
  
[`KernelDensity`](api/java/index.html#org.apache.spark.mllib.stat.KernelDensity) 는 샘플의 RDD에서 커널 밀도 추정치를 계산하는 방법을 제공합니다. 다음 예에서는 이 작업을 수행하는 방법을 보여 줍니다.

API에 대한 자세한 내용은 [`KernelDensity` Java docs](api/java/org/apache/spark/mllib/stat/KernelDensity.html) 를 참조하세요.

{% include_example java/org/apache/spark/examples/mllib/JavaKernelDensityEstimationExample.java %}
</div>

<div data-lang="python" markdown="1">
  
[`KernelDensity`](api/python/reference/api/pyspark.mllib.stat.KernelDensity.html) 는 샘플의 RDD에서 커널 밀도 추정치를 계산하는 방법을 제공한다. 다음 예에서는 이 작업을 수행하는 방법을 보여 줍니다.

API에 대한 자세한 내용은 [`KernelDensity` Python docs](api/python/reference/api/pyspark.mllib.stat.KernelDensity.html) 를 참조하세요.

{% include_example python/mllib/kernel_density_estimation_example.py %}
</div>

</div>
