# OpenSSLCodeExecution

Python PoC demonstrating arbitrary code execution using only the openssl binary, as discovered by Anthony Weems and described in [Remote code execution in Managed Anthos Service Mesh control plane](https://lf.lc/vrp/203177829/). 

---

## Usage

First change the exploit function in the exploit.c file to do what you want and compile it to a shared object file with:

```bash
gcc -shared -o exploit.so -fPIC exploit.c
```

Then run the Python exploit.

```python
$ python3 ./exploit.py -h
usage: exploit.py [-h] input output

Given a shared object (.so) input file, finds the OpenSSL commands needed to execute it and writes them to an
output file.

positional arguments:
  input       The .so input file name
  output      The output file name

optional arguments:
  -h, --help  show this help message and exit
```

This will generate an output file containing 3 openssl commands. Running these commands in order will execute the exploit function specified in exploit.c.

---

## Shout Out

I learned about this from [Could I Hack into Google Cloud?](https://www.youtube.com/watch?v=GvO2Xtx8p9w) by LiveOverflow. 
