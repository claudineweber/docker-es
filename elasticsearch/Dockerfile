# Use the official Elasticsearch image as base
FROM docker.elastic.co/elasticsearch/elasticsearch:8.13.4

# Copy custom configuration
COPY config/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml

# Temporarily switch to root to adjust permissions
USER root
RUN chown -R elasticsearch:elasticsearch /usr/share/elasticsearch/config/elasticsearch.yml

# Switch back to elasticsearch user
USER elasticsearch

# Set environment variables
ENV discovery.type=single-node

# Expose ports
EXPOSE 9200 9300
