FROM golang:1.16-alpine AS build

RUN mkdir /app

COPY . /app

WORKDIR /app
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o docker-go .


FROM scratch

COPY --from=build  /app/docker-go /

EXPOSE 8080
CMD [ "/docker-go" ]
