FROM conchoid/docker-rbenv:v1.0-2.3.6-alpine3.4

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

