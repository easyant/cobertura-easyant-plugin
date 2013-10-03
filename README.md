# Documentation :: cobertura by org.apache.easyant.plugins

# Description

This modules provides code coverage integration based on cobertura
	
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
|cobertura:init||||
|cobertura:instrument|||cobertura:init,abstract-compile:compile,abstract-test:init|
|cobertura:run|generates code coverage report||cobertura:instrument|

## Imported module

|organisation|module|revision|Import type|prefix|
|------------|------|--------|-----------|------|
|org.apache.easyant.plugins|abstract-test|0.10|import||
|org.apache.easyant.plugins|abstract-compile|0.9|import||

## Module parameters

### Properties

|property|description|required|default value|
|--------|-----------|--------|-------------|
|cobertura.src.dir|directory containing main sources (used for reports)|false|${src.main.java}|
|test.run.fork|Run the tests in a separate VM. (true/false)|false|true|
|javac.debug.mode|javac debug mode, true or false|false|true|
|net.sourceforge.cobertura.datafile||false||
|target.reports|base directory for reports|false|${target}/reports|
|target.coverage.reports|base directory where coverage reports will be generated|false|${target.reports}/coverage|
|cobertura.exclude.classes.regex|Exclude regex pattern to ignore files to be instrumented|false|.*\.Test.*|
|cobertura.instrumented.classes.dir|Specify the output directory for the instrumented classes|false|${target}/coverage|
|cobertura.datafile|Specify the name of the file to use for storing the metadata about your classes. This is a single file containing serialized Java classes. It contains information about the names of classes in your project, their method names, line numbers, etc. It will be updated as your tests are run, and will be referenced by the Cobertura reporting command.|false|${cobertura.instrumented.classes.dir}/cobertura.ser|
|cobertura.include.classes.regex|Include regex pattern to select files you want to be instrumented|false|.*|

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

