# Creating an Oracle Circuit for Grover's Algorithm
<p align="center">
  <img width="602" alt="Screenshot 2023-09-12 at 08 41 37" src="https://github.com/matt-jung/oracle-for-grovers-algorithm/assets/133035195/6b601b13-9a38-43e6-bd98-5952cd7c5f37">
</p>

## How it Works
### Function of the Oracle Circuit
As part of Grover's unstructured search algorithm, the oracle circuit is given an equal superposition of all possible input states and aims to identify the states that are solutions to a given search problem. The oracle does this by inverting the phase of states that correspond to solutions, and doing nothing to all other states. I.e.

<p align="center">
  $U_{oracle} | x \rangle = -| x \rangle$ when $| x \rangle$ is a solution
</p>
<p align="center">
  $U_{oracle} | x \rangle = | x \rangle$ when $| x \rangle$ is not a solution
</p>

### Circuit Implementation
The user inputs a binary string that represents the solution to a given search problem. The program them simulates a quantum circuit via Qiskit that corresponds to the oracle for that given string. The process is as follows:

- Apply $X$ gates to qubits corresponding to a '0' in the binary string
- Apply a multi-control phase gate with phase $\pi$ to all qubits
- Apply $X$ gates to the same qubits from the first step
  
<p align="center">
  <img width="220" alt="Screenshot 2023-09-12 at 09 09 51" src="https://github.com/matt-jung/oracle-for-grovers-algorithm/assets/133035195/5fe3b58c-9207-4fc1-bc57-e36518eda148">
</p>
<p align="center">
  Example circuit for the string '101101'
</p>

### Analysis
The matrix representation for the multi-control phase (MCP) gate is:

```math
\begin{bmatrix}
1 & 0 & \dots &  &  \\
0 & 1 &  &  &  \\
\vdots &  & \ddots &  &  \\
 &  &  & 1 &  \\
 &  &  &  & -1 
\end{bmatrix} 
```


