# Apache Spark

스파크는 대규모 데이터 처리를 위한 통합 분석 엔진입니다. 스칼라, 자바, 파이썬, R로 된 고급 API를 제공하며, 데이터 분석을 위한 일반적인 연산 그래프를 지원하는 최적화된 엔진을 제공합니다. 또한 SQL 및 DataFrames용 Spark SQL, 판다 워크로드용 Panda API, 머신러닝용 MLlib, 그래프 처리를 위한 GraphX, 스트림 처리를 위한 구조화된 스트리밍을 포함한 다양한 고급 도구 세트를 지원합니다.

<https://spark.apache.org/>

[![GitHub Action Build](https://github.com/apache/spark/actions/workflows/build_and_test.yml/badge.svg?branch=master&event=push)](https://github.com/apache/spark/actions/workflows/build_and_test.yml?query=branch%3Amaster+event%3Apush)
[![Jenkins Build](https://amplab.cs.berkeley.edu/jenkins/job/spark-master-test-sbt-hadoop-3.2/badge/icon)](https://amplab.cs.berkeley.edu/jenkins/job/spark-master-test-sbt-hadoop-3.2)
[![AppVeyor Build](https://img.shields.io/appveyor/ci/ApacheSoftwareFoundation/spark/master.svg?style=plastic&logo=appveyor)](https://ci.appveyor.com/project/ApacheSoftwareFoundation/spark)
[![PySpark Coverage](https://codecov.io/gh/apache/spark/branch/master/graph/badge.svg)](https://codecov.io/gh/apache/spark)


## 온라인 문서

프로그래밍 가이드를 포함한 최신 스파크 설명서는 [project web page](https://spark.apache.org/documentation.html) 에서 확인할 수 있습니다.
이 README 파일에는 기본 설정 지침만 포함되어 있습니다.

## Spark 빌드

Spark는 [Apache Maven](https://maven.apache.org/) 을 사용하여 구축됩니다.
Spark 및 해당 예제 프로그램을 빌드하려면 다음을 실행합니다:

    ./build/mvn -DskipTests clean package

(사전 빌드된 패키지를 다운로드한 경우에는 이 작업을 수행할 필요가 없습니다.)

자세한 문서는 프로젝트 사이트 ["Building Spark"](https://spark.apache.org/docs/latest/building-spark.html) 에서 확인할 수 있습니다.

IDE를 사용한 Spark 개발에 대한 정보를 포함한 일반적인 개발 팁은 ["Useful Developer Tools"](https://spark.apache.org/developer-tools.html) 를 참조하십시오.

## 대화형 Scala Shell

스파크를 사용하는 가장 쉬운 방법은 Scala shell을 사용하는 것입니다:

    ./bin/spark-shell

1,000,000,000을 반환하는 다음 명령어를 실행해 보세요:

    scala> spark.range(1000 * 1000 * 1000).count()

## 대화형 Python Shell

대안으로, 파이썬을 선호하는 경우 Python shell을 사용할 수 있습니다:

    ./bin/pyspark

1,000,000,000을 반환하는 다음 명령어를 실행해 보세요:

    >>> spark.range(1000 * 1000 * 1000).count()

## 예제 프로그램

스파크에는 예제 디렉터리에 여러 `examples` 프로그램도 함께 제공된다.
둘 중 하나를 실행하려면 `./bin/run-example <class> [params]` 을 사용하세요. 예를 들면:

    ./bin/run-example SparkPi

에서 Pi 예제를 로컬로 실행합니다.

예를 실행할 때 클러스터에 예제를 제출할 때 MASTER 환경 변수를 설정할 수 있습니다. 
이것은 mesos:// 또는 spark:// URL이고, YARN에서 실행하기 위한 "yarn", 그리고 하나의 스레드로 로컬로 실행하려면 "local" , 또는 "local[N]" 은 N개의 스레드로 로컬로 실행됩니다. 클래스가 `examples`' 패키지에 있는 경우 단축된 클래스 이름을 사용할 수도 있습니다. 예시:

    MASTER=spark://host:7077 ./bin/run-example SparkPi

대부분의 예제 프로그램 츨력은 매개 변수가 제공되지 않을 때 도움이 됩니다.

## 테스트 실행

먼저 테스트하려면 [building Spark](#building-spark) 가 필요합니다.
스파크가 제작되면 다음을 사용하여 테스트를 실행할 수 있습니다:

    ./dev/run-tests

다음 방법에 대한 지침을 참조하십시오.
[run tests for a module, or individual tests](https://spark.apache.org/developer-tools.html#individual-tests).

또한 Kubernetes 통합 테스트도 있습니다. resource-managers/kubernetes/integration-tests/README.md 를 참조하세요.

## 하둡 버전에 관하여

Spark는 Hadoop 코어 라이브러리를 사용하여 HDFS 및 기타 Hadoop 지원 스토리지 시스템과 통신합니다. 프로토콜이 Hadoop의 다른 버전에서 변경되었으므로 클러스터가 실행되는 동일한 버전에 대해 Spark를 빌드해야 합니다.

특정 Hive 및 Hive Sreveftserver 배포를 위한 빌드를 포함하여 Hadoop의 특정 배포를 위한 빌드에 대한 자세한 지침은
["Specifying the Hadoop Version and Enabling YARN"](https://spark.apache.org/docs/latest/building-spark.html#specifying-the-hadoop-version-and-enabling-yarn) 에서 빌드 문서를 참조하십시오..

## 구성

Spark 구성 방법에 대한 개요는 온라인 설명서의 [Configuration Guide](https://spark.apache.org/docs/latest/configuration.html) 를 참조하십시오.

## 기여

프로젝트 참여를 시작하는 방법에 대한 자세한 내용은 [Contribution to Spark guide](https://spark.apache.org/contributing.html) 를 참조하십시오.
