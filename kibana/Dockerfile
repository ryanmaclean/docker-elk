FROM kibana:latest

RUN apt-get update && apt-get install -y netcat git

COPY entrypoint.sh /tmp/entrypoint.sh
RUN chmod +x /tmp/entrypoint.sh

RUN kibana plugin --install elastic/sense
RUN kibana plugin --install kibana/timelion
RUN git clone https://github.com/ryanmaclean/beats-dashboards.git
RUN ./beats-dashboards/load.sh -url "http://localhost:9200"
CMD ["/tmp/entrypoint.sh"]
