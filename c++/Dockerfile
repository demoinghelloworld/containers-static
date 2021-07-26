FROM registry.access.redhat.com/ubi7/ubi as build
RUN yum-config-manager --enable rhel-7-server-optional-rpms
RUN yum -y install gcc-c++ glibc-static libstdc++-static git && yum clean all
RUN mkdir -p /app /build
WORKDIR /build
RUN git clone https://github.com/demoinghelloworld/languages.git
WORKDIR /build/languages/c++
RUN g++ -o hello hello.cpp -static

FROM scratch
COPY --from=build /build/languages/c++/hello ./hello
CMD ["/hello"]
