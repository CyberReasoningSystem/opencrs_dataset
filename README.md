# `opencrs_dataset` 🗂️

## Description

`opencrs_dataset` is the **dataset resulted by running OpenCRS's dataset module** with all integrated test suites. It contains **`54586` vulnerable ELF executables**, compiled from **C sources** and targetting the **32-bit** `i386` architecture.

## Folder Structure

```text
opencrs_dataset                             root folder
├── executables                             folder with all executables
│   └── ...
├── index.csv                               labels for exact executable, with
|                                           parent dataset and its CWEs,
|                                           eventually separated by commas
└── README.md                               this file
```

## Executables Analysis

### Parent Test Suites

| Test Suite Name                                                                                       | Creator                                                                                                | Initial Sources Count | Final Executables Count |
| ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | --------------------- | ----------------------- |
| [Juliet C/C++ 1.3](https://samate.nist.gov/SARD/test-suites/112)                                      | National Security Agency's Center for Assured Software. National Institute of Standards and Technology | `64123`               | `54531`                 |
| [C Test Suite for Source Code Analyzer v2 - Vulnerable](https://samate.nist.gov/SARD/test-suites/100) | Alexander Hoole. National Institute of Standards and Technology                                        | `54`                  | `50`                    |
| Toy Test Suite                                                                                        | OpenCRS                                                                                                | `5`                   | `5`                     |

### Top 10 Present Weaknesses

| Weakness                                   | Count   |
| ------------------------------------------ | ------- |
| Stack-based Buffer Overflow                | `13834` |
| Heap-based Buffer Overflow                 | `11088` |
| Integer Overflow or Wraparound             | `3960`  |
| Mismatched Memory Management Routines      | `3564`  |
| Integer Underflow                          | `2952`  |
| Free of Memory not on the Heap             | `2680`  |
| Use of Externally-Controlled Format String | `2407`  |
| Buffer Underflow                           | `2048`  |
| Buffer Under-read                          | `2048`  |
| OS Command Injection                       | `1921`  |

## Steps to Reproduce

1. Set up OpenCRS's `dataset` module on an Ubuntu 20.04 host by following the [guide](https://github.com/CyberReasoningSystem/dataset#setup).
2. Build each test suite (identified by `<test_suite_id>`): `poetry run dataset build --testsuite <test_suite_id>`.
3. The executables in this repository, under the `executables` folder, are those from `dataset`'s `executables`. The same relation applies for `index.csv`, which is `dataset`'s `vulnerables.csv` without the last column.

