# Copyright 2016, Google Inc.
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are
# met:
#
#     * Redistributions of source code must retain the above copyright
# notice, this list of conditions and the following disclaimer.
#     * Redistributions in binary form must reproduce the above
# copyright notice, this list of conditions and the following disclaimer
# in the documentation and/or other materials provided with the
# distribution.
#     * Neither the name of Google Inc. nor the names of its
# contributors may be used to endorse or promote products derived from
# this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

# Docker file for building gRPC manylinux Python artifacts.

FROM quay.io/pypa/manylinux1_i686

# Update the package manager
RUN yum update -y

###################################
# Install Python build requirements
RUN /opt/python/cp27-cp27m/bin/pip install cython
RUN /opt/python/cp27-cp27mu/bin/pip install cython
RUN /opt/python/cp34-cp34m/bin/pip install cython
RUN /opt/python/cp35-cp35m/bin/pip install cython

####################################################
# Install auditwheel with fix for namespace packages
RUN git clone https://github.com/pypa/auditwheel /usr/local/src/auditwheel
RUN cd /usr/local/src/auditwheel && git checkout bf071b38c9fe78b025ea05c78b1cb61d7cb09939
RUN /opt/python/cp35-cp35m/bin/pip install /usr/local/src/auditwheel
RUN rm /usr/local/bin/auditwheel
RUN cd /usr/local/bin && ln -s /opt/python/cp35-cp35m/bin/auditwheel
