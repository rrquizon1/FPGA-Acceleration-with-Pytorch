This repository is very simialr to the original repo here [here](https://github.com/rrquizon1/FPGA-Acceleration-Study/)

The main difference is using pytorch framework instead of tensorflow keras. This gives me flexibility as a I move to further neural network architectures such as CNN as I am more familiar with pytorch framework. 

The RTL structure of the neuron closely resembles the original implementation. In this example, I successfully implemented a network that differs from the one in the original tutorial, demonstrating a deeper understanding of the design.

The jupyter notebook trainNN.ipynb generates the following:

1. Generation of sigmoid memory file for sigmoid implementation in the neural network
    
2. Generation of network weights and biases

3. Generation of test data

4. A simple script that instantiates multiple number of neuron preventing manual instantiation.


 The instantiation already have the expected name for the .mif file to be loaded.

 

 The neural network for this example is structured like below:
<img width="844" height="605" alt="image" src="https://github.com/user-attachments/assets/03a5e046-852a-4906-a089-47d1daa144f7" />

For this example, I used pytorch to train the network:
<img width="810" height="734" alt="image" src="https://github.com/user-attachments/assets/88b71b9d-8926-4ef0-9809-8edbac89732d" />

