# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)

if (NOT DEFINED ENV{BSIM_COMPONENTS_PATH})
  message(FATAL_ERROR "This test requires the BabbleSim simulator. Please set  \
          the  environment variable BSIM_COMPONENTS_PATH to point to its       \
          components folder. More information can be found in                  \
          https://babblesim.github.io/folder_structure_and_env.html")
endif()

find_package(Zephyr HINTS $ENV{ZEPHYR_BASE})
project(bsim_test_privacy)

target_sources(app PRIVATE
  src/test_undirected_main.c
  src/test_undirected_central.c
  src/test_undirected_peripheral.c
)

zephyr_include_directories(
  $ENV{BSIM_COMPONENTS_PATH}/libUtilv1/src/
  $ENV{BSIM_COMPONENTS_PATH}/libPhyComv1/src/
  $ENV{ZEPHYR_BASE}/subsys/bluetooth/host/
)
