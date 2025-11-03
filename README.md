This repository is very simialr to the original repo here [here](https://github.com/rrquizon1/FPGA-Acceleration-Study/)

The main difference is using pytorch framework instead of tensorflow keras. This gives me flexibility as a I move to further neural network architectures such as CNN as I am more familiar with pytorch framework. 

The RTL structure of the neuron closely resembles the original implementation. In this example, I successfully implemented a network that differs from the one in the original tutorial, demonstrating a deeper understanding of the design.

The jupyter notebook trainNN.ipynb generates the following:

1. Generation of sigmoid memory file for sigmoid implementation in the neural network
    
2. Generation of network weights and biases

3. Generation of test data

4. A simple script that instantiates multiple number of neuron preventing manual instantiation.


 The instantiation already have the expected name for the .mif file to be loaded. See below for the script:
 
 <img width="498" height="521" alt="image" src="https://github.com/user-attachments/assets/7ff14733-c393-4c08-a116-5b4e8b155ced" />

The parameters num_neurons and layer_num define the number of neuron instances to be created and are also used to specify the naming convention of the .mif files containing the weights and biases for each neuron.

The neural network for this example is structured like below:

<img width="844" height="605" alt="image" src="https://github.com/user-attachments/assets/03a5e046-852a-4906-a089-47d1daa144f7" />

For this example, I used pytorch to train the network:

<img width="810" height="734" alt="image" src="https://github.com/user-attachments/assets/88b71b9d-8926-4ef0-9809-8edbac89732d" />

The extraction of weights and biases are in the jupyter notebook.

The network accepts flattened inputs of the MNIST images with the first layer having 128  neurons while the third layer have 10 neurons and a max finder at the final output.

The RTL files include the following:

* neuron.v- contains the neuron implementation
* include.v-contains all the defining variables including, datawidth, numLayers, activation,etc.
* Weight_Memory.v- memory module used for loading of weights
* Sig_ROM.v- memory module used for loading of sigmoid implementation
* Layer_x- modules for each layers
* zynet.v-top level of the neural network interfaced to an AXI4 lite bus
* relu.v- ReLU implementation, you can select this if youre using relu as activation
* tb.v- testbench for simulation

See sample utilization of DSP blocks below:

<img width="892" height="718" alt="image" src="https://github.com/user-attachments/assets/ce55754a-63d9-4855-b593-d440af9a83f0" />

See sample run below:

<img width="732" height="366" alt="image" src="https://github.com/user-attachments/assets/624a7f75-968a-4870-8d9d-f80e798d5ace" />

Some notes:

* This example can be configured to have longer datawidth, more layers, weightIntWidth, etc. When adjusting the parameters of the network, make sure to adjust also the testdata parameters and sigmoid parameters to prevent erroneous results.
* The timing for this design is not closed and was still not hardawre validated on Lattice devices 
   
