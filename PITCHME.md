# Monitoring Overview

Monitoring in a container app world

---

## Definitions & examples
- Monitoring vs Management |
- Infrastructure monitoring
   - Nagios, APM AppDynamics, DataDog |
- Application performance monitoring 
   - CA APM, AppDynamis, Dynatrace 

Note:
Many combine IT and APM - or could
Missing is active management - or more precisly done with other tools
Alerting - what about anomaly detection 
Many are on-premise, more and more are moving to SaaS

---

## Definitions & examples (cont)
- Uptime monitoring 
   - Pingdom |
- Network monitoring
   - Munin |
- SLA
   - CA APM, FreshTrack

Note:
Many combine IT and APM - or could
Missing is active management - or more precisly done with other tools
Alerting - what about anomaly detection 
Many are on-premise, more and more are moving to SaaS

---

## Logging
   - Sumo, Splunk, Elastic Stack

Note:
Should logging and monitoring be separate?  When debugging you probably require both...

---

## Whitebox
### inside container monitoring
- instrumenting your processes
   - snmp, JMX

Note:
This is an interesting topic.  Many of these violate the single process best practice from 12 Factor apps.
Great for debugging.
Could use image layers - more dependencies, more potential vulnerabilites, what happens when your WB client needs updating?
Choose as minimal a client as you can...

---

## Backbox
- Leveraging your orchestration environment

Note:
What we will focus on today
Using some common tools you can achive a lot of what you ned to meet your SLA - which resorting to whitebox


---

## Sysdig
- Linux kernel instrumentation
- ["strace + tcpdump + htop + iftop + lsof + ...awesome sauce"](https://github.com/draios/sysdig)
- fantastic debugging tool
- [Architecture Overview](https://sysdig.com/blog/sysdig-vs-dtrace-vs-strace-a-technical-discussion/)
- [Commercial product for aggregation/display](https://sysdig.com/product/monitor/)

Note:
- trace syscalls by container, etc.
- author of WireShark

---

## Prometheus
- Collect and store time-series metrics
- Rich support for collection of infrastructure and third party metrics
- Hosted by CNCF
- Default monitoring solution for Kubernetes
- [Docker plans to integrate](https://github.com/moby/moby/issues/27307)

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
- Blackbox monitoring
- Need additional debugging your app?
   - Logging
   - Whitebox

Note: 
Just remember what we mentioned earlier

