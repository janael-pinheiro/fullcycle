FROM golang:1.21-alpine3.18 AS build-stage

WORKDIR /app

COPY go.mod .
RUN go mod download

COPY . .

RUN CGO_ENABLED=0 GOOS=linux go build -C ./cmd/ -o /hello

FROM scratch

WORKDIR /

COPY --from=build-stage /hello /hello

ENTRYPOINT [ "./hello" ]