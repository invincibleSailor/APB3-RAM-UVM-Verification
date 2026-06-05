# APB3 RAM Verification using UVM

## Overview

This project implements and verifies an APB3 (Advanced Peripheral Bus) RAM slave using Universal Verification Methodology (UVM).

The DUT is a 32-location memory supporting APB3 read and write transactions with slave error generation for invalid addresses.

The verification environment is developed using UVM and includes:

* Driver
* Monitor
* Sequencer
* Agent
* Environment
* Scoreboard
* Multiple Test Sequences

---

## Features

### DUT Features

* APB3 compliant slave
* 32 x 32-bit memory
* Read operation support
* Write operation support
* Slave error generation (PSLVERR)
* Active-low reset

### Verification Features

* Randomized transactions
* Read testing
* Write testing
* Read-after-write verification
* Bulk write/read verification
* Error address testing
* Reset verification
* Self-checking scoreboard

---

## APB3 Signals

| Signal  | Description        |
| ------- | ------------------ |
| PCLK    | APB Clock          |
| PRESETn | Active-low Reset   |
| PSEL    | Slave Select       |
| PENABLE | Enable Signal      |
| PWRITE  | Read/Write Control |
| PADDR   | Address Bus        |
| PWDATA  | Write Data         |
| PRDATA  | Read Data          |
| PREADY  | Transfer Complete  |
| PSLVERR | Error Indication   |

---

## Verification Architecture

```text
          +-------------+
          |   Sequence  |
          +------+------+
                 |
                 v
          +-------------+
          | Sequencer   |
          +------+------+
                 |
                 v
          +-------------+
          | Driver      |
          +------+------+
                 |
                 v
          +-------------+
          | APB RAM DUT |
          +------+------+
                 |
                 v
          +-------------+
          | Monitor     |
          +------+------+
                 |
                 v
          +-------------+
          | Scoreboard  |
          +-------------+
```

## Implemented Testcases

### 1. Write Test

* Random write transactions
* Valid address range

### 2. Read Test

* Random read transactions
* Valid address range

### 3. Read After Write Test

* Write operation followed by read operation

### 4. Bulk Write and Bulk Read Test

* Multiple writes followed by multiple reads

### 5. Invalid Address Write Test

* Generates PSLVERR

### 6. Invalid Address Read Test

* Generates PSLVERR

### 7. Reset Test

* Verifies DUT reset behavior

---

## Simulation

Compile and run:

```bash
vlog apb_ram.sv
vlog apb_tb.sv
vsim tb
run -all
```

---

## Results

The scoreboard compares DUT outputs with a reference memory model and reports:

* DATA MATCHED
* TEST FAILED
* SLV ERROR

---

## Future Improvements

* Functional Coverage
* APB4 Support
* Assertions (SVA)
* Coverage-driven Verification
* Multiple Slave Support
* UVM Register Model (RAL)

---

## Author

Kashyap Joshi

Electronics and Communication Engineering

Institute of Technology, Nirma University
