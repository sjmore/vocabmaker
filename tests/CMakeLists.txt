# 테스트 실행 파일의 이름을 정합니다.
project(EchoTest CXX)

# C++ 표준을 17로 설정합니다.
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 테스트에 필요한 소스 파일을 추가합니다.
add_executable(echo_test main.cpp)

# echo_svr 라이브러리와 gtest 라이브러리를 링크합니다.
# target_link_libraries를 사용하면 필요한 헤더 파일의 경로도 자동으로 설정됩니다.
target_link_libraries(echo_test PRIVATE echo_logic GTest::gtest_main)

# CTest에 테스트를 추가합니다.
include(GoogleTest)
gtest_discover_tests(echo_test)
