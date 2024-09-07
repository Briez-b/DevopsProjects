###########################
#First stage
###########################
FROM ubuntu AS FirstBuild
COPY . .

RUN apt-get update && apt-get install -y golang-go
ENV GO111MODULE=off
RUN CGO_ENABLED=0 go build -o /app .
###########################
# Second stage
###########################
# Most lightweight build
From scratch
# Copy compiled files to this build
COPY --from=FirstBuild /app /app

ENTRYPOINT ["/app"]