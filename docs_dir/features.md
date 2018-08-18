# Features

This page shows the features of DGTD Numerical Simulation System. The DGTD is suitable for solving the scattering problems excited by plane wave, radiation problems excited by lumped port or wave port, wave guide problems excited by various mode of wave. </br>
The DGTD have the parallel and distributed solver for electrically large problems, which can improve the computational performance and reduce the computational time. Otherwise DGTD is equipped with various kinds of numerical techniques in terms of algorithms.

## Higher-order Precision
<img src="../img/ho-spaces-padding.png" align="right">
DGTD is FEM like algorithm, so it can compute based on the unstructured mesh or curve mesh, which fits better for some complex geometry. With the locality of DGTD scheme, the high order scheme is easily constructed with high order precision. In the complex condition, DGTD is obviously superior to FDTD or other structured mesh based algorithms. The hp-adaptive is also let the DGTD be adjustable on some meshes requring high precision. For some objects with simple structures, which is meshed with structured mesh, the DGTD is also high-order precision in this case. </br>

## Hybrid Mesh
<img src="../img/ho-spaces-padding.png" align="right">
DGTD supports upper three mesh conditions:

- Unstructured Mesh
- Structured Mesh
- Unstructured-Structured Hybrid Mesh

In general conditions, we recommend users compute with DGTD based on unstructured mesh, which can lead to better accuracy, but in some cases, the objects contains both complex and simple structures, the complex structures are generated with unstructured mesh, and the simple structures are generated with structured mesh, this will maintain the high precision and reduce degree of freedom compared with fully unstructured mesh condition.

## Local Time Step
<img src="../img/ho-spaces-padding.png" align="right">
The local time step (LTS) is the technique which can obviously reduce the computational time in below problems:

- Multi-Scale Problem
- Complex Geometry Problem
- Transient Problem

In multi-scale problems, the gap or hole will generate very small mesh, which leads to the tiny global time step. In order to keep the stability on small mesh, all the mesh should move with tiny time step in time domain, it causes large amount of computation time. To solve this problem, local time step technique requires different size of mesh move with different time step but keeps the stability, the large mesh will not concern on the tiny time step on small mesh, which save a lot of time.

## Explicit-Implicit Hybrid Scheme
<img src="../img/ho-spaces-padding.png" align="right">
The construction of DGTD scheme can be classfied into three categories:

- Explicit Scheme
- Implicit Scheme
- Explicit-Implicit Hybrid Scheme

These two schemes have their own advantages and their own shortcomings, the explicit scheme has a very good cell locality, suitable for parallelism. The implicit scheme causes the coupling between the cells, we need to solve a linear system, which leads to a decrease in the parallel effect, but the implicit scheme can lead to a larger time step, we have an explicit format on most grids, but we use the implicit scheme on the small grid, which makes the time step larger on the small grid.</br>

Thus, the computation time on the small grid is reduced, and the whole computing time is reduced, meanwhile the parallel effect will not drop down, this technology is based on the LTS technique.

## Plane Wave Excitation
<img src="../img/ho-spaces-padding.png" align="right">
Plane wave excitation is mainly used in scattering problem. Plane wave propagates in specific direction, polarization mode is line polarization. Plane wave produces scattering wave after hitting the scattering objects, according to huygens equivalent principle, near field scattering wave is mapped to far field, so far field distribution can be obtained. The far field information of scattering object is called Radaring Crossing Section (RCS), our proposed DGTD now realize bistatic RCS, which is the most common condition in modern radar detection. The RCS problem is always be electrically large, such as aircraft and warships</br>

## Lumped Port Excitation
<img src="../img/ho-spaces-padding.png" align="right">
This port is mainly used in radiation problems. As a simplified excitation source, the structure of a metal patch replaces the coaxial line structure. In some cases, the wave port is not convenient introduced in simulation environment, such as dipole, so the lumped port is constructed to solve those cases. It should be noted that the S parameter of lumped port is not the same as wave port, it computes S parameter based on impedance matching. The lumped-port only need to introduce magnetic source, the structure is simpler, most of the situation can be achieved as accurate as that excited by wave port.</br></br>

## Wave Port Excitation
<img src="../img/ho-spaces-padding.png" align="right">
Wave port is a physical structure, it is used to simulate the transmission of electromagnetic wave in the coaxial lines. Because of its physical characteristics, which is modeling according to the coaxial line in real life, wave port can result in more accurate calculation results and closer to the actual experimental results. The S parameter obtained by wave port is based on the incident and reflect wave. If conditions permit, wave port is the first recommended choice of port mode in the electromagnetic wave simulation.</br>
In the antenna problem, the wave port is mainly stimulated by the form of TEM wave.

## Modal Wave (TE,TM,TEM) Excitation
<img src="../img/ho-spaces-padding.png" align="right">
In the waveguide problem, there are different modes of wave in the transmission line, such as:

- Te Mode
- TM Mode
- TEM Mode
- Other Mixed Mode

Different excitation modes will lead to different results. In the waveguide problem, we need to select a specific type of mode wave, different modes of wave port excitation have been achieved in our proposed DGTD algorithm.</br>

## HPC Distributed System
<img src="../img/ho-spaces-padding.png" align="right">
In order to achieve faster calculation speed, DGTD realizes the multiple cores parallel on the single machine and distributed parallel on the cluster. With distributed system,  DGTD can achieve the parallel scale of the thousand cores under the Linux system, and has the advantage on calculating the electrically large size problem. With parallel system, DGTD and can reduce the calculation time obviously on the single machine by the multi-core parallel. Parallel efficiency of our proposed DGTD can reach more than 90%.
