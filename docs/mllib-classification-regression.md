---
레이아웃: 전역
제목: 분류와 회귀- RDD 기반 API
보여지는 제목: 분류와 회귀- RDD 기반 API
라이센스: |
  하나 이상의 ASF(Apache Software Foundation)에 라이센스 부여 기여자 라이센스 계약. 다음에 배포된 NOTICE 파일을 참조하십시오. 저작권 소유권 관련 추가 정보를 위한 작업입니다. ASF는 Apache License 버전 2.0에 따라 이 파일의 라이센스를 사용자에게 부여합니다. ("라이센스"); 다음 사항을 준수하지 않는 한 이 파일을 사용할 수 없습니다. 면허증. 라이센스 사본은 다음 주소에서 얻을 수 있습니다. http://www.apache.org/licenses/LICENSE-2.0 관련 법률이 요구하거나 서면으로 합의하지 않는 한 소프트웨어 라이센스에 따라 배포되며 "있는 그대로" 배포됩니다. 명시적 또는 묵시적으로 어떠한 종류의 보증이나 조건도 없습니다. 사용 권한을 관리하는 특정 언어에 대해서는 라이센스를 참조하십시오. 사용권에 따른 제한.
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

More details for these methods can be found here:

* [Linear models](mllib-linear-methods.html)
  * [classification (SVMs, logistic regression)](mllib-linear-methods.html#classification)
  * [linear regression (least squares, Lasso, ridge)](mllib-linear-methods.html#linear-least-squares-lasso-and-ridge-regression)
* [Decision trees](mllib-decision-tree.html)
* [Ensembles of decision trees](mllib-ensembles.html)
  * [random forests](mllib-ensembles.html#random-forests)
  * [gradient-boosted trees](mllib-ensembles.html#gradient-boosted-trees-gbts)
* [Naive Bayes](mllib-naive-bayes.html)
* [Isotonic regression](mllib-isotonic-regression.html)
