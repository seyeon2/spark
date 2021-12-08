---
license: |
  
  하나 이상의 기여자 라이센스 계약에 따라 ASF(Apache Software Foundation)에 라이센스가 부여됩니다. 저작권 소유에 대한 추가 정보는 본 작업과 함께 배포된 NOTICE 파일을 참조하십시오.  ASF는 Apache License 버전 2.0("License")에 따라 이 파일에 라이센스를 부여하며, 라이센스를 준수하지 않는 한 이 파일을 사용할 수 없습니다. 귀하는 http://www.apache.org/licenses/LICENSE-2.0에서 라이센스 복사본을 얻을 수 있습니다. 관련 법률에서 요구하거나 서면으로 동의하지 않는 한 라이센스에 따라 배포되는 소프트웨어는 명시적 또는 묵시적 보증 또는 조건 없이 "있는 그대로" 배포됩니다. 라이센스 아래의 사용 권한 및 제한 사항을 관리하는 특정 언어는 라이센스를 참조하십시오.
  
---

Spark 문서에 오신 것을 환영합니다! 

이 문서에서는 Spark 소스 코드와 함께 스파크 문서를 탐색하고 작성하는 방법을 안내합니다. https://spark.apache.org/documentation.html에서 Spark 버전 릴리스 관련 설명서를 찾을 수도 있습니다.

문서를 일반 텍스트로 보거나 문서를 직접 작성하는 방법에 대해 자세히 알아보십시오. 왜 직접 작성하나요? 당신이 현재 수정기호 제어에서 체크아웃한 Spark 버전에 해당하는 문서를 가질 수 있기 때문입니다.

## 전제조건

스파크 문서 빌드는 스칼라, 자바, 파이썬, R 및 SQL로 HTML 문서와 API 문서를 빌드하기 위해 많은 도구를 사용한다.

당신은 [Ruby](https://www.ruby-lang.org/en/documentation/installation/) 와
[Python](https://docs.python.org/2/using/unix.html#getting-and-installing-the-latest-version-of-python)을 설치해야 합니다. `bundle` 명령을 사용할 수 있는지 확인하고, 해당 명령이 포함된 Gem을 설치합니다:

```sh
$ sudo gem install bundler
```

이후 모든 필수 ruby 종속성을 번들러를 통해 `docs/` 디렉토리에서 설치할 수 있습니다:

```sh
$ cd docs
$ bundle install
```

참고: Ruby 1.9와 Ruby 2.0을 모두 사용하는 시스템에 있는 경우 gem2.0으로 교체해야 할 수 있습니다.

### R 문서

R 문서를 생성하려면 [Pandoc 설치](https://pandoc.org/installing.html)을 설치하고 다음 라이브러리를 설치해야 합니다.

```sh
$ sudo Rscript -e 'install.packages(c("knitr", "devtools", "testthat", "rmarkdown"), repos="https://cloud.r-project.org/")'
$ sudo Rscript -e 'devtools::install_version("roxygen2", version = "7.1.1", repos="https://cloud.r-project.org/")'
```
참고: 다른 버전의 Roxygen2는 SparkR 설명서 생성에서 작동할 수 있지만 `$SPARK_HOME/R/pkg/DESCRIPTION`의 `RoxygenNote`  필드는 7.1.1이며 버전이 일치하지 않을 경우 업데이트됩니다.

### API 문서

어떤 언어에 대한 API 문서를 생성하려면 다음 라이브러리를 설치해야 합니다.

<!--
TODO(SPARK-32407): Sphinx 3.1+ does not correctly index nested classes.
See also https://github.com/sphinx-doc/sphinx/issues/7551.

TODO(SPARK-35375): Jinja2 3.0.0+ causes error when building with Sphinx.
See also https://issues.apache.org/jira/browse/SPARK-35375.
-->

```sh
$ sudo pip install 'sphinx<3.1.0' mkdocs numpy pydata_sphinx_theme ipython nbsphinx numpydoc sphinx-plotly-directive 'jinja2<3.0.0'
```

## HTML 문서 생성

우리는 문서가 소스 코드와 함께 발전하고 개정 제어(현재 git)에 의해 캡처될 수 있도록 하기 위해 스파크 문서를 소스의 일부로 포함한다. 이렇게 하면 체크아웃하거나 다운로드한 버전 또는 릴리스에 관계없이 코드에는 관련 설명서의 버전이 자동으로 포함됩니다.

이 디렉토리에는 ".md" 접미사와 함께 마크다운을 사용하여 포맷된 텍스트 파일이 있습니다. 당신이 원하면 그 파일들을 직접 읽을 수 있습니다. `index.md`부터 시작하세요.

`docs/` 디렉토리에서 `bundle exec jekyll build`을 실행하여 컴파일합니다. Jekyll을 사용하여 컴파일하면 `index.html`뿐만 아니라 컴파일된 나머지 파일을 포함하는 `_site`라는 디렉토리가 생성됩니다.

```sh
$ cd docs
$ bundle exec jekyll build
```

다음과 같이 기본 Jekyll 빌드를 수정할 수 있습니다.

```sh
# API 문서 생성 건너뛰기(시간 소요)

$ SKIP_API=1 bundle exec jekyll build

# 로컬 포트 4000에서 콘텐츠 제공
$ bundle exec jekyll serve --watch

# 라이브 페이지에서 사용되는 추가 기능으로 사이트 구축

$ PRODUCTION=1 bundle exec jekyll build
```

## API 문서 (Scaladoc, Javadoc, Sphinx, roxygen2, MkDocs)

당신은 `$SPARK_HOME` 디렉토리에서 `./build/sbt unidoc`을 실행하여 Spark scaladoc 과 javadoc만을 빌드할 수 있습니다. 

마찬가지로 `$SPARK_HOME/python/docs` 디렉토리에서 `make html`을 실행하여 PySpark 문서만 작성할 수 있습니다. 설명서는 `__init__.py`에 public으로 나열된 클래스에 대해서만 생성됩니다. SparkR 문서는 `$SPARK_HOME/R/create-docs.sh`를 실행하여 작성할 수 있습니다. 그리고 SQL 문서는 [building Spark](https://github.com/apache/spark#building-spark)를 먼저 구축한 후 `$SPARK_HOME/sql/create-docs.sh`를 실행하여 작성할 수 있습니다.

`docs` 디렉토리에서 `bundle exec jekyll build`를 실행하면 다양한 스파크 하위 프로젝트의 scaladoc 과 javadoc 통해 `docs` 디렉토리(이후 `_site` 디렉토리에도 복사됩니다. 사이트를 구축하기 전에 jekyll 플러그인을 사용하여 `./build/sbt unidoc` 을 실행합니다. 만약 당신이 실행하지 않은 경우 [Unidoc](https://github.com/sbt/sbt-unidoc))을 사용하여 모든 scaladoc 및 javadoc 을 생성하므로 시간이 걸릴 수 있습니다. jekyll 플러그인은 또한 [Spinkx](http://sphinx-doc.org/),를 사용하여 PySpark 문서를 생성하고 [roxygen2](https://cran.r-project.org/web/packages/roxygen2/index.html)를 사용하는 SparkR 문서와 [MkDocs](https://www.mkdocs.org/))를 사용하는 SQL 문서를 생성합니다.

참고: Scala, Java, Python, R 및 SQL API 문서를 빌드하고 복사하는 단계를 건너뛰려면 `SKIP_API=1 bundle exec jekyll build`를 실행하십시오. 또한 `SKIP_SCALADOC=1`, `SKIP_PYTHONDOC=1`, `SKIP_RDOC=1` 및 `SKIP_SQLDOC=1` 을 사용하여 해당 언어의 한 단계를 건너뛸 수 있습니다. `SKIP_SCALADOC`는 Scala와 Java 문서를 모두 건너뛰는 것을 나타냅니다.
