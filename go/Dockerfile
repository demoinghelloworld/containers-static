FROM registry.access.redhat.com/ubi7/ubi as build
RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN yum -y install golang git && yum clean all
RUN mkdir -p /app /build
WORKDIR /build
RUN git clone https://github.com/demoinghelloworld/languages.git
WORKDIR /build/languages/go
RUN go build -ldflags="-extldflags=-static" -o hello hello.go

FROM scratch
COPY --from=build /build/languages/go/hello ./hello
CMD ["/hello"]
