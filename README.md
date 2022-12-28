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

## Drawing a pyTKET circuit in a Jupyter Notebook

<code>
pip install pytket
<code>

from pytket import Circuit, OpType
from pytket.circuit.display import render_circuit_jupyter
