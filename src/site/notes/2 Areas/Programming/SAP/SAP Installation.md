---
{"dg-publish":true,"permalink":"/2-areas/programming/sap/sap-installation/","created":"2025-09-14T21:37:30.743+07:00","updated":"2025-09-14T21:41:33.011+07:00"}
---

## Installation
To host SAP on VM please follow the following steps:
- https://www.googlecloudcommunity.com/gc/Developer-Tools/Install-ABAP-Platform-Trial-2022-on-Google-Cloud-Platform-and/m-p/813482
- Check for the installation scripts at: https://github.com/google-cloud-abap/abap-cloud-trial-2022-gcp/blob/main/create_vm_with_docker.sh
- Run docker using these parameters:

``` 
sudo docker run \
  --stop-timeout 3600 \
  --name a4h \
  -h vhcala4hci \
  -p 3200:3200 \
  -p 3300:3300 \
  -p 8443:8443 \
  -p 30213:30213 \
  -p 50000:50000 \
  -p 50001:50001 \
  --sysctl kernel.shmmni=32768 \
  sapse/abap-cloud-developer-trial:ABAPTRIAL_2022_SP01 \
  -skip-limits-check \
  --agree-to-sap-license
```

sysctl kernel.shmmni=32768 is to increase the containers memory for 32 gb
- Get license from https://go.support.sap.com/minisap/#/minisap
- Check for the information's about the docker images at : https://hub.docker.com/r/sapse/abap-cloud-developer-trial
