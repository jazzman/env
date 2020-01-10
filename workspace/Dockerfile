ARG PHP_VERSION

FROM laradock/workspace:2.6.1-${PHP_VERSION}

###########################################################################
# xDebug:
###########################################################################

USER root

ARG INSTALL_XDEBUG=false

RUN if [ ${INSTALL_XDEBUG} = true ]; then \
    apt-get update && apt-get upgrade -y \
    && apt-get install -y php${PHP_VERSION}-xdebug \
;fi

ARG PHP_VERSION

COPY ./php.ini /etc/php/${PHP_VERSION}/cli/conf.d/php.ini

USER root

# Clean up
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    rm /var/log/lastlog /var/log/faillog

# Set default work directory
WORKDIR /var/www