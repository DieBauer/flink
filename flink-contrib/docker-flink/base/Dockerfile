################################################################################
#  Licensed to the Apache Software Foundation (ASF) under one
#  or more contributor license agreements.  See the NOTICE file
#  distributed with this work for additional information
#  regarding copyright ownership.  The ASF licenses this file
#  to you under the Apache License, Version 2.0 (the
#  "License"); you may not use this file except in compliance
#  with the License.  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
# limitations under the License.
################################################################################

FROM java:8-jdk-alpine

RUN apk --update add curl tar supervisor openssh-server openssh-client

#priviledge separation directory
RUN mkdir /var/run/sshd

RUN echo 'root:secret' | chpasswd

#SSH as root... probably needs to be revised for security!
RUN sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config

EXPOSE 22

# supervisor base configuration
ADD supervisor.conf /etc/supervisor/

# default command / not overridable CMD needed for supervisord
#CMD ["supervisord", "-c", "/etc/supervisor.conf"]
