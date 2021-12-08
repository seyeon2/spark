---
레이아웃: 전역
제목: PMML 모델 내보내기 - RDD 기반 API
타이틀: PMML 모델 내보내기 - RDD 기반 API
라이센스: |
  하나 이상의 ASF(Apache Software Foundation)에 라이센스 부여
  기여자 라이센스 계약. 다음에 배포된 NOTICE 파일을 참조하십시오.
  저작권 소유권 관련 추가 정보를 위한 작업입니다.
  ASF는 Apache License 버전 2.0에 따라 이 파일의 라이센스를 사용자에게 부여합니다.
  ("라이센스"); 다음 사항을 준수하지 않는 한 이 파일을 사용할 수 없습니다.
  면허증. 라이센스 사본은 다음 주소에서 얻을 수 있습니다.

  http://www.apache.org/licenses/LICENSE-2.0

  관련 법률이 요구하거나 서면으로 합의하지 않는 한 소프트웨어
  라이센스에 따라 배포되며 "있는 그대로" 배포됩니다.
  명시적 또는 묵시적으로 어떠한 종류의 보증이나 조건도 없습니다.
  사용 권한을 관리하는 특정 언어에 대해서는 라이센스를 참조하십시오.
  사용권에 따른 제한.
---

* Table of contents
{:toc}

## spark.mlib 지원 모델

spark.mllib은 예측 모델 마크업 언어로 모델 내보내기를 지원합니다. ([PMML](http://en.wikipedia.org/wiki/Predictive_Model_Markup_Language)).

아래 표는 PMML로 내보낼 수 있는 'spark.mlib' 모델과 동등한 PMML 모델을 요약한 것입니다.

<table class="table">
  <thead>
    <tr><th>spark.mllib model</th><th>PMML model</th></tr>
  </thead>
  <tbody>
    <tr>
      <td>KMeansModel</td><td>ClusteringModel</td>
    </tr>    
    <tr>
      <td>LinearRegressionModel</td><td>RegressionModel (functionName="regression")</td>
    </tr>
    <tr>
      <td>RidgeRegressionModel</td><td>RegressionModel (functionName="regression")</td>
    </tr>
    <tr>
      <td>LassoModel</td><td>RegressionModel (functionName="regression")</td>
    </tr>
    <tr>
      <td>SVMModel</td><td>RegressionModel (functionName="classification" normalizationMethod="none")</td>
    </tr>
    <tr>
      <td>Binary LogisticRegressionModel</td><td>RegressionModel (functionName="classification" normalizationMethod="logit")</td>
    </tr>
  </tbody>
</table>

## Examples
<div class="codetabs">

<div data-lang="scala" markdown="1">
지원되는 'model'을(를) PMML로 내보내려면 'model.toPMML'을(를) 호출하십시오.

PMML 모델을 문자열('model.toPMML')로 내보낼 뿐만 아니라 PMML 모델을 다른 형식으로 내보낼 수도 있습니다.

Api에 대한 자세한 내용은 [`KMeans` Scala docs](api/scala/org/apache/spark/mllib/clustering/KMeans.html) 및 [`Vectors` Scala docs](api/scala/org/apache/spark/mllib/linalg/Vectors$.html) 를 참조하십시오

다음은 KMeansModel을 빌드하고 PMML 형식으로 인쇄하는 전체 예:
{% include_example scala/org/apache/spark/examples/mllib/PMMLModelExportExample.scala %}

지원되지 않는 모델의 경우, `.toPMML` 함수 또는 `IllegalArgumentException` 예외가 발생할 것입니다.

</div>

</div>
