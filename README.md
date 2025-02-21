# Communication-Avoiding QR Factorization (CAQR)

## Author
**Name:** Seeshuraj Bhoopalan  
**ID:** 24359927

## Project Overview
This repository contains an implementation of Communication-Avoiding QR (CAQR) factorization for tall-skinny matrices. The implementation includes both Python and C versions, following the Tall-Skinny QR (TSQR) approach discussed in the lecture materials.

## Repository Structure
```
├── TSQR_C-codes/       # C implementation of CAQR
│   ├── tsqr.c          # Main source code for TSQR
│   ├── tsqr_scaling.c  # Scaling tests implementation
│   ├── Makefile        # Compilation instructions
│   └── hostfile        # Configuration for distributed execution
├── Python_Notebook/
│   └── A1_case_study.ipynb  # Jupyter notebook with Python implementation
├── CAQR-Assignment.pdf  # Assignment description
└── README.md           # This file
```

## Implementation Details

### TSQR Algorithm
The implementation focuses on the case where a tall, narrow matrix is distributed onto four processors. The algorithm follows these steps:
1. Divide the input matrix into four blocks of rows
2. Perform local QR factorization on each block
3. Combine the R factors in a tree-based approach
4. Form the final Q and R matrices

### Python Implementation
The Python implementation in `A1_case_study.ipynb` uses NumPy's QR factorization and demonstrates the mathematical principles behind TSQR. It includes a scaling analysis that shows how performance varies with matrix dimensions.

### C Implementation
The C implementation uses LAPACK's QR factorization routines (specifically `dgeqrf` and `dorgqr`) for local QR factorizations. The code handles matrix distribution, combination, and verification of results. Scaling tests are implemented in a separate file (`tsqr_scaling.c`).

## System Requirements

### Python Dependencies
- NumPy
- Matplotlib (for scaling plots)
- Jupyter Notebook

### C Dependencies
- LAPACK and LAPACKE
- BLAS

## Execution Instructions

### Python Implementation
Open and run the Jupyter notebook:
```bash
cd Python_Notebook
jupyter notebook A1_case_study.ipynb
```

### C Implementation
```bash
cd TSQR_C-codes
make
./tsqr
```

For scaling tests:
```bash
cd TSQR_C-codes
make scaling
./tsqr_scaling
```

## Environment Notes
The C implementation requires LAPACK and LAPACKE libraries. Due to availability constraints on shared systems (Callan, Chuck, and Seagull), the code was executed on a custom Azure system with the following specifications:
- 4-core CPU
- 16GB RAM
- 32GB Storage

C/C++ compiler configuration:
```json
{
    "name": "Linux",
    "compilerPath": "/usr/bin/g++",
    "cStandard": "c17",
    "cppStandard": "c++14",
    "intelliSenseMode": "linux-clang-x64"
}
```

## Scaling Analysis
The implementation includes scaling tests that measure performance with respect to:
1. Varying number of columns (n) with fixed number of rows (m)
2. Varying number of rows (m) with fixed number of columns (n)

Results are presented in the Python notebook and demonstrate the efficiency of the CAQR approach for tall-skinny matrices.

## Assignment Compliance
This implementation satisfies all requirements specified in the assignment:
- Matrix distribution across four processors
- Use of built-in QR factorization for local computations
- Implementation in both high-level (Python) and low-level (C) languages
- Scaling analysis with respect to matrix dimensions
