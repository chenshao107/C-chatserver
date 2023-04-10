cmake_minimum_required(VERSION 3.24)
project(server)

# 定义一个SRC_LIST变量，包含了该目录下所有的源文件
aux_source_directory(. SRC_LIST)
aux_source_directory(./db DB_LIST)

#find_package(muduo)
include_directories(${PROJECT_SOURCE_DIR}/../../include)
include_directories(${PROJECT_SOURCE_DIR}/../../include/server)
include_directories(${PROJECT_SOURCE_DIR}/../../include/server/db)
#include_directories(${PROJECT_SOURCE_DIR}/../../include/server/mudel)
include_directories(${PROJECT_SOURCE_DIR}/../../thirdparty)

# 指定生成可执行文件
add_executable(ChatServer ${SRC_LIST} ${DB_LIST} chatservice.cpp ../../include/public.hpp ../../include/server/db/db.h db/db.cpp ../../include/server/usermodel.hpp usermodel.cpp ../../include/server/user.hpp ../../include/server/offlinemessagemodel.hpp offlinemessagemodel.cpp ../../include/server/friendmodel.hpp friendmodel.cpp ../../include/server/groupmodel.hpp ../../include/server/groupuser.hpp groupmodel.cpp ../../include/server/group.hpp redis.cpp)



# 指定可执行文件链接时依赖的库文件
target_link_libraries(ChatServer libmuduo_net.a libmuduo_base.a mysqlclient pthread hiredis.a)





