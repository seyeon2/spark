---
레이아웃: 전역
제목: 네이비 베이즈 - RDD 기반 API
타이틀: 네이브 베이즈 - RDD 기반 API
라이센스: |
  하나 이상의 기여자 라이센스 계약에 따라 ASF(Apache Software Foundation)에 라이센스가 부여됩니다. 저작권 소유에 대한 추가 정보는 본 작업과 함께 배포된 NOTICE 파일을 참조하십시오. ASF는 Apache License 버전 2.0("License")에 따라 이 파일에 라이센스를 부여하며, 라이센스를 준수하지 않는 한 이 파일을 사용할 수 없습니다. 귀하는 http://www.apache.org/licenses/LICENSE-2.0에서 라이센스 복사본을 얻을 수 있습니다. 관련 법률에서 요구하거나 서면으로 동의하지 않는 한 라이센스에 따라 배포되는 소프트웨어는 명시적 또는 묵시적 보증 또는 조건 없이 "있는 그대로" 배포됩니다. 라이센스 아래의 사용 권한 및 제한 사항을 관리하는 특정 언어는 라이센스를 참조하십시오.
---

[Naive Bayes](http://en.wikipedia.org/wiki/Naive_Bayes_classifier) 는 모든 기능 쌍 간의 독립성을 가정한 간단한 다중 클래스 분류 알고리즘이다. 나이브 베이즈는 매우 효율적으로 훈련될 수 있다. 훈련 데이터에 대한 단일 패스 내에서 주어진 각 형상의 조건부 확률 분포를 계산한 다음 베이즈의 정리를 적용하여 주어진 관측치의 조건부 확률 분포를 계산하고 예측에 사용한다.

`spark.mllib`은 [multinomial naive
Bayes](http://en.wikipedia.org/wiki/Naive_Bayes_classifier#Multinomial_naive_Bayes)
와 [Bernoulli naive Bayes](http://nlp.stanford.edu/IR-book/html/htmledition/the-bernoulli-model-1.html)를 지원한다.
이러한 모델은 일반적으로 [document classification](http://nlp.stanford.edu/IR-book/html/htmledition/naive-bayes-text-classification-1.html)에 사용됩니다.
이 문맥에서, 각 관측치는 문서이고, 각 특징은 (다항식 순진한 베이에서) 용어의 빈도 또는 (베르누이 순진한 베이에서) 용어의 발견 여부를 나타내는 0 또는 1의 값을 나타내는 항을 나타냅니다. 형상 값은 음수가 아니어야 합니다. 모델 유형은 선택적 매개변수인 "다항" 또는 "베르누이"를 기본값으로 사용하여 선택됩니다.
[Additive smoothing](http://en.wikipedia.org/wiki/Lidstone_smoothing)은 매개 변수 $\lambda$ (default to $1.0$) 를 설정하여 사용할 수 있습니다. 문서 분류를 위해 입력 특징 벡터는 일반적으로 희소하며 희소성을 이용하기 위해 희소 벡터가 입력으로 제공되어야 합니다. 교육 데이터는 한 번만 사용되므로 캐시할 필요가 없습니다.

## 예시

<div class="codetabs">
<div data-lang="scala" markdown="1">

[NaiveBayes](api/scala/org/apache/spark/mllib/classification/NaiveBayes$.html) 는 다항식 순진한 베이스를 구현합니다. 
[LabeledPoint](api/scala/org/apache/spark/mllib/regression/LabeledPoint.html) 의 RDD와 선택적 평활 파라미터인 lambda'를 입력으로 사용하고(기본 모델 유형 파라미터는 "다항식"임), [NaiveBayesModel](api/scala/org/apache/spark/mllib/classification/NaiveBayesModel.html)을 출력합니다

[`NaiveBayes` Scala docs](api/scala/org/apache/spark/mllib/classification/NaiveBayes$.html) 및 [`NaiveBayesModel` Scala docs](api/scala/org/apache/spark/mllib/classification/NaiveBayesModel.html) 을 참조하십시오.

{% include_example scala/org/apache/spark/examples/mllib/NaiveBayesExample.scala %}
</div>
<div data-lang="java" markdown="1">

[NaiveBayes](api/java/org/apache/spark/mllib/classification/NaiveBayes.html) 는 다항식 순진한 베이스를 구현합니다. 
[LabeledPoint](api/java/org/apache/spark/mllib/regression/LabeledPoint.html) 의 스칼라 RDD와 선택적으로 매개 변수 'lambda'를 입력으로 평활하고 평가 및 예측에 사용할 수 있는 [NaiveBayesModel](api/java/org/apache/spark/mllib/classification/NaiveBayesModel.html) 을 출력합니다.

[`NaiveBayes` Java docs](api/java/org/apache/spark/mllib/classification/NaiveBayes.html) 및 [`NaiveBayesModel` Java docs](api/java/org/apache/spark/mllib/classification/NaiveBayesModel.html) 을 참조하십시오.

{% include_example java/org/apache/spark/examples/mllib/JavaNaiveBayesExample.java %}
</div>
<div data-lang="python" markdown="1">

[NaiveBayes](api/python/reference/api/pyspark.mllib.classification.NaiveBayes.html) 는 다항식 순진한 베이스를 구현합니다.  
[LabeledPoint](api/python/reference/api/pyspark.mllib.regression.LabeledPoint.html) 의 스칼라 RDD와 선택적으로 매개 변수 'lambda'를 입력으로 평활하고 평가 및 예측에 사용할 수 있는 [NaiveBayesModel](api/python/reference/api/pyspark.mllib.classification.NaiveBayesModel.html)을 출력합니다.

Python API는 아직 모델 저장/로드 기능을 지원하지 않지만 향후 지원될 예정입니다.

API에 대한 자세한 내용은 [`NaiveBayes` Python docs](api/python/reference/api/pyspark.mllib.classification.NaiveBayes.html) 및 [`NaiveBayesModel` Python docs](api/python/reference/api/pyspark.mllib.classification.NaiveBayesModel.html) 을 참조하십시오.

  {% include_example python/mllib/naive_bayes_example.py %}
</div>
</div>
