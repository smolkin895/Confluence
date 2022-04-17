# Confluence
Experience and notes
# Python notes
## REQUIRMENTS.TXT
### basic commands
|Command|Descriprion|
|:-----------------------------:|-----------------------------------|
|Install requrments.txt|`python -m pip install -r pathToFile\requirements.txt`|
|Grpc generation|`python -m grpc_tools.protoc -I protobufs  --python_out=. --grpc_python_out=. recommendations.proto`|

## GIT
### basic commands
|Command|Descriprion|
|:-----------------------------:|:-----------------------------------:|
|||
|||

# Docker File
## Docker file example
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
