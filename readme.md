stopped after setting up "JDBC Controller postgres"

tbc

---
commands
docker-compose up -> start containers
docker ps --all ->  list all containers, both running and stopped
docker stats -> display a live stream of container resource usage statistics
docker container ls -> alternative way to list running containers, e.g.:
docker container ls  

CONTAINER ID   IMAGE                          COMMAND                  CREATED          STATUS                     PORTS                                                   NAMES
fcdb20988876   apache/nifi-registry:1.15.0    "/bin/sh -c ${NIFI_R…"   19 minutes ago   Up 8 minutes (healthy)     0.0.0.0:18080->18080/tcp, 18443/tcp                     registry_container
a6b21ca46117   bitnami/minio:2021             "/opt/bitnami/script…"   19 minutes ago   Up 7 minutes (healthy)     0.0.0.0:9000-9001->9000-9001/tcp                        minio_container
b567ffeb2487   puckel/docker-airflow:1.10.9   "/entrypoint.sh webs…"   19 minutes ago   Up 7 minutes (healthy)     5555/tcp, 8793/tcp, 0.0.0.0:8085->8080/tcp              airflow_container
82e0d7e7533f   apache/nifi:1.14.0             "../scripts/start.sh"    19 minutes ago   Up 7 minutes (healthy)     8000/tcp, 8443/tcp, 10000/tcp, 0.0.0.0:8091->8080/tcp   nifi_container
5d171514a51a   bitnami/zookeeper:3.7.0        "/opt/bitnami/script…"   19 minutes ago   Up 7 minutes               2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp                  zookeeper_container
05da4455d948   dpage/pgadmin4:6.1             "/entrypoint.sh"         19 minutes ago   Up 8 minutes (unhealthy)   443/tcp, 0.0.0.0:5050->80/tcp                           pgadmin_container
71516d78c311   postgres:14-bullseye           "docker-entrypoint.s…"   19 minutes ago   Up 7 minutes (healthy)     0.0.0.0:5432->5432/tcp                                  postgres_container

docker inspect 71516d78c311 -> provides detailed information about a specific container, e.g. 71516d78c311

all services/ urls
Apache NiFi — http://localhost:8091/nifi/ (to process and distribute data)
Apache NiFi Registry — http://localhost:18080/nifi-registry/ (to store, manage and version control NiFi resources)
Apache Airflow — http://localhost:8085/admin/ (to programmatically author, schedule and monitor workflows)
pgAdmin — http://localhost:5050/browser/ (as db)
minIO — http://localhost:9000/ (as a locally hosted, S3-compatible object-storage)
Docker for hosting


thx to https://github.com/CribberSix?tab=repositories