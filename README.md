# Confluence
Experience and notes
# Python notes
## REQUIREMENTS.TXT
### Basic commands
|Command|Descriprion|
|:-----------------------------:|-----------------------------------|
|Install requrments.txt|`python -m pip install -r pathToFile\requirements.txt`|
|Grpc generation|`python -m grpc_tools.protoc -I protobufs  --python_out=. --grpc_python_out=. recommendations.proto`|

## GIT
### Basic commands
|Command|Descriprion|
|:-----------------------------:|-----------------------------------|
||``|
||``|

## DOCKER
### Basic commands
|Command|Descriprion|
|:-----------------------------:|-----------------------------------|
|Build image|`docker build . -f path/to_service/Dockerfile -t recommendations`|
|Run image|`docker run -p 127.0.0.1:50051:50051/tcp recommendations`|
|Запущенные контейнеры|`docker ps`|
|Остановить контейнер|`docker stop container_name`|
|Выполнить команду снаружи докер контейнера|`docker exec <Enter container ID> cat /etc/nginx/conf.d/default.conf`|

### Docker file example
```
FROM python

RUN mkdir /service
COPY protobufs/ /service/protobufs/
COPY recommendations/ /service/recommendations/
WORKDIR /service/recommendations
RUN python -m pip install --upgrade pip
RUN python -m pip install -r requirements.txt
RUN python -m grpc_tools.protoc -I ../protobufs --python_out=. \
           --grpc_python_out=. ../protobufs/recommendations.proto

EXPOSE 50051
ENTRYPOINT [ "python", "recommendations.py" ]
```
