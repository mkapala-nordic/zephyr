# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(app)

target_sources(app PRIVATE
  src/test_bt_crypto_ccm.c

  $ENV{ZEPHYR_BASE}/subsys/bluetooth/host/aes_ccm.c
)
