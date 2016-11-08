This is an example of a sink for Cloud Foundry. Currently, this is manually pushed (`cf push`) using the python buildpack.

## How to deploy with Spring Cloud Data Flow Cloud Foundry

```
jar cvf pysink.jar cusumer.py requirement.txt Procfile
```

Upload `pylog.jar` to some repostory such as http server.

In Spring Cloud Data Flow Shell,

```
app register --name pylog --type sink --uri https://github.com/making/python-spring-cloud-stream/raw/master/examples/cloudfoundry/spring_cloud_stream_sink_cloudfoundry/pylog.jar
```

```
stream create --name pydemo --definition "time | pylog"
```

```
stream deploy --name pydemo --properties "app.pylog.spring.cloud.deployer.cloudfoundry.buildpack=python_buildpack"
```


