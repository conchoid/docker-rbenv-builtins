FROM ruby:2.3.6-alpine3.4

ENV SETUP_HOME /opt/ruby
ENV RBENV_ROOT ${SETUP_HOME}/rbenv
ENV PATH ${RBENV_ROOT}/shims:${RBENV_ROOT}/bin:${PATH}

RUN apk add --no-cache --update \
# rbenv build dependence
    bash=4.3.42-r5 \
    git=2.8.6-r0 \
    make=4.1-r1 \
    gcc=5.3.0-r0 \
    libc-dev=0.7-r0 \
# ruby build dependence 
    autoconf=2.69-r0 \
    curl=7.58.0-r0 \
    bison=3.0.4-r0 \
    coreutils=8.25-r0 \
    readline-dev=6.3.008-r4 \
    linux-headers=4.4.6-r1 \
    patch=2.7.5-r1 \
    libffi-dev=3.2.1-r2 \
    gdbm=1.11-r1 \
    openssl-dev=1.0.2n-r0

# install rbenv
RUN set -x \
    && RBENV_VERSION="v1.1.1" \
    && git clone https://github.com/rbenv/rbenv.git "${RBENV_ROOT}" \
    && cd "${RBENV_ROOT}" \
    && git checkout "${RBENV_VERSION}" \
    && src/configure && make -C src \
    && rm -rf .git

# install ruby-build as rbenv plugin
RUN set -x \
    && RUBY_BUILD_DIR="${RBENV_ROOT}/plugins/ruby-build" \
    && RUBY_BUILD_VERSION="v20171215" \
    && mkdir -p "${RBENV_ROOT}/plugins" \
    && git clone https://github.com/rbenv/ruby-build.git "${RUBY_BUILD_DIR}" \
    && cd "${RUBY_BUILD_DIR}" \
    && git checkout "${RUBY_BUILD_VERSION}" \
    && rm -rf .git

# preinstall ruby
# Version which confirmed that all of Rubocop, Reek, Brakeman and Rails_best_practices works is 2.2.X, 2.3.X, 2.4.X only.
# Since 2.5.X has problems with stack overflow in Alpine environment (https://bugs.ruby-lang.org/issues/14387), those tools did not work properly.
# For now, versions other than 2.2.X, 2.3.X, and 2.4.X are not supported, but the share of other versions can not be ignored, so need to support later.

# COPY ruby-1.9.3-p551.patch ${SETUP_HOME}/
# COPY ruby-2.0.0-p648.patch ${SETUP_HOME}/
# RUN rbenv install --patch 1.9.3-p551 < ${SETUP_HOME}/ruby-1.9.3-p551.patch
# RUN rbenv install --patch 2.0.0-p648 < ${SETUP_HOME}/ruby-2.0.0-p648.patch
# RUN rbenv install 2.1.10
RUN rbenv install 2.2.9
RUN rbenv install 2.3.6
RUN rbenv install 2.4.3
# RUN rbenv install 2.5.0-rc1

