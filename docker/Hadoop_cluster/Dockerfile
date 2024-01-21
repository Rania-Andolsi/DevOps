# Use a base image with Java and Hadoop pre-installed
FROM openjdk:8-jdk

# Set Hadoop version
ENV HADOOP_VERSION 3.3.1

# Download and extract Hadoop
RUN curl -O https://archive.apache.org/dist/hadoop/common/hadoop-${HADOOP_VERSION}/hadoop-${HADOOP_VERSION}.tar.gz && \
    tar -xzvf hadoop-${HADOOP_VERSION}.tar.gz -C /opt/ && \
    rm hadoop-${HADOOP_VERSION}.tar.gz

# Set environment variables
ENV HADOOP_HOME /opt/hadoop-${HADOOP_VERSION}
ENV PATH $HADOOP_HOME/bin:$PATH

# Hadoop configurations
COPY core-site.xml $HADOOP_HOME/etc/hadoop/core-site.xml
COPY hdfs-site.xml $HADOOP_HOME/etc/hadoop/hdfs-site.xml
# Add any additional configuration files as needed

# Format HDFS
RUN hdfs namenode -format

# Expose Hadoop ports
EXPOSE 9000 9870 8088

# Start Hadoop services
CMD ["hdfs", "datanode"]

