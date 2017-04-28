FROM registry.access.redhat.com/openshift3/jenkins-slave-base-rhel7

MAINTAINER Koray Seremet <koray@redhat.com>

LABEL com.redhat.component="skopeo" \
      name="skopeo" \
      architecture="x86_64" \
      io.k8s.display-name="Skopeo Jenkins Slave" \
      io.k8s.description="Skopeo image management tool on top of the jenkins slave base image" \
      io.openshift.tags="openshift,jenkins,slave,copy"

USER root

COPY etc/policy.json /etc/containers/

RUN yum -y --setopt=tsflags=nodocs --enablerepo=rhel-7-server-extras-rpms install skopeo && \
    yum -y clean all && \
    chown -R 1001:0 /etc/containers $HOME /usr/bin/skopeo  && \
    chmod -R g+rw /etc/containers $HOME /usr/bin/skopeo

USER 1001
