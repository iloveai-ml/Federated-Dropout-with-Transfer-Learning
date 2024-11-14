
# Summary

This notebook is an implementation of the paper titled  "Federated Dropout – A Simple Approach for Enabling Federated Learning on Resource Constrained Devices" (https://arxiv.org/abs/2109.15258)

The paper presents a novel methodology aimed at addressing the challenges of Federated Learning (FL) on devices with limited computational resources. The authors propose a technique called Federated Dropout (FedDrop), which builds upon the traditional dropout method used in deep neural networks (DNNs) to enhance performance while reducing both communication and computation overhead.

##Overview of the Methodology

### Problem Statement
Federated Learning involves training models across multiple devices while keeping data localized to enhance privacy. However, two main bottlenecks hinder its effectiveness:
Communication Bottleneck: High-dimensional model updates require significant bandwidth.
Computation Bottleneck: Resource-constrained devices struggle with the intensive computations needed for model updates.

 ### FedDrop Concept
FedDrop aims to mitigate these bottlenecks by utilizing a dropout mechanism to create subnets from a global model, allowing devices to train smaller models instead of the full-scale DNN. This approach includes several key features:

1. Subnet Distribution: The server generates multiple subnets using dropout techniques, each assigned to different devices. This allows devices to work with smaller models, thereby reducing computational demands.

2. Subnet Aggregation: After local updates, the server aggregates these subnets to update the global model, ensuring that all updates contribute to improving overall performance.

3. C2 Awareness: The dropout rates for each device are adapted based on their communication and computation capabilities, optimizing performance while managing latency.

### Implementation Steps

1. The implementation of FedDrop follows these sequential steps in each training round:

2. Subnet Generation: The server randomly generates subnets using dropout, assigning one subnet per device.

3. Model Downloading: Devices download their respective subnets from the server.

4. Local Model Updating: Each device updates its local subnet using its local dataset.

5. Local Model Uploading: Updated subnets are sent back to the server.

6. Global Model Updating: The server aggregates the updated subnets to refine the global model.


### Performance Evaluation

Experiments conducted within the paper demonstrate that FedDrop can significantly improve learning performance compared to traditional FL methods, particularly in cases of overfitting and when using uniform dropout strategies. For instance, it showed an accuracy increase of 2.5% when training on the Cifar-10 dataset under certain conditions.

## Conclusion

The FedDrop approach effectively addresses both communication and computation challenges in Federated Learning by leveraging adaptive subnet generation through dropout techniques. This innovation not only enhances model training efficiency but also maintains privacy and reduces resource demands on edge devices.
