FROM daocloud.io/java:8
ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH

ENV TOMCAT_MAJOR 8
ENV TOMCAT_VERSION 8.0.50
ENV TOMCAT_TGZ_URL http://mirrors.shu.edu.cn/apache/tomcat/tomcat-${TOMCAT_MAJOR}/v${TOMCAT_VERSION}/bin
RUN wget -qO- "${TOMCAT_TGZ_URL}/apache-tomcat-${TOMCAT_VERSION}.tar.gz" | tar xvz -C /usr/local
RUN ln -s /usr/local/apache-tomcat-${TOMCAT_VERSION} ${CATALINA_HOME}

EXPOSE 8080

CMD ["/usr/local/tomcat/bin/catalina.sh","run"]
