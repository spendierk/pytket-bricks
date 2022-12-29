#  pyTKET Bricks

The pyTKET bricks are a hands-on and fun way to familiarize yourself with well-known quantum circuits. Assemble the bricks to represent a Bell State or Grover's algorithm example. 

https://user-images.githubusercontent.com/106914305/209889480-10e965fd-5854-4b76-a36e-4a681a53319e.mp4

The brick color code and design are based on the [pyTKET](https://cqcl.github.io/pytket/manual/index.html) circuit rendering tool. PyTKET is the python wrapper of [TKET](https://www.quantinuum.com/developers/tket), Quantinuum's open-source quantum SDK. 

Your pyTKET bricks set includes [H-gates, Z-gates, CX-gates, and CZ-gates,](https://en.wikipedia.org/wiki/Quantum_logic_gate) as well as qubit zero (q[0]) and qubit one (q[1]) and wire pieces represented as straight lines.

We hope you enjoy pyTKET bricks alone, with friends, or with your family!


## Sample circuits you can assemble with pyTKET bricks

### 1) Bell state example

The pyTKET bricks can be arrange to represent a Bell state or Bell pair, after physicist John Stewart Bell. [This circuit entangles two qubits.](https://en.wikipedia.org/wiki/Bell_state) 

<img src="Images/Bell.jpg" width="400" >


### 2) Grover's algorithm example

Grover’s algorithm is a quantum search algorithm for an unstructured database, which Lov Grover devised in 1996. Here we use pyTKET bricks to assemble the 2-qubit [Grover’s algorithm](https://en.wikipedia.org/wiki/Grover%27s_algorithm) for the case |w>=|11>.

<img src="Images/Grover.jpg" width="400" >

## Drawing a pyTKET circuit using Python

[PyTKET](https://cqcl.github.io/pytket/manual/index.html) is a python module for interfacing with [TKET](https://www.quantinuum.com/developers/tket), a quantum computing toolkit and optimising compiler developed by Quantinuum.

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

## Run a sample circuit on a state vector simulator

Next, we show how to use pyTKET to execute the Bell state example on the `AerStateBackend` simulator. First, install the pytket-qiskit backend extension

```shell
pip install pytket-qiskit
```

and then run:

```shell
from pytket.extensions.qiskit import AerStateBackend
import numpy as np

backend = AerStateBackend() #initialize backend with default settings
result = backend.run_circuit(bell) #interface for running circuit on a given backend to obtain results
result_state = result.get_state() #for results we get the full state vector of the output
print(f"State vector -> {np.round(result_state, 3)}")   # prints (0,0), (1,0), (0,1), (1,1) states
```

The printed output is
`State vector -> [0.707+0.j 0.   +0.j 0.   +0.j 0.707+0.j]`
which corrsponds to the expected state function
```math
\left| \psi \right\rangle = \frac{1}{\sqrt{2}} \left( \left| 00 \right\rangle + \left| 11 \right\rangle\right).
```
