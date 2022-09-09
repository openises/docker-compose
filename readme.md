Directories you must provide:

```
/opt/openises/
/opt/openises/cad-web/
/opt/openises/avl/
/opt/openises/avl/logs/
```

Files you must provide:

```
/opt/openises/cad-web/ - fill with Tickets Core
/opt/openises/avl/traccar.xml
```

A default `traccar.xml` can be generated following `traccar-docker`'s [documentation](https://hub.docker.com/r/traccar/traccar):

```
docker run \
--rm \
--entrypoint cat \
traccar/traccar:latest \
/opt/traccar/conf/traccar.xml > /var/docker/traccar/traccar.xml
```

Configure `traccar.xml` by following Traccar's [documentation](https://www.traccar.org/configuration-file/). To use Traccar data in Tickets, you must run Traccar using a SQL DB. Follow [their instructions](https://www.traccar.org/mysql/) for using SQL instead of H2.
