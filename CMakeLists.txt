cmake_minimum_required(VERSION 3.5)
project(ConcurrentServer)

add_compile_options(-std=gnu99 -Wall -O3 -g -DNDEBUG -pthread)

set(INC_DIR /usr/local/include)
set(LINK_DIR /usr/local/lib)

include_directories(${INC_DIR})
link_directories(${LINK_DIR})

add_executable(sequential_server sequential-server.c utils.c)

add_executable(threaded_server threaded-server.c utils.c)
target_link_libraries(threaded_server pthread)

add_executable(blocking_listener blocking-listener.c utils.c)
add_executable(nonblocking_listener nonblocking-listener.c utils.c)

add_executable(select_server select-server.c utils.c)

add_executable(epoll_server epoll-server.c utils.c)

add_executable(uv_server uv-server.c utils.c)
target_link_libraries(uv_server uv)

add_executable(eventLongIssue eventLongRun.c)
target_link_libraries(eventLongIssue uv)

add_executable(eventLongIssueWork eventLongRunWork.c)
target_link_libraries(eventLongIssueWork uv)

add_executable(uv_isprime_server uv-isprime-server.c utils.c)
target_link_libraries(uv_isprime_server uv)