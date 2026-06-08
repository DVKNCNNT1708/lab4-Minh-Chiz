# Docker Evidence – Lab 04

## Team

- Team name: 
- Service:
- Image tag:

## 1. Build evidence

Command:

```bash
docker build -t <image-name>:<tag> .
```

![alt text](<Screenshot 2026-06-08 204414.png>)

PS D:\Bài Tập\lab4-Minh-Chiz> docker build -t fit4110/iot-ingestion:lab04 .
[+] Building 3.5s (19/19) FINISHED         docker:desktop-linux
 => [internal] load build definition from Dockerfile       0.0s
 => => transferring dockerfile: 1.12kB                     0.0s
 => resolve image config for docker-image://docker.io/doc  1.2s
 => [auth] docker/dockerfile:pull token for registry-1.do  0.0s
 => CACHED docker-image://docker.io/docker/dockerfile:1.7  0.0s
 => => resolve docker.io/docker/dockerfile:1.7@sha256:a57  0.0s
 => [internal] load metadata for docker.io/library/python  1.0s
 => [auth] library/python:pull token for registry-1.docke  0.0s
 => [internal] load .dockerignore                          0.0s
 => => transferring context: 233B                          0.0s
 => [builder 1/5] FROM docker.io/library/python:3.11-slim  0.0s
 => => resolve docker.io/library/python:3.11-slim@sha256:  0.0s
 => [internal] load build context                          0.0s
 => => transferring context: 8.08kB                        0.0s
 => CACHED [runtime 2/6] WORKDIR /app                      0.0s
 => CACHED [runtime 3/6] RUN addgroup --system appgroup    0.0s
 => CACHED [builder 2/5] WORKDIR /build                    0.0s
 => CACHED [builder 3/5] RUN python -m venv /opt/venv      0.0s
 => CACHED [builder 4/5] COPY requirements.txt .           0.0s
 => CACHED [builder 5/5] RUN /opt/venv/bin/pip install --  0.0s
 => CACHED [runtime 4/6] COPY --from=builder /opt/venv /o  0.0s
 => [runtime 5/6] COPY src/ ./src/                         0.0s
 => [runtime 6/6] RUN chown -R appuser:appgroup /app       0.3s
 => exporting to image                                     0.3s
 => => exporting layers                                    0.1s
 => => exporting manifest sha256:ed3c72d9e7cf291f3eacb9bb  0.0s
 => => exporting config sha256:e632e7bfb9dbaf90b1aa930b09  0.0s
 => => exporting attestation manifest sha256:dccf1248ecf7  0.0s
 => => exporting manifest list sha256:5f2c5b65a8726478172  0.0s
 => => naming to docker.io/fit4110/iot-ingestion:lab04     0.0s
 => => unpacking to docker.io/fit4110/iot-ingestion:lab04  0.0s

## 2. Run evidence

Command:

```bash
docker run --rm -p 8000:8000 --env-file .env.example <image-name>:<tag>
```

![alt text](<Screenshot 2026-06-08 210133.png>)

PS D:\Bài Tập\lab4-Minh-Chiz> docker run --rm --name fit4110-iot-lab04 -p 8000:8000 --env-file .env.example fit4110/iot-ingestion:lab04
INFO:     Started server process [7]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://0.0.0.0:8000 (Press CTRL+C to quit)
INFO:     127.0.0.1:37274 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:58496 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:44132 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:59416 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:45854 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:41662 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:35522 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:60844 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:41712 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:47532 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:46732 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:57202 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:46832 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:54150 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:38238 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:46894 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:60812 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:46460 - "GET /health HTTP/1.1" 200 OK
INFO:     172.17.0.1:44008 - "GET /health HTTP/1.1" 200 OK
INFO:     172.17.0.1:44008 - "POST /readings HTTP/1.1" 201 Created
INFO:     172.17.0.1:44008 - "GET /readings/latest?device_id=ESP32-LAB-A01&limit=5 HTTP/1.1" 200 OK
INFO:     172.17.0.1:44008 - "GET /readings/R-20260608-0001 HTTP/1.1" 200 OK
INFO:     172.17.0.1:44008 - "POST /readings HTTP/1.1" 401 Unauthorized
INFO:     172.17.0.1:44008 - "POST /readings HTTP/1.1" 401 Unauthorized
INFO:     172.17.0.1:44008 - "POST /readings HTTP/1.1" 422 Unprocessable Entity
INFO:     172.17.0.1:44008 - "POST /readings HTTP/1.1" 422 Unprocessable Entity
INFO:     172.17.0.1:44008 - "POST /readings HTTP/1.1" 201 Created
INFO:     172.17.0.1:44008 - "POST /readings HTTP/1.1" 422 Unprocessable Entity
INFO:     127.0.0.1:47232 - "GET /health HTTP/1.1" 200 OK
INFO:     172.17.0.1:44008 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:35434 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:53660 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:43182 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:51060 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:51744 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:34132 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:54024 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:38910 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:36018 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:55560 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:53550 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:44848 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:33622 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:58728 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:60094 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:46928 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:50420 - "GET /health HTTP/1.1" 200 OK
INFO:     127.0.0.1:55162 - "GET /health HTTP/1.1" 200 OK

## 3. Healthcheck evidence

Command:

```bash
curl http://localhost:8000/health
```

Result:

```json
{
  "status": "ok"
}
```
![alt text](<Screenshot 2026-06-08 204451.png>)

PS D:\Bài Tập\lab4-Minh-Chiz> curl.exe http://localhost:8000/health
{"status":"ok","service":"iot-ingestion","version":"0.4.0"}

## 4. Newman evidence

Command:

```bash
npm run test:local
```

Report path:

```text
reports/newman-lab04-local.html
reports/newman-lab04-local.xml
```
![alt text](<Screenshot 2026-06-08 210445.png>)
![alt text](<Screenshot 2026-06-08 210457.png>)

PS D:\Bài Tập\lab4-Minh-Chiz> npm run test:local

> fit4110-lab04-docker-packaging@0.1.0 test:local
> newman run postman/collections/FIT4110_lab04_iot_docker.postman_collection.json -e postman/environments/FIT4110_lab04_local.postman_environment.json -r cli,junit,htmlextra --reporter-junit-export reports/newman-lab04-local.xml --reporter-htmlextra-export reports/newman-lab04-local.html

(node:1164) [DEP0176] DeprecationWarning: fs.F_OK is deprecated, use fs.constants.F_OK instead
(Use `node --trace-deprecation ...` to show where the warning was created)
newman

FIT4110 Lab04 IoT Docker Verification

□ 01_Functional
└ GET health returns 200
  GET http://localhost:8000/health [200 OK, 184B, 24ms]
  √  Status code is 200
  √  Response has status ok
  √  Response has service name and version

└ POST valid temperature reading returns 201
  POST http://localhost:8000/readings [201 Created, 271B, 7ms]
  √  Status code is 201
  √  Response follows created-reading schema
  √  Response device_id matches request

└ GET latest readings returns items array
  GET http://localhost:8000/readings/latest?device_id=ESP32-LAB-A01&limit=5 [200 OK, 332B, 4ms]
  √  Status code is 200
  √  Response has items array

└ GET reading by saved reading_id returns 200
  GET http://localhost:8000/readings/R-20260608-0001 [200 OK, 320B, 4ms]
  √  Status code is 200
  √  Response reading_id matches saved variable

□ 02_Auth
└ POST reading without token returns 401
  POST http://localhost:8000/readings [401 Unauthorized, 302B, 3ms]
  √  Missing token returns 401

└ POST reading with wrong token returns 401
  POST http://localhost:8000/readings [401 Unauthorized, 294B, 5ms]
  √  Wrong token returns 401

□ 03_Negative
└ POST reading missing device_id returns validation error
  POST http://localhost:8000/readings [422 Unprocessable Entity, 320B, 3ms]
  √  Missing required field returns 422

└ POST reading with value as string returns validation error
  POST http://localhost:8000/readings [422 Unprocessable Entity, 368B, 3ms]
  √  Wrong data type returns 422

□ 04_Boundary_Reliability
└ POST boundary temperature 80 is accepted with warning
  POST http://localhost:8000/readings [201 Created, 300B, 4ms]
  √  Boundary value 80 returns 201
  √  High temperature response includes warning header

└ POST boundary temperature 81 is rejected
  POST http://localhost:8000/readings [422 Unprocessable Entity, 342B, 3ms]
  √  Boundary value 81 returns 422

└ GET health responds under 1000ms on local/container
  GET http://localhost:8000/health [200 OK, 184B, 2ms]
  √  Response time is below 1000ms
  √  Health endpoint is reachable

┌─────────────────────────┬─────────────────┬─────────────────┐
│                         │        executed │          failed │
├─────────────────────────┼─────────────────┼─────────────────┤
│              iterations │               1 │               0 │
├─────────────────────────┼─────────────────┼─────────────────┤
│                requests │              11 │               0 │
├─────────────────────────┼─────────────────┼─────────────────┤
│            test-scripts │              11 │               0 │
├─────────────────────────┼─────────────────┼─────────────────┤
│      prerequest-scripts │               0 │               0 │
├─────────────────────────┼─────────────────┼─────────────────┤
│              assertions │              19 │               0 │
├─────────────────────────┴─────────────────┴─────────────────┤
│ total run duration: 1030ms                                  │
├─────────────────────────────────────────────────────────────┤
│ total data received: 1.68kB (approx)                        │
├─────────────────────────────────────────────────────────────┤
│ average response time: 5ms [min: 2ms, max: 24ms, s.d.: 5ms] │
└─────────────────────────────────────────────────────────────┘

## 5. Notes

- Known limitation:
- Next step for Lab 05:
