# Azure Vision AI Resources

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

## Getting Started 

There’re several areas, or paradigms in machine learning that define most of the methods with vision AI: supervised, unsupervised and reinforcement learning. This classification is open, in fact if you dig deeply into machine learning research and theory, you’ll also discover weakly supervised, self-learning and a wealth of other methods. 

- **Supervised** learning deals with datasets that include labeled data. Typical tasks for supervised learning include classification, for example classifying activities or objects on the image. For supervised learning to work, large labeled datasets are required. Fortunately, you don’t need to do most of image classification from scratch, datasets such as ImageNet contain tens of millions labeled images, and with techniques like transfer learning, you could use them in your model.
- **Unsupervised** learning doesn’t assume that data is labeled, instead its goal is finding similarities in the data. It’s often used for self-organizing dimensionality reduction and clustering, such as K-Means. For example, if you train an unsupervised model with sufficient data containing images of athletes performing actions in different activity, such a model should be able to predict what group, or sport a given image belongs to. This method is great if you don’t have a labeled data set, but sometimes you have some labels in an unlabeled set: this scenario is often called a semi-supervised problem.
- **Reinforcement learning (RL)** applies a concept of an agent trying to achieve the goal and receiving a reward for most positive actions. Reinforcement learning originated from game theory, theory of control, and Markov Decision Process: it is widely used for robot training, including autonomous vehicles. This book goes over several applications of reinforcement learning in sports: for movement analysis, simulation and coaching. 

## Classification

Classification of objects is essential for a machine learning model to understand various classes of objects present in the video or image: for example, classifying a human, or a tennis ball is the first practical step towards analyzing the image. Most image classification models are trained on ImageNet and use CNNs.

- [Image Classification](https://github.com/microsoft/computervision-recipes/tree/master/scenarios/classification) 

## Detection

Detection of objects from images or videos is a fundamental task in deep vision: typically, it involves finding a bounding box for an object. Detection is usually done with R-CNN (Region based CNN).

- [Detect objects in images](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/concept-object-detection)
- [Brand detection](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/concept-brand-detection)

## Segmentation

Segmentation is the next step from classification and detection, dividing the image to segments on the pixel level. Because objects are often occluded in images, with parts of one blocking another, instance segmentation helps identifying entire objects regardless of occlusion. Some examples of networks that semantic segmentation models use are Mask R-CNN.

- **Segmentation** - image classification is a machine learning technique to learn and predict the category of a given image. [Segmentation](https://github.com/microsoft/computervision-recipes/tree/master/scenarios/segmentation)

## Object Tracking

Object Tracking is another task in deep vision that deals with video and objects displacement over time. 

## Keypoints

- **Human body keypoints** - [Notebook](https://github.com/kevinash/ai-in-sports/blob/master/4.5_HumanBodyKeypoints.ipynb)

## 3D Pose Estimation

## Video Action Recognition

## Azure Machine Learning

## Cognitive Services

## Deploying Machine Learning in Azure 

- **Deploying Machine Learning** - deploy ML models in Azure ([Notebook](notebooks/DeployingML.ipynb))
- [Deploying to Azure Kubernetes Service (AKS)](https://github.com/microsoft/computervision-recipes/blob/master/scenarios/classification/22_deployment_on_azure_kubernetes_service.ipynb)

## Machine Learning Pipelines

- **ML Automation** - automating ML in Azure ([Notebook](notebooks/MLAutomation.ipynb))


## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
