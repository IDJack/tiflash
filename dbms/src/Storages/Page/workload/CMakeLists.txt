# Copyright 2022 PingCAP, Ltd.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

include_directories (${CMAKE_CURRENT_BINARY_DIR})

set (page-workload-src HeavyMemoryCostInGC.cpp HeavyRead.cpp HeavySkewWriteRead.cpp HeavyWrite.cpp HighValidBigFileGC.cpp HoldSnapshotsLongTime.cpp Normal.cpp 
     PageStorageInMemoryCapacity.cpp ThousandsOfOffset.cpp MainEntry.cpp Normal.cpp PageStorageInMemoryCapacity.cpp PSBackground.cpp PSRunnable.cpp PSStressEnv.cpp PSWorkload.cpp)

add_library (page-workload-lib ${page-workload-src})
target_link_libraries (page-workload-lib dbms clickhouse_functions clickhouse-server-lib)
target_compile_options (page-workload-lib PRIVATE -Wno-format -lc++)