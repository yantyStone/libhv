add_executable(hmutex_test hmutex_test.c ../base/htime.c)
target_include_directories(hmutex_test PRIVATE .. ../base)
target_link_libraries(hmutex_test -lpthread)

add_executable(connect_test connect_test.c ../base/hsocket.c ../base/htime.c)
target_include_directories(connect_test PRIVATE .. ../base)

add_executable(socketpair_test socketpair_test.c ../base/hsocket.c)
target_include_directories(socketpair_test PRIVATE .. ../base)

add_executable(defer_test defer_test.cpp)
target_include_directories(defer_test PRIVATE .. ../base)

add_executable(hstring_test hstring_test.cpp ../base/hstring.cpp ../base/hbase.c)
target_include_directories(hstring_test PRIVATE .. ../base)

add_executable(threadpool_test threadpool_test.cpp)
target_include_directories(threadpool_test PRIVATE .. ../base)
target_link_libraries(threadpool_test -lpthread)

add_executable(objectpool_test objectpool_test.cpp)
target_include_directories(objectpool_test PRIVATE .. ../base)
target_link_libraries(objectpool_test -lpthread)

add_executable(ls listdir_test.cpp ../base/hdir.cpp ../base/hbase.c)
target_include_directories(ls PRIVATE .. ../base)

add_executable(ifconfig ifconfig_test.cpp ../base/ifconfig.cpp)
target_include_directories(ifconfig PRIVATE .. ../base)

add_executable(nslookup nslookup_test.c ../protocol/dns.c)
target_include_directories(nslookup PRIVATE .. ../base ../protocol)

add_executable(ping ping_test.c ../protocol/icmp.c ../base/hsocket.c ../base/htime.c)
target_compile_definitions(ping PRIVATE -DPRINT_DEBUG)
target_include_directories(ping PRIVATE .. ../base ../protocol)

add_executable(ftp ftp_test.c ../protocol/ftp.c ../base/hsocket.c)
target_include_directories(ftp PRIVATE .. ../base ../protocol)

add_executable(sendmail sendmail_test.c ../protocol/smtp.c ../base/hsocket.c ../utils/base64.c)
target_include_directories(sendmail PRIVATE .. ../base ../utils ../protocol)

if(UNIX)
add_executable(webbench webbench.c)
endif()

add_custom_target(unittest DEPENDS
    hmutex_test
    connect_test
    socketpair_test
    defer_test
    hstring_test
    threadpool_test
    objectpool_test
    ls
    ifconfig
    nslookup
    ping
    ftp
    sendmail
)
