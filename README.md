# FTA LIVE Azure Vision AI Session Resources

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

## Explore Vision AI with Azure

Azure supports all of the familiar data science frameworks. Many data scientists use open source tools, such as Python, R, Lua and Julia became very popular. If you have a specific tool you like: you can alsways package your environment in an [Azure virtual machine](https://docs.microsoft.com/en-us/azure/virtual-machines/), serving a wide variety of operating systems, types of processors, storage and configurations. 

[Azure Cognitive Services](https://docs.microsoft.com/en-us/azure/cognitive-services/what-are-cognitive-services) provide a shortcut to many pretrained models and methods packaged for scale and efficiency as part of Cognitive Services APIs. Azure Cognitive Services are cloud-based services with REST APIs and client library SDKs available to help you build cognitive intelligence into your applications. You can add cognitive features to your applications without having artificial intelligence (AI) or data science skills. Azure Cognitive Services comprise various AI services that enable you to build cognitive solutions that can see, hear, speak, understand, and even make decisions. 

## Getting Started 

There’re several areas, or paradigms in machine learning that define most of the methods with vision AI: supervised, unsupervised and reinforcement learning. This classification is open, in fact if you dig deeply into machine learning research and theory, you’ll also discover weakly supervised, self-learning and a wealth of other methods. 

- **Supervised** learning deals with datasets that include labeled data. Typical tasks for supervised learning include classification, for example classifying activities or objects on the image. For supervised learning to work, large labeled datasets are required. Fortunately, you don’t need to do most of image classification from scratch, datasets such as ImageNet contain tens of millions labeled images, and with techniques like transfer learning, you could use them in your model.
- **Unsupervised** learning doesn’t assume that data is labeled, instead its goal is finding similarities in the data. It’s often used for self-organizing dimensionality reduction and clustering, such as K-Means. For example, if you train an unsupervised model with sufficient data containing images of athletes performing actions in different activity, such a model should be able to predict what group, or sport a given image belongs to. This method is great if you don’t have a labeled data set, but sometimes you have some labels in an unlabeled set: this scenario is often called a semi-supervised problem.
- **Reinforcement learning (RL)** applies a concept of an agent trying to achieve the goal and receiving a reward for most positive actions. Reinforcement learning originated from game theory, theory of control, and Markov Decision Process: it is widely used for robot training, including autonomous vehicles. This book goes over several applications of reinforcement learning in sports: for movement analysis, simulation and coaching. 

## Vision AI Tasks in Azure

Task | Definition
------------ | -------------
Classification | Classification of objects is essential for a machine learning model to understand various classes of objects present in the video or image: for example, classifying a human, or a tennis ball is the first practical step towards analyzing the image. Examples of image classification models include ImageNet and CNNs.
Detection | Detection of objects from images or videos is a fundamental task in deep vision: typically, it involves finding a bounding box for an object. Examples of detection models include R-CNN (Region based CNN).
Segmentation | Segmentation is the next step from classification and detection, dividing the image to segments on the pixel level. Because objects are often occluded in images, with parts of one blocking another, instance segmentation helps identifying entire objects regardless of occlusion. Some examples of networks that semantic segmentation models use are Mask R-CNN.
Tracking | Object Tracking is another task in deep vision that deals with video and objects displacement over time.  
Keypoints | Keypoints detection, in particular human keypoints detection, is the task of estimating human body pose, typically based on the model that consists of human body parts and joints.
Action Recognition | Action recognition typically involves analyzing actions over time. Kinetics is an example of a dataset targeting action recognition.


## Classification Tasks

Classification of objects is essential for a machine learning model to understand various classes of objects present in the video or image: for example, classifying a human, or a tennis ball is the first practical step towards analyzing the image. Most image classification models are trained on ImageNet and use CNNs.

- Classification tasks ([Azure Workspace for Classification](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/classification/20_azure_workspace_setup.ipynb) | [Deployment to Azure Kubernetes Services](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/classification/22_deployment_on_azure_kubernetes_service.ipynb))

## Detection Tasks

Detection of objects from images or videos is a fundamental task in deep vision: typically, it involves finding a bounding box for an object. Detection is usually done with R-CNN (Region based CNN).

- Detection tasks ( [Training](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/detection/01_training_introduction.ipynb) | [Deployment](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/detection/20_deployment_on_kubernetes.ipynb) | [Detecting objects in images](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/concept-object-detection) | [Brand detection](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/concept-brand-detection))

## Segmentation Tasks

Segmentation is the next step from classification and detection, dividing the image to segments on the pixel level. Because objects are often occluded in images, with parts of one blocking another, instance segmentation helps identifying entire objects regardless of occlusion. Some examples of networks that semantic segmentation models use are Mask R-CNN.

- Segmentation tasks ( [Training](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/segmentation/01_training_introduction.ipynb) ) 

## Object Tracking

Object Tracking is another task in deep vision that deals with video and objects displacement over time. 

## Keypoints

Keypoints detection, in particular human keypoints detection, is the task of estimating human body pose, typically based on the model that consists of human body parts and joints. ( [Human Keypoints Detection](https://github.com/kevinash/ai-in-sports/blob/master/4.5_HumanBodyKeypoints.ipynb) )

## Action Recognition

Action recognition typically involves analyzing actions over time. Kinetics is an example of a dataset targeting action recognition.

## Managing Models in Azure

The term CI/CD (Continuous Integration/Continuous Delivery) many times referring to the development cycle in machine learning, and in this section we’ll be going over some practical examples of taking your research to the level of best practices and standards used in modern data science. 

## Deploying Machine Learning in Azure 

The first step in deploying your models is registering them in the workspace, this saves them in the cloud so they can be used later from your code:

```python

from azureml.core.model import Model

model = Model.register(model_path = "./models",
             model_name = "TestModel",
             description = "Classification",
             workspace = workspace)

```

Now, referencing your models becomes easy, simply pass your workspace and model name and in your code, you have a reference to the model:

```python

model = Model(workspace, 'TestModel')

```
You can check the path in the cloud of the model you just deployed, note that registration automatically versions your models:

```python
Model.get_model_path('TestModel', _workspace=workspace)
```

The location of your registered model in the workspace will become important in the next steps, because you’ll need to reference this model in your scoring script’s initialization, when this model is loaded by your service.

- More on deploying ML models in Azure ( [Notebook](notebooks/DeployingML.ipynb) | [Deploying to Azure Kubernetes Service](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/classification/22_deployment_on_azure_kubernetes_service.ipynb) )
 

## Machine Learning Pipelines

- **ML Automation** - automating ML in Azure ([Notebook](notebooks/MLAutomation.ipynb))

## Cognitive Services

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
