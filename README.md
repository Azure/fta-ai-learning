# IMPORTANT

With the end of the FastTrack for Azure program, this repository will no longer be updated and is being archived.

# FTA Azure Vision AI Session Resources

> FTA team: this resource contains examples, content, best practices and guidance
> for AI/ML

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Vision AI

To improve the efficacy of visual inspection, enterprises began turning to deep learning artificial neural networks known as convolutional neural networks (or CNNs), to emulate human vision for analysis of images and video. Today this is commonly called computer vision, or simply Vision AI. Artificial intelligence for image analytics spans a wide variety of industries, including manufacturing, retail, healthcare, and the public sector, and an equally wide area of use cases.

## Typical Vision AI Tasks

Task | Definition
------------ | -------------
Classification | Classification of objects is essential for a machine learning model to understand various classes of objects present in the video or image: for example, classifying a human, or a tennis ball is the first practical step towards analyzing the image. Examples of image classification models include ImageNet and CNNs.
Detection | Detection of objects from images or videos is a fundamental task in deep vision: typically, it involves finding a bounding box for an object. Examples of detection models include R-CNN (Region based CNN).
Segmentation | Segmentation is the next step from classification and detection, dividing the image to segments on the pixel level. Because objects are often occluded in images, with parts of one blocking another, instance segmentation helps identifying entire objects regardless of occlusion. Some examples of networks that semantic segmentation models use are Mask R-CNN.
Tracking | Object Tracking is another task in deep vision that deals with video and objects displacement over time.  
Keypoints | Keypoints detection, in particular human keypoints detection, is the task of estimating human body pose, typically based on the model that consists of human body parts and joints.
Action Recognition | Action recognition typically involves analyzing actions over time. Kinetics is an example of a dataset targeting action recognition.

## Key Considerations 

When planning a vision AI/ML architecture in Azure, there's a number of decisions a business needs to make. These considerations are important, because they can help designing scalable and efficient AI/ML vision solutions that provide accurate results, perform well under load, and optimize costs and operations for any architectural changes that may be needed in the future in different environments. A robust AI/ML solution is one that provides the same services and capabilities to a growing number of clients. With customers using Azure machine learning, a scalable architecture would provide a level of insulation not only for data, but also for compute environments, including models, training and inference configurations for multiple tenants and remain responsive under load. With the pace of adopting artificial intelligence growing very rapidly in the last few years, increased accuracy and size of machine learning models and how these models get deployed, distributed and orchestrated, there's a need in architectural guidance for accurate, reliable and scalable AI/ML solutions. 

### Scalability

Scaling a machine learning solution that is typically created as a result of experimentation by a data science team often involves two key parts: AI/ML model training and inference scaling. Each scaling scenario involves a need to increase the size of tenant and possibly, the amount of data needed to train the models and the number of clients that access the models for inference. A typical decision here is between pre-configured Azure Cognitive Services, or custom deployed via Azure Kubernetes Services (AKS) and Azure Container Instances (ACI). Solution architects need to consider how they reconcile between maintaining a sufficiently low level of complexity and designing the solution to scale with number of tenants and the size of tenants' data and workload. AI/ML vision applications may need to effectively serve clients which are distributed across the globe. The goal is optimizing your solution to run with just enough capacity for your average workload.  

### Performance

Taking advantage of Azure high-performance computing (HPC) for machine learning and AI workloads in vision scenarios. Determining compute needs for training workloads, you can decide on a specific type of VMs or hardware instance for each of your tenants. This typically involves decisions on training and inference models based on CPU, GPU, FPGA or other hardware accelerated environments. For inference, an important decision for performance is often determined by latency requirements. Depending on your needs, Azure can provide real-time inference with NVIDIA GPUs, including NVIDIA Triton Inference servers.

Key decisions for performance gains for an AI/ML solution are part of a broader machine learning architecture planning, including data strategy, personalization, operationalization and automation. Typically, as part of this wider architecture, you'll deal not only with data science specific tasks, such as model training, management and deployment, but also with needs to maintain data stores, providing a secure audited access to analytical results, release management and process automation.

Performance improvements often involve decisions on distributing and managing distributed clusters and nodes for compute tasks. Inference sizing requires [profiling capabilities](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-deploy-profile-model), provided for example by Azure Machine Learning. 

### Vision on the Edge

The rationale behind migrating workloads from the cloud to the edge for Vision AI generally falls into two categories – performance and cost. On the performance side of the equation, exfiltrating large quantities of data can cause an unintended performance strain on existing network infrastructure. Additionally, the latency of sending images and/or video streams to the cloud to retrieve results may not meet the needs of the use case. For instance, a person straying into an unauthorized area may require immediate intervention, and that scenario can affect latency when every second counts. Positioning the inferencing model near the point of ingestion, allows for near real-time scoring of the image. It also allows alerting to be performed either locally or through the cloud, depending on the network topology.
In terms of cost, sending all of the data to the cloud for analysis could significantly impact the ROI or return on investment of a Vision AI initiative. With Azure IoT Edge, a Vision AI module can be designed to only capture the relevant images with a reasonable confidence level based on the scoring. This significantly limits the amount of data being sent.

### Costs 

As with any other solution, AI/ML solutions must remain cost competitive as a component of a vision application. The goal is optimizing your solution to provide training and inference results with just enough capacity for your average workload. Generally, higher costs are incurred with the use of real-time compute resources for inference and model training. When developing a multitenant architecture, the impact on the application's operations and complexity is an important consideration and may impact costs.

Using a pre-configured service (like Azure Cognitive Services) or a pre-trained model significantly reduces initial research and development costs, sometimes saving many months in research and requiring highly qualified data scientists to train, design and optimize models. Many models are built on the shoulders of the giants, by applying a technique called transfer learning, by leveraging feature extraction layers from an existing model, and adding your own layer to predict classes from extracted features.

But using pre-built models or services is not the only way to optimize costs and operations for a machine learning solution in the context of multi-tenancy. Starting with determining compute for training workload, you can decide on a specific type of VMs or hardware instance for each of your tenants. This typically involves decisions on training and inference models based on CPU, [GPU](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-deploy-inferencing-gpus), [FPGA](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-deploy-fpga-web-service) or other hardware accelerated environments, latency requirements for inference and training of your models.

This checklist may help if you're planning cost optimization for your multitenant AI/ML solution:

Optimization Task | Description
------------ | -------------
Sizing Model Training | Determine compute size for training
Sizing Model Inference | Determine compute size for inference
Monitoring Utilization | Tune VM size by monitoring utilization
Node Clustering | Choose between local, single-node and multi-node compute
Shared Compute | Optimize cost of shared compute resources
Budgets, Cost and Quotas| Plan, manage and share budgets, cost and quota

Let's look at some common scenarios for developing a multitenant AI/ML application or service. Azure supports all of the familiar data science frameworks. Many data scientists use open source tools, such as Python, R, Lua and Julia became very popular. If you have a specific tool you like: you can alsways package your environment in an [Azure virtual machine](https://docs.microsoft.com/en-us/azure/virtual-machines/), serving a wide variety of operating systems, types of processors, storage and configurations. 

[Azure Cognitive Services](https://docs.microsoft.com/en-us/azure/cognitive-services/what-are-cognitive-services) provide a shortcut to many pretrained models and methods packaged for scale and efficiency as part of Cognitive Services APIs. Azure Cognitive Services are cloud-based services with REST APIs and client library SDKs available to help you build cognitive intelligence into your applications. You can add cognitive features to your applications without having artificial intelligence (AI) or data science skills. Azure Cognitive Services comprise various AI services that enable you to build cognitive solutions that can see, hear, speak, understand, and even make decisions. 

## Scenario: Using Cognitive Services

In this scenario (or if you mostly use inference based AI/ML solutions), your business may be just beginning using AI, and looking into ways to orchestrate multiple AI/ML models. Typically this exploration begins with inference and pre-built services, like [Azure Cognitive Services](https://azure.microsoft.com/en-us/services/cognitive-services), providing a convenient and easy interface and a collection of tested and pre-trained models. Azure Cognitive Services provide an easy start with SaaS solutions, for example [Azure Cognitive Search](https://docs.microsoft.com/en-us/azure/search/search-what-is-azure-search) offered as a service provides [design patterns for multitenant isolation](https://docs.microsoft.com/en-us/azure/search/search-modeling-multitenant-saas-applications), ease of operations (with a 99.9% SLA) and scalability. Integrating Cognitive Services is the easiest first step to any solution getting started with a multitenant AI/ML project.

Developing vision AI applications based on Cognitive Services requires effectively distributing resources, while providing a level of privacy between tenants.

* Scale and Isolation: developers need to take measures to ensure that no tenants have unauthorized or unwanted access to the data of other tenants. 

* Cloud resource costs: As with any other application, software solutions must remain cost competitive as a component of a multitenant application.

* Ease of Operations: When developing a multitenant architecture, the impact on the application's operations and complexity is an important consideration. 

* Global scale: multitenant applications may need to effectively serve tenants which are distributed across the globe.

* Scalability: Application developers need to consider how they reconcile between maintaining a sufficiently low level of application complexity and designing the application to scale with number of tenants and the size of tenants' data and workload. 

## Getting Started 

There’re several areas, or paradigms in machine learning that define most of the methods with vision AI: supervised, unsupervised and reinforcement learning. This classification is open, in fact if you dig deeply into machine learning research and theory, you’ll also discover weakly supervised, self-learning and a wealth of other methods. 

- **Supervised** learning deals with datasets that include labeled data. Typical tasks for supervised learning include classification, for example classifying activities or objects on the image. For supervised learning to work, large labeled datasets are required. Fortunately, you don’t need to do most of image classification from scratch, datasets such as ImageNet contain tens of millions labeled images, and with techniques like transfer learning, you could use them in your model.
- **Unsupervised** learning doesn’t assume that data is labeled, instead its goal is finding similarities in the data. It’s often used for self-organizing dimensionality reduction and clustering, such as K-Means. For example, if you train an unsupervised model with sufficient data containing images of athletes performing actions in different activity, such a model should be able to predict what group, or sport a given image belongs to. This method is great if you don’t have a labeled data set, but sometimes you have some labels in an unlabeled set: this scenario is often called a semi-supervised problem.
- **Reinforcement learning (RL)** applies a concept of an agent trying to achieve the goal and receiving a reward for most positive actions. Reinforcement learning originated from game theory, theory of control, and Markov Decision Process: it is widely used for robot training, including autonomous vehicles. This book goes over several applications of reinforcement learning in sports: for movement analysis, simulation and coaching. 

If you are interested in fundametals, we recommend checking [Microsoft Azure 101 Fundamentals course](https://docs.microsoft.com/en-us/learn/certifications/azure-ai-fundamentals/).


### Classification 

Classification of objects is essential for a machine learning model to understand various classes of objects present in the video or image: for example, classifying a human, or a tennis ball is the first practical step towards analyzing the image. Most image classification models are trained on ImageNet and use CNNs.

[Build a classifier usign Custom Vision](https://docs.microsoft.com/en-us/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier)

- Classification tasks ([Azure Workspace for Classification](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/classification/20_azure_workspace_setup.ipynb) | [Deployment to Azure Kubernetes Services](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/classification/22_deployment_on_azure_kubernetes_service.ipynb))

### Detection 

Detection of objects from images or videos is a fundamental task in deep vision: typically, it involves finding a bounding box for an object. Detection is usually done with R-CNN (Region based CNN).

- Detection tasks ( [Training](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/detection/01_training_introduction.ipynb) | [Deployment](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/detection/20_deployment_on_kubernetes.ipynb) | [Detecting objects in images](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/concept-object-detection) | [Brand detection](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/concept-brand-detection))

### Segmentation 

Segmentation is the next step from classification and detection, dividing the image to segments on the pixel level. Because objects are often occluded in images, with parts of one blocking another, instance segmentation helps identifying entire objects regardless of occlusion. Some examples of networks that semantic segmentation models use are Mask R-CNN.

- Segmentation tasks ( [Training](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/segmentation/01_training_introduction.ipynb) ) 

### Object Tracking

Object Tracking is another task in deep vision that deals with video and objects displacement over time. 

### Keypoints

Keypoints detection, in particular human keypoints detection, is the task of estimating human body pose, typically based on the model that consists of human body parts and joints. ( [Human Keypoints Detection](https://github.com/kevinash/ai-in-sports/blob/master/4.5_HumanBodyKeypoints.ipynb) )

### Action Recognition

Action recognition typically involves analyzing actions over time. Kinetics is an example of a dataset targeting action recognition.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
