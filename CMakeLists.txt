cmake_minimum_required(VERSION 3.25)

# 최상위 프로젝트 이름 정의
project(vocabmaker CXX)

# 테스팅 활성화
enable_testing()

# Google Test 추가
include(FetchContent)
FetchContent_Declare(
  googletest
  GIT_REPOSITORY https://github.com/google/googletest.git
  GIT_TAG    v1.17.0
)

# For Windows: Prevent overriding the parent project's compiler/linker settings
set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
FetchContent_MakeAvailable(googletest)

FetchContent_Declare(
  cpp-httplib
  GIT_REPOSITORY https://github.com/yhirose/cpp-httplib.git
  GIT_TAG        master   # 또는 특정 릴리즈 태그 (예: v0.15.3)
)
FetchContent_MakeAvailable(cpp-httplib)

target_include_directories(MyApp PRIVATE ${cpp-httplib_SOURCE_DIR})

# tests 디렉터리를 빌드에 포함
add_subdirectory(tests)


