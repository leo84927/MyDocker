FROM logstash:8.15.3

USER root
RUN rm -f /usr/share/logstash/pipeline/logstash.conf
RUN curl -L -o /usr/share/logstash/lib/mysql-connector-java-5.1.47.jar https://repo1.maven.org/maven2/mysql/mysql-connector-java/5.1.47/mysql-connector-java-5.1.47.jar

RUN logstash-plugin install logstash-input-beats