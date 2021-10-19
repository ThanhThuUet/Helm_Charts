FROM bitnami/fluentd:1.14.0-debian-10-r9
LABEL maintainer "thuntt"

## Change user to perform privileged actions
USER 0

## Install custom Fluentd plugins
RUN apt-get update && apt-get install build-essential git -y
# RUN echo 'gem "fluent-plugin-color-stripper", :git => "https://github.com/mattheworiordan/fluent-plugin-color-stripper.git", :branch => "master"' \
#     >> Gemfile.local
RUN git clone https://github.com/mattheworiordan/fluent-plugin-color-stripper.git && \
    cd fluent-plugin-color-stripper && \
    fluent-gem build fluent-plugin-color-stripper.gemspec && \
    fluent-gem install fluent-plugin-color-stripper-0.0.3.gem

## Revert to the original non-root user
USER 1001
