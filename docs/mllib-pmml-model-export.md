---
레이아웃: 전역
제목: PMML 모델 내보내기 - RDD 기반 API
타이틀: PMML 모델 내보내기 - RDD 기반 API
라이센스: |
  하나 이상의 기여자 라이센스 계약에 따라 ASF(Apache Software Foundation)에 라이센스가 부여됩니다. 저작권 소유에 대한 추가 정보는 본 작업과 함께 배포된 NOTICE 파일을 참조하십시오. ASF는 Apache License 버전 2.0("License")에 따라 이 파일에 라이센스를 부여하며, 라이센스를 준수하지 않는 한 이 파일을 사용할 수 없습니다. 귀하는 http://www.apache.org/licenses/LICENSE-2.0에서 라이센스 복사본을 얻을 수 있습니다. 관련 법률에서 요구하거나 서면으로 동의하지 않는 한 라이센스에 따라 배포되는 소프트웨어는 명시적 또는 묵시적 보증 또는 조건 없이 "있는 그대로" 배포됩니다. 라이센스 아래의 사용 권한 및 제한 사항을 관리하는 특정 언어는 라이센스를 참조하십시오.
  
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
