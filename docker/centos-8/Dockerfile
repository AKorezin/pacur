FROM centos:8
MAINTAINER Pacur <contact@pacur.org>

RUN yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm

RUN yum -y install yum-utils
RUN yum-config-manager --enable AppStream
RUN yum-config-manager --enable PowerTools

RUN yum -y upgrade
RUN yum -y groupinstall 'Development Tools'
RUN yum -y install tar expect rpm-build rpm-sign openssl createrepo rsync make automake gcc wget zip git bzr mercurial

RUN wget https://dl.google.com/go/go1.13.6.linux-amd64.tar.gz
RUN echo "a1bc06deb070155c4f67c579f896a45eeda5a8fa54f35ba233304074c4abbbbd go1.13.6.linux-amd64.tar.gz" | sha256sum -c -
RUN tar -C /usr/local -xf go1.13.6.linux-amd64.tar.gz
RUN rm -f go1.13.6.linux-amd64.tar.gz

ENV GOPATH /go
ENV PATH /usr/local/go/bin:$PATH:/go/bin

RUN go get github.com/pacur/pacur

ENTRYPOINT ["pacur"]
CMD ["build", "centos-8"]