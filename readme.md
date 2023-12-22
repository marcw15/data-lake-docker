stopped after setting up "JDBC Controller postgres"

tbc

---
commands
>docker-compose up -> start containers
>docker ps --all ->  list all containers, both running and stopped
>docker stats -> display a live stream of container resource usage statistics
>docker container ls -> alternative way to list running containers, e.g.:
>>docker container ls  

<table>
  <tr>
    <th>CONTAINER ID</th>
    <th>IMAGE</th>
    <th>COMMAND</th>
    <th>CREATED</th>
    <th>STATUS</th>
    <th>PORTS</th>
    <th>NAMES</th>
  </tr>
  <tr>
    <td>fcdb20988876</td>
    <td>apache/nifi-registry:1.15.0</td>
    <td>"/bin/sh -c ${NIFI_R…"</td>
    <td>19 minutes ago</td>
    <td>Up 8 minutes (healthy)</td>
    <td>0.0.0.0:18080->18080/tcp, 18443/tcp</td>
    <td>registry_container</td>
  </tr>
  <tr>
    <td>a6b21ca46117</td>
    <td>bitnami/minio:2021</td>
    <td>"/opt/bitnami/script…"</td>
    <td>19 minutes ago</td>
    <td>Up 7 minutes (healthy)</td>
    <td>0.0.0.0:9000-9001->9000-9001/tcp</td>
    <td>minio_container</td>
  </tr>
  <tr>
    <td>b567ffeb2487</td>
    <td>puckel/docker-airflow:1.10.9</td>
    <td>"/entrypoint.sh webs…"</td>
    <td>19 minutes ago</td>
    <td>Up 7 minutes (healthy)</td>
    <td>5555/tcp, 8793/tcp, 0.0.0.0:8085->8080/tcp</td>
    <td>airflow_container</td>
  </tr>
  <tr>
    <td>82e0d7e7533f</td>
    <td>apache/nifi:1.14.0</td>
    <td>"../scripts/start.sh"</td>
    <td>19 minutes ago</td>
    <td>Up 7 minutes (healthy)</td>
    <td>8000/tcp, 8443/tcp, 10000/tcp, 0.0.0.0:8091->8080/tcp</td>
    <td>nifi_container</td>
  </tr>
  <tr>
    <td>5d171514a51a</td>
    <td>bitnami/zookeeper:3.7.0</td>
    <td>"/opt/bitnami/script…"</td>
    <td>19 minutes ago</td>
    <td>Up 7 minutes</td>
    <td>2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp</td>
    <td>zookeeper_container</td>
  </tr>
  <tr>
    <td>05da4455d948</td>
    <td>dpage/pgadmin4:6.1</td>
    <td>"/entrypoint.sh"</td>
    <td>19 minutes ago</td>
    <td>Up 8 minutes (unhealthy)</td>
    <td>443/tcp, 0.0.0.0:5050->80/tcp</td>
    <td>pgadmin_container</td>
  </tr>
  <tr>
    <td>71516d78c311</td>
    <td>postgres:14-bullseye</td>
    <td>"docker-entrypoint.s…"</td>
    <td>19 minutes ago</td>
    <td>Up 7 minutes (healthy)</td>
    <td>0.0.0.0:5432->5432/tcp</td>
    <td>postgres_container</td>
  </tr>
</table>

docker inspect 71516d78c311 -> provides detailed information about a specific container, e.g. 71516d78c311

all services/ urls
Apache NiFi — http://localhost:8091/nifi/ (to process and distribute data)
Apache NiFi Registry — http://localhost:18080/nifi-registry/ (to store, manage and version control NiFi resources)
Apache Airflow — http://localhost:8085/admin/ (to programmatically author, schedule and monitor workflows)
pgAdmin — http://localhost:5050/browser/ (as db)
minIO — http://localhost:9000/ (as a locally hosted, S3-compatible object-storage)
Docker for hosting


thx to https://github.com/CribberSix?tab=repositories