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

Except redirect/move to `/opt/openises/avl/traccar.xml` instead.

Configure `traccar.xml` by following Traccar's [documentation](https://www.traccar.org/configuration-file/). To use Traccar data in Tickets, you must run Traccar using a SQL DB. Follow [their instructions](https://www.traccar.org/mysql/) for using SQL instead of H2.

Change domains and passwords in `docker-compose.yml`.

Remember that this `docker-compose` is for demonstration only. Do not commit secrets and passwords to public locations, and disable database administration tools if you don't need to use them.

For production deployments, use of configuration management tools that gaurantee idempotency such as with Ansible playbooks is strongly recommended. Your configuration management should sync files as needed with correct file/directory permissions, and when an existing install is recognized:

* disable or remove `install.php`,
* write-protect `incs/`,
* and especially `incs/mysql.inc.php`.

Default accounts after fresh installations:

```
Tickets: admin/admin
Tickets: guest/guest
Traccar: admin/admin
```
