# apache-ignite

Apache Ignite 모니터링 걸기


* 환경: K8S 1.7.16, Ignite 2.11.0
* 모니터링 솔루션: Prometheus, Grafana

1] 원하는 정보
Ignite Cache 에 존재하는 캐시당 Put, Get, Hit, Miss 등 캐싱 모니터링에 필요한 정보

2] 시도
   2-1) Ignite 가 지원하는 JmxMetricExporterSpi 사용
        - 2.8 버전 이상부터는 jmx 를 통한 매트릭을 지원은 하지만 규격에 문제가 있어서 정보수집이 안됨.

   2-2) JMX exporter sidecar 를 통한 정보 추출
        - GC, JVM 정보만 넘어올 뿐 상세한 Hit, Miss 등의 값은 구할 수 없음.

   2-3) (성공) Ignite 가 지원하는 OpenCensusMetricExporterSpi 사용
        - Ignite 에 opencensus 라이브러리를 올린다음 정보 추출

3] 방법
   3-1) ignite-opencensus lib 활성화
   3-2) opencensus, prometheus simple client 라이브러리 추가
   ------------------------
