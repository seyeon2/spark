---
레이아웃: 전역
제목: 분류와 회귀- RDD 기반 API
보여지는 제목: 분류와 회귀- RDD 기반 API
라이센스: |
   하나 이상의 기여자 라이센스 계약에 따라 ASF(Apache Software Foundation)에 라이센스가 부여됩니다. 저작권 소유에 대한 추가 정보는 본 작업과 함께 배포된 NOTICE 파일을 참조하십시오. ASF는 Apache License 버전 2.0("License")에 따라 이 파일에 라이센스를 부여하며, 라이센스를 준수하지 않는 한 이 파일을 사용할 수 없습니다. 귀하는 http://www.apache.org/licenses/LICENSE-2.0에서 라이센스 복사본을 얻을 수 있습니다. 관련 법률에서 요구하거나 서면으로 동의하지 않는 한 라이센스에 따라 배포되는 소프트웨어는 명시적 또는 묵시적 보증 또는 조건 없이 "있는 그대로" 배포됩니다. 라이센스 아래의 사용 권한 및 제한 사항을 관리하는 특정 언어는 라이센스를 참조하십시오.
   
---

`spark.mllib` 패키지는 다음을 위한 다양한 메소드를 지원합니다. 
[binary classification](http://en.wikipedia.org/wiki/Binary_classification),
[multiclass
classification](http://en.wikipedia.org/wiki/Multiclass_classification), 그리고
[regression analysis](http://en.wikipedia.org/wiki/Regression_analysis). 아래 표에는 각 문제 유형에 대해 지원되는 알고리즘이 요약되어 있습니다.

<table class="table">
  <thead>
    <tr><th>문제 유형</th><th>지원되는 방법</th></tr>
  </thead>
  <tbody>
    <tr>
      <td>이진 분류</td><td>linear SVMs, logistic regression, decision trees, random forests, gradient-boosted trees, naive Bayes</td>
    </tr>
    <tr>
      <td>다중 클래스 분류</td><td>logistic regression, decision trees, random forests, naive Bayes</td>
    </tr>
    <tr>
      <td>회귀</td><td>linear least squares, Lasso, ridge regression, decision trees, random forests, gradient-boosted trees, isotonic regression</td>
    </tr>
  </tbody>
</table>

이 방법들을 자세히 알고 싶으면 아래를 참조하세요:

* [Linear models](mllib-linear-methods.html)
  * [classification (SVMs, logistic regression)](mllib-linear-methods.html#classification)
  * [linear regression (least squares, Lasso, ridge)](mllib-linear-methods.html#linear-least-squares-lasso-and-ridge-regression)
* [Decision trees](mllib-decision-tree.html)
* [Ensembles of decision trees](mllib-ensembles.html)
  * [random forests](mllib-ensembles.html#random-forests)
  * [gradient-boosted trees](mllib-ensembles.html#gradient-boosted-trees-gbts)
* [Naive Bayes](mllib-naive-bayes.html)
* [Isotonic regression](mllib-isotonic-regression.html)
