FROM cs2cdocker/mariadb:10.0
USER root
#ADD MariaDB-10.2.23-centos7-mips64el-backup.rpm /tmp
ADD MariaDB-10.2.23-centos7-mips64el-common.rpm /tmp
ADD MariaDB-10.2.23-centos7-mips64el-client.rpm /tmp
#ADD MariaDB-10.2.23-centos7-mips64el-connect-engine.rpm /tmp
#ADD MariaDB-10.2.23-centos7-mips64el-devel.rpm /tmp
#ADD MariaDB-10.2.23-centos7-mips64el-gssapi-server.rpm /tmp
#ADD MariaDB-10.2.23-centos7-mips64el-rocksdb-engine.rpm /tmp
ADD MariaDB-10.2.23-centos7-mips64el-server.rpm /tmp
ADD MariaDB-10.2.23-centos7-mips64el-shared.rpm /tmp
ADD MariaDB-10.2.23-centos7-mips64el-test.rpm /tmp

RUN yum remove mariadb*  MariaDB* mariadb-lib* -y

#RUN rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-backup.rpm  --nodeps \
RUN rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-common.rpm --nodeps \
&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-client.rpm  --nodeps \
#&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-connect-engine.rpm --nodeps \
#&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-devel.rpm --nodeps \
#&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-gssapi-server.rpm --nodeps \
#&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-rocksdb-engine.rpm --nodeps \
&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-server.rpm --nodeps \
&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-shared.rpm --nodeps \
&& rpm -i /tmp/MariaDB-10.2.23-centos7-mips64el-test.rpm --nodeps

RUN rm -rf /tmp/*.rpm
RUN chown -R mysql.0 /var/lib/mysql && chown -R mysql.0 /etc/my.cnf*

ADD run-mysqld /usr/bin/
ADD common.sh /usr/share/container-scripts/mysql/
#ADD 50-passwd-change.sh /usr/share/container-scripts/mysql/init/
VOLUME [/var/lib/mysql/data]
USER mysql
ENTRYPOINT ["container-entrypoint"]
CMD ["run-mysqld"]
