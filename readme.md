# OKX Exchange Connector in C++ 💼💻

## Description
This repository contains a C++ application that accomplishes the following tasks:

1. **Connect to OKX Crypto Exchange API:** 🌐 The application connects to the OKX Crypto Exchange API using pure requests without external libraries.

2. **Extract Last 1m L1 LOB Data:** 📊 Continuously extracts the last 1 minute Level 1 Limit Order Book (LOB) data for BTC-USDT from the OKX API with less than 1-second lag via HTTP Requests and less than 100ms lag via WebSocket connector.

3. **Model Difficult Calculation Task:** 🧮 Implements a separate class for a difficult calculation task, involving memory and time-expensive operations. The task involves solving the equation AX = E, where A is a matrix and E is the identity matrix (inverse matrix of A).

4. **Simultaneous Execution:** ⚙️ The application runs the OKX API connector and the difficult calculation task class simultaneously. It logs messages about the number of OKX requests made and the number of heavy tasks completed, demonstrating the correctness of parallel execution.

## Requirements
- C++ compiler
- Standard C++ libraries

### Or you can build the binary using CMake and conan.

## How to Run
1. Clone the repository to your local machine.
2. Compile the C++ files using your preferred C++ compiler (e.g., g++):
     ```
     REST:
     g++ main.cpp -o main CalculationClass.cpp OKXClass.cpp -lcurl -lssl -lcrypto
     WebSocket:
     g++ main.cpp -o main CalculationClass.cpp WebSocketClass.cpp -lssl -lcrypto
     ```
4. Run the compiled executable.

### Using Cmake and Conan
1. Install Conan.
2. Install required libraries using
    ```bash
    conan install . --output-folder=build --build=missing
    ```
3. Go to the build directory and invoke build
    ```bash
    cd build
    cmake .. -DCMAKE_TOOLCHAIN_FILE=./build/Release/generators/conan_toolchain.cmake -DCMAKE_BUILD_TYPE=Release
    cmake --build . 
    ```
  Compilation is complete now.
4. Run Using the binaries in the build folder.
  ```bash
  ./WebSocket/websocket_client 
  ```
  or
  ```bash
  ./REST/rest_client
  ```


## Files Structure
```
- REST
  - main.cpp
  - CalculationClass.h
  - CalculationClass.cpp
  - OKXClass.h
  - OKXClass.cpp
  - Recycle Bin (contains additional files)
- WebSocket
  - main.cpp
  - CalculationClass.h
  - CalculationClass.cpp
  - WebSocketClass.h
  - WebSocketClass.cpp
  - Recycle Bin (contains additional files)
```
### In the `REST` folder:
- `main.cpp`: Contains the main program logic for the HTTP requests implementation, including the simultaneous execution of the OKX API connector and the difficult calculation task.
- `CalculationClass.h` and `CalculationClass.cpp`: Define and implement the `CalculationClass`, which handles the difficult calculation task.
- `OKXClass.h` and `OKXClass.cpp`: Define and implement the `OKXClass`, which connects to the OKX Crypto Exchange API using HTTP requests via libcurl.

### In the `WebSocket` folder:
- `main.cpp`: Contains the main program logic for the WebSocket implementation, including the simultaneous execution of the OKX API connector and the difficult calculation task.
- `CalculationClass.h` and `CalculationClass.cpp`: Define and implement the `CalculationClass`, which handles the difficult calculation task.
- `WebSocketClass.h` and `WebSocketClass.cpp`: Define and implement the `WebSocketClass`, which connects to the OKX Crypto Exchange API using WebSocket via the WebSocket++ library.

## License
This project is licensed under the [MIT License](LICENSE). 📜🔒

