FROM docker.elastic.co/elastic/elastic:8.13.4

# Copy custom configuration
COPY elasticsearch/config/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml

# Set ownership to elasticsearch user
RUN chown -R elasticsearch:elasticsearch /usr/share/elasticsearch/config/elasticsearch.yml

# Set environment variables
ENV discovery.type=single-node

# Expose ports
EXPOSE 9200 9300