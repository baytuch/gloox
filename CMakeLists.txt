
cmake_minimum_required(VERSION 2.8)
set (VERSION "1.0.22")
project(gloox)

# cmake -G "NMake Makefiles" -D CMAKE_BUILD_TYPE=Release ..
set(EXT_LIBS_PATH "C:/Users/Sasha/dev")

if (MSVC)
  if (NOT OPENSSL_LIBRARYDIR AND NOT OPENSSL_INCLUDEDIR)
    set (OPENSSL_LIBRARYDIR "${EXT_LIBS_PATH}/lib")
    set (OPENSSL_INCLUDEDIR "${EXT_LIBS_PATH}/include")
  endif()
  include_directories(${OPENSSL_INCLUDEDIR})
  FIND_LIBRARY(SSL_LIBRARY ssleay32 ${OPENSSL_LIBRARYDIR})
  FIND_LIBRARY(CRYPTO_LIBRARY libeay32 ${OPENSSL_LIBRARYDIR})
  message(STATUS ${SSL_LIBRARY})
  message(STATUS ${CRYPTO_LIBRARY})
endif()

if (MSVC)
  add_definitions(-D HAVE_OPENSSL)
endif()

add_subdirectory(src)
