
# bereavement-support-payment-performance-tests


Performance test suite for the `BSP API`, using [performance-test-runner](https://github.com/hmrc/performance-test-runner) under the hood.

## Pre-requisites

### Services

To run performance tests locally, execute

```bash
sm2 --start TFC_PAYMENTS_ALL --wait 100
```

Using the `--wait 100` argument ensures a health check is run on all the services started as part of the profile. `100` refers to the given number of seconds to wait for services to pass health checks.


### Logging

The default log level for all HTTP requests is set to `WARN`. Configure [logback.xml](src/test/resources/logback.xml) to update this if required.

### WARNING :warning:

Do **NOT** run a full performance test against staging from your local machine. Please [implement a new performance test job](https://confluence.tools.tax.service.gov.uk/display/DTRG/Practical+guide+to+performance+testing+a+digital+service#Practicalguidetoperformancetestingadigitalservice-SettingupabuildonJenkinstorunagainsttheStagingenvironment) and execute your job from the dashboard in [Performance Jenkins](https://performance.tools.staging.tax.service.gov.uk).

## Tests

Run smoke test (locally) as follows:

```bash
sbt -Dperftest.runSmokeTest=true -DrunLocal=true gatling:test
```

Run full performance test (locally) as follows:

```bash
sbt -DrunLocal=true gatling:test
```

Run smoke test (staging) as follows:

```bash
sbt -Dperftest.runSmokeTest=true -DrunLocal=false gatling:test
```

## Scalafmt

Check all project files are formatted as expected as follows:

```bash
sbt scalafmtCheckAll scalafmtCheck
```

Format `*.sbt` and `project/*.scala` files as follows:

```bash
sbt scalafmtSbt
```

Format all project files as follows:

```bash
sbt scalafmtAll
```
### License

This code is open source software licensed under the [Apache 2.0 License]("http://www.apache.org/licenses/LICENSE-2.0.html").