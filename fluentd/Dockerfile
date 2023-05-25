FROM fluent/fluentd:v1.12-debian-1
USER root
RUN ["gem", "install", "fluent-plugin-tail-path", "--no-rdoc", "--no-ri", "--version", "0.0.4"]
USER fluent
