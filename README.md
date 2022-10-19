## EC2 User-data
```
#!/bin/bash -ex
yum -y update
yum -y install docker git
usermod -aG docker $USER
systemctl enable docker
systemctl start docker
curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
git clone https://github.com/MamNonDevOps/docker-k6-grafana-influxdb.git
```
Kiểm tra start docker service, nếu có lỗi sau xảy ra
```
Traceback (most recent call last):
  File "urllib3/connectionpool.py", line 677, in urlopen
  File "urllib3/connectionpool.py", line 392, in _make_request
  File "http/client.py", line 1277, in request
  File "http/client.py", line 1323, in _send_request
  File "http/client.py", line 1272, in endheaders
  File "http/client.py", line 1032, in _send_output
  File "http/client.py", line 972, in send
  File "docker/transport/unixconn.py", line 43, in connect
FileNotFoundError: [Errno 2] No such file or directory
```
