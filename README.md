# Documentation :: cobertura by org.apache.easyant.plugins

# Description

# Example

```xml
<ea:plugin organisation="org.apache.easyant.plugins" module="cobertura" revision="0.1"/>
```
Organisation attribute is optional. If not specified default one will be used.

```xml
<ea:plugin module="cobertura" revision="0.1"/>
```

## Available targets

|target name|description|extension point|depends|
|-----------|-----------|---------------|-------|
|/skip-tests|skip tests|||
|abstract-test:compute-test-sets|compute the set of test cases to run||abstract-test:test-ready|
|cobertura:init||||
|abstract-test:init|||abstract-provisioning:provisioning|
|cobertura:instrument|||cobertura:init,abstract-compile:compile,abstract-test:init|
|cobertura:run|||cobertura:instrument|

## Available extension points

|target name|description|depends|
|-----------|-----------|-------|
|abstract-test:test-ready|defines test requirements||
|abstract-test:integration-test-ready|defines integration-test requirements||
|abstract-provisioning:provisioning|defines provisioning step, usually it's a good place for loading libraries, populating classpath|abstract-provisioning:provisioning-ready|
|abstract-compile:compile-ready|defines the requirements to compile. It's the good place if you want to process or generate sources|abstract-provisioning:provisioning|
|abstract-provisioning:provisioning-ready|defines provisioning requirements||
|abstract-test:integration-test-run|defines integration-test step|abstract-test:integration-test-ready|
|abstract-test:test-run|defines tests step|abstract-test:test-ready|
|abstract-compile:compile|defines the compile step|abstract-compile:compile-ready|

## Imported module

|organisation|module|revision|Import type|prefix|
|------------|------|--------|-----------|------|
|org.apache.easyant.plugins|abstract-provisioning|0.9|null||
|org.apache.easyant.plugins|abstract-compile|0.9|null||
|org.apache.easyant.plugins|abstract-test|0.9|null||

## Module parameters

### Properties

|property|description|required|default value|
|--------|-----------|--------|-------------|
|skip.test||false||
|test.run.includes.pattern|Pattern describing class files included in test run|false|**/*|
|test.run.failonerror|specify if the build should be stopped when tests are failed. Typically this property should be set to false in continuous environmnent systems|false|true|
|src.test.integration.resources|directory for integration test resources (configuration files, data files, etc)|false|${basedir}/src/integration-test/resources|
|target.test.html|destination directory for html test report|false|${target}/test/html|
|test.mode|mode to use to execute tests: 'run' to only run tests, 'report' to generate html report|false|run|
|lib.test|directory where test libraries are picked up|false|${basedir}/lib/test|
|target.test.classes|destination directory for compiled test classes|false|${target}/test/classes|
|lib.main|directory where main libraries are picked up|false|${basedir}/lib/main|
|cobertura.src.dir|directory containing main sources (used for reports)|false|${src.main.java}|
|test.integration.run.dir|working directory for integration test process, defaults to the project basedir|false|${basedir}|
|target.test.integration.classes|destination directory for compiled integration test classes|false|${target}/integration-test/classes|
|target.reports|base directory for reports|false|${target}/reports|
|test.run.dir|working directory for unit test process, defaults to the project basedir|false|${basedir}|
|cobertura.instrumented.classes.dir|Specify the output directory for the instrumented classes|false|${target}/coverage|
|test.jar.pattern|when test.scan.path is enabled, identifies which jars should be examined for test cases|false|.*-test.jar|
|cobertura.datafile|Specify the name of the file to use for storing the metadata about your classes. This is a single file containing serialized Java classes. It contains information about the names of classes in your project, their method names, line numbers, etc. It will be updated as your tests are run, and will be referenced by the Cobertura reporting command.|false|${cobertura.instrumented.classes.dir}/cobertura.ser|
|target.test.xml|destination directory for xml test report|false|${target}/test/xml|
|target.main.classes|destination directory for compiled classes|false|${target}/main/classes|
|test.integration.run.includes.pattern|Pattern describing class files included in integration test run|false|**/*|
|skip.test.integration||false||
|src.test.resources|directory with unit test resource files (configuration files, data files, etc)|false|${basedir}/src/test/resources|
|test.integration.jar.pattern|when test.scan.path is enabled, identifies which jars should be examined for test cases|false|.*-test.jar|
|cobertura.include.classes.regex|Include regex pattern to select files you want to be instrumented|false|.*|
|test.scan.path|if true, the full test classpath will be scanned for additional test cases to run|false|false|
|test.integration.scan.path|if true, the full integration test classpath will be scanned for additional test cases to run|false|false|
|lib.provided|directory where provided libraries are picked up|false|${basedir}/lib/provided|
|test.run.excludes.pattern|Pattern describing class files excluded in test run|false||
|target|the target directory|false|target|
|target.coverage.reports|base directory where coverage reports will be generated|false|${target.reports}/coverage|
|cobertura.exclude.classes.regex|Exclude regex pattern to ignore files to be instrumented|false|.*\.Test.*|
|test.integration.run.excludes.pattern|Pattern describing class files excluded in integration test run|false||

## Ivy Configurations

|name|description|extends|visibility|deprecated|
|----|-----------|-------|----------|----------|
|default|runtime dependencies artifact can be used with this conf|[]|public||
|test|this scope indicates that the dependency is not required for normal use of the application, and is only available for the test compilation and execution phases.|[]|private||
|provided|this is much like compile, but indicates you expect the JDK or a container to provide it. It is only available on the compilation classpath, and is not transitive.|[]|public||

## Dependencies Overview

|Organisation|Module|Revision|
|------------|------|--------|
|net.sourceforge.cobertura|cobertura|1.9.4.1|

