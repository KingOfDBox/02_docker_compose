Практика 2 — Многоконтейнерный стенд на Docker Compose 
1) Создаем все необходимые файлы
2) поднимаем стенд в docker
```
serkingofdbox@DESKTOP-5S32NBH:~/tmp/lab2$ docker compose up -d --build
WARN[0000] /home/serkingofdbox/tmp/lab2/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
[+] Running 37/37
 ✔ redis Pulled                                                       41.8s
   ✔ d75b3becd998 Pull complete                                        0.1s
   ✔ 232f7549c9b0 Pull complete                                        0.1s
   ✔ c70aae7b5e0d Pull complete                                       39.2s
 ✔ adminer Pulled                                                     62.9s
   ✔ aa5a2611d454 Pull complete                                       45.9s
   ✔ fb47194af07c Pull complete                                       60.3s
   ✔ 75f4e19fb4b8 Pull complete                                        0.1s
   ✔ fc671ef6f9c8 Pull complete                                       23.7s
   ✔ 4f4fb700ef54 Pull complete                                        0.3s
   ✔ 4cb8c0d2cc28 Pull complete                                        1.9s
   ✔ c812d71d0a92 Pull complete                                        0.0s
   ✔ 1329c5084d62 Pull complete                                       23.6s
   ✔ e06f17d8d87f Pull complete                                       60.5s
   ✔ 80e636f8651f Pull complete                                       60.6s
   ✔ f413b510cd4a Pull complete                                        0.0s
   ✔ ad217014f3d0 Pull complete                                       46.1s
   ✔ 5ed107248614 Pull complete                                        0.0s
   ✔ 800a2b6306a0 Pull complete                                       60.2s
   ✔ 5500e10789f2 Pull complete                                        0.0s
   ✔ 3a418472befe Pull complete                                        0.0s
 ✔ traefik Pulled                                                     82.2s
   ✔ 2f2dc5ed6642 Pull complete                                        0.9s
   ✔ 2e42f1fa21f1 Pull complete                                       77.8s
   ✔ b7bc362d9483 Pull complete                                       10.0s
   ✔ da9db072f522 Pull complete                                        9.8s
 ✔ postgres Pulled                                                   124.2s
   ✔ cab99cec2af7 Pull complete                                        3.3s
   ✔ f2db3dd76baa Pull complete                                        2.2s
   ✔ 8e5dc03d34e5 Pull complete                                        0.7s
   ✔ 670559ed8ba9 Pull complete                                        2.2s
   ✔ b9d06b7fef7a Pull complete                                        1.8s
   ✔ ad6e868aea79 Pull complete                                        5.9s
   ✔ 1fc8985c6238 Pull complete                                        9.6s
   ✔ 5443128c2125 Pull complete                                      119.7s
   ✔ 538c669d4f94 Pull complete                                        2.6s
   ✔ a23babb82b92 Pull complete                                        3.0s
[+] Building 59.5s (14/14) FINISHED
 => [internal] load local bake definitions                             0.0s
 => => reading from stdin 491B                                         0.0s
 => [internal] load build definition from Dockerfile                   0.1s
 => => transferring dockerfile: 579B                                   0.0s
 => [internal] load metadata for docker.io/library/python:3.11-slim    0.1s
 => [internal] load .dockerignore                                      0.1s
 => => transferring context: 2B                                        0.0s
 => [builder 1/4] FROM docker.io/library/python:3.11-slim@sha256:8eb5  0.4s
 => => resolve docker.io/library/python:3.11-slim@sha256:8eb5fc663972  0.1s
 => [internal] load build context                                      0.1s
 => => transferring context: 666B                                      0.0s
 => [builder 2/4] WORKDIR /app                                         0.6s
 => [builder 3/4] COPY requirements.txt .                              0.2s
 => [stage-1 3/5] RUN useradd -m appuser && chown -R appuser /app      1.1s
 => [builder 4/4] RUN pip install --user --no-cache-dir -r requireme  49.6s
 => [stage-1 4/5] COPY --from=builder /root/.local /home/appuser/.loc  2.1s
 => [stage-1 5/5] COPY app/ app/                                       0.1s
 => exporting to image                                                 5.0s
 => => exporting layers                                                3.7s
 => => exporting manifest sha256:588852ec23e2a5e7f3c74b1cf2b960383913  0.0s
 => => exporting config sha256:a7fa727695214ba0e383921aa3cb90b5855fa7  0.0s
 => => exporting attestation manifest sha256:9481a3bb8d8de6b8afe9ee01  0.0s
 => => exporting manifest list sha256:b281747da318ac0695b4ec0d2192852  0.0s
 => => naming to docker.io/library/lab2-api:latest                     0.0s
 => => unpacking to docker.io/library/lab2-api:latest                  1.1s
 => resolving provenance for metadata file                             0.0s
[+] Running 9/9
 ✔ lab2-api                   Built                                    0.0s
 ✔ Network lab2_public        Created                                  0.1s
 ✔ Network lab2_backend       Created                                  0.0s
 ✔ Volume "lab2_pgdata"       Created                                  0.0s
 ✔ Container lab2-redis-1     Started                                  1.0s
 ✔ Container lab2-adminer-1   Started                                  1.1s
 ✔ Container lab2-traefik-1   Started                                  1.1s
 ✔ Container lab2-postgres-1  Healthy                                  6.5s
 ✔ Container lab2-api-1       Started                                  6.6s
```
3) Проверка
```
```
4) Состояние
```
serkingofdbox@DESKTOP-5S32NBH:~/tmp/lab2$ docker compose ps
WARN[0000] /home/serkingofdbox/tmp/lab2/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion
NAME              IMAGE                COMMAND                  SERVICE    CREATED          STATUS                    PORTS
lab2-adminer-1    adminer              "entrypoint.sh docke…"   adminer    17 minutes ago   Up 17 minutes             8080/tcp
lab2-api-1        lab2-api             "uvicorn app.main:ap…"   api        17 minutes ago   Up 17 minutes (healthy)   8000/tcp
lab2-postgres-1   postgres:16-alpine   "docker-entrypoint.s…"   postgres   17 minutes ago   Up 17 minutes (healthy)
lab2-redis-1      redis:7-alpine       "docker-entrypoint.s…"   redis      17 minutes ago   Up 17 minutes
lab2-traefik-1    traefik:v3.1         "/entrypoint.sh --ap…"   traefik    17 minutes ago   Up 17 minutes             0.0.0.0:80->80/tcp, [::]:80->80/tcp
```
