# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.
#

include ../../../Makefile.in
include Makefile.in

features := $(subst $(comma), ,$(FEATURE_FLAGS))
features := $(foreach f,$(features),-f docker-compose.$(f).yaml)

BACKEND_SERVICE := oap
ifneq (,$(findstring satellite,$(features)))
	BACKEND_SERVICE := satellite
endif

.PHONY: deploy
deploy:
	docker-compose $(features) up -d

.PHONY: undeploy
undeploy:
	docker-compose $(features) --log-level ERROR down
