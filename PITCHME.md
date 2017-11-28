# Monitoring Overview

Monitoring in a container app world

---

## Roll your own items
   - snmp, JMS
    - downsides
     - sprawl and doing this.  Maybe in a base layer?

---

## Traditional
### (mostly JVM)
   - APM
   - New Relic
   - AppDynamics

---

## logging
   - Sumo, Splunk, Elastic Stack,

---

## metrics
   - whitebox vs blackbox

---

# Sysdig

---

## Prometheus
- Collect and store time-series metrics
- Rich support for collection of infrastructure and third party metrics
- Hosted by CNCF
- Default monitoring solution for Kubernetes
- Docker plans to integrate (https://github.com/moby/moby/issues/27307)

---

## Prometheus "Ecosystem" Overview
- Prometheus Server
- Alert Manager
- Exporters
- Client Libraries
- Display

---

![DockerPrometheus](assets/prometheus-on-docker.png)

---

## Prometheus Server
- Stores time-series data by metric name and key/value labels
  - query language for analyzing stored data
- "Scrapes" (pulls) data from targets
  - static configuration or discovery
- Triggers alerts via configurable rules

Note:
Configurable discovery for DNS, EC2, Consul catalog API, GCE, Kubernetes, Azure and many others

---

### Third Party Data
- Exporters
  - Node Exporter: hardware and OS Metrics for *NIX
  - WMI: Windows metrics
  - CAdvisor: container metrics
  - Other monitoring: JMX, SNMP, AWS CloudWatch
  - many others
- Directly exposed metrics
  - Kubernetes
  - Etcd
  - FreeBSD Kernel
  - many others

Note:

- Databases: MySQL, memcached, MongoDB, MSSQL, PostgreSQL, ...
- Messaging: Kafka, RabbitMQ, Beanstalkd, NATS, ...
- Storage: Ceph, Gluster, Hadoop HDFS, Lustre, ...
- HTTP: Apache, HAProxy, Nginx, ...
- APIs: AWS, DigitalOcean, DockerHub, DockerCloud, GitHub, Rancher, ...
- Other monitoring systems: AWS CloudWatch, JMX, SNMP, ...

---

## Client Libraries
- add custom metrics at key points in your implementation
- "push gateway" can be used to cache metrics from ephemeral or batch jobs that may not be present when data is pulled

---

## Data Display
- Grafana
  - built-in support to query Prometheus
  - define dashboards to display data from Prometheus

---

## Resources
- [Prometheus Docs](https://prometheus.io/docs/introduction/overview/)
- [Prometheus with Docker](https://stefanprodan.com/2016/a-monitoring-solution-for-docker-hosts-containers-and-containerized-services/)

---

# Demo

---

## What to do with all that data?

- Freshtracks
- Prelert (Part of elastic)

---

## Key Takeaways or what's right for my project?
- Are you using it for debugging your app?
   - Logging
   - Whitebox
- Are you using it for SLA of your app?
   - Blackbox
   - If using a JVM language
      - Add whitebox

