#  pyTKET Bricks

The pyTKET bricks are a hands-on and fun way to familiarize yourself with well-known quantum circuits. Assemble the bricks to represent a Bell State or Grover's algorithm example. The brick color code and design is based on the [pyTKET](https://cqcl.github.io/pytket/manual/index.html) circuit rendering tool. PyTKET is the python wrapper of [TKET](https://www.quantinuum.com/developers/tket), Quantinuum's open-source quantum SDK. 

We hope you enjoy pyTKET bricks by yourself, with friends, or with your family!


## Sample circuits you can assemble with pyTKET bricks

### 1) Bell state example

The pyTKET bricks can be arrange to represent a Bell state or Bell pair, after physicist John Stewart Bell. It entangles two qubits. 

<img src="Images/Bell.jpg" width="400" >


### 2) Grover's algorithm example

Grover’s algorithm is a quantum search algorithm for an unstructured database, which was devised by Lov Grover in 1996. Here we use pyTKET bricks to assemble the 2-qubit Grover’s algorithm foe the case |w>=|11>.

<img src="Images/Grover.jpg" width="400" >

## Drawing a pyTKET circuit using python

PyTKET is a python module for interfacing with TKET, a quantum computing toolkit and optimising compiler developed by Quantinuum.

Pytket is available for Python 3.8, 3.9 and 3.10, on Linux, MacOS and Windows. To install, run:

```shell
pip install pytket
```

Then import the pyTKET circuit class and circuit rendering tool:

```shell
from pytket import Circuit, OpType
from pytket.circuit.display import render_circuit_jupyter
```

Then for the Bell state circuit run:
```shell
bell = Circuit(2)
bell.H(0).CX(0,1)
render_circuit_jupyter(bell)
```
<img src="Images/Bell_pytket.jpg" width="600" >

Similarily, to draw the Grover's algorithm example run:
```shell
grover = Circuit(2)
grover.H(0).H(1).CZ(0,1).H(0).H(1).Z(0).Z(1).CZ(0,1).H(0).H(1)
render_circuit_jupyter(grover)
```
<img src="Images/Grover_pytket.jpg" width="600" >
