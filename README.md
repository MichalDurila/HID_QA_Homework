# QA Test Specification
The task is to write an automated test which executes a set of test cases over the supplied library
“hash”. Please attempt to discover as many bugs in the “hash” library as possible and write a
summary/protocol of detected bugs. The output of the task should be:
* The source code of your automated test.
* The summary of detected bugs.

## Tested Library
The library is provided as a dynamically linked library (hash.dll / .so / .dylib). For Windows we also
provide the corresponding import library hash.lib.

The functionality of the individual functions is specified in the header file hash.h – take this file as the
specification you will test against.

We are also providing a sample application sample.cpp and its compiled binaries. You can use it to
verify that the code works properly on your test computer. However, please note that the sample
application IS NOT a subject of your test.

The “hash” library has a task of calculating MD5 cryptographic hash of the contents of all files in a
specified directory. The calculation runs asynchronously, in parallel with any other calculations in
progress, which allows to perform the calculations more effectively in multiple threads. The results of
all running calculations are stored sequentially in a single in-memory text log, which can be read on
row-by-row basis. Every row has the following format:
`“<operation id> <filename> <MD5 hash in hexadecimal notation>”`

The operation id is an identification of the operation started by a call to HashDirectory(). Operation
ids are unique and allow you to identify which rows of the log were created by which operation.

## Interfacing With Dynamic Library From Python
If you will be writing the automated test in Python, you will need to load the dynamic library and
create a mapping from C to Python interface. This can be done using the Python ctypes module:
https://docs.python.org/3/library/ctypes.html

## Additional Notes
* The automated test should be programmed in one of the following languages: Python, C,
C# or C++.
* The “hash” library is available for the following operating systems: Windows (library is Intel
32-bit architecture), Linux (library is Intel 64-bit architecture) or Mac (the library is arm64
architecture).
