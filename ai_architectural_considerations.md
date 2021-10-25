# AI/ML Architectural Considerations

When planning an AI/ML architecture, there's a number of decisions a business needs to make depending on goals and key metrics that customers require. These planning considerations are important, because they can help designing scalable and efficient AI/ML solutions that provide accurate results, perform well under load, and optimize costs and operations for any architectural changes that may be needed. Look at this table of key decisions and try to identify metrics important for your business:

Metric | Description
------------ | -------------
Getting started with AI | Interested in exploration of AI/ML methods
Optimize model accuracy | Optimizing, starting with pre-trained, packaged or full custom models
Optimize costs and operations | Architectural optimization of existing AI/ML operations
Increase scale and performance | Scale/performance may depend on many factors, for example a number of users or geographic availability
Compliance and governance | Making AI/ML model comply with government or corporate policies

![Architectural Decisions](/images/key-decisions.png)

Overall these metrics and decisions for AI/ML roll into an overall machine learning architecture including data strategy, personalization, operationalization and automation.

Task | Description
------------ | -------------
Model Design and Management | Building and training models to solve ISV specific business demands
Data | Store and maintain data for ML processes, data drift triggers
Personalization | Provide secure and audited access to datasets and model analytical results
Operationalization | Deploy and manage models and datasets at scale, provide effective inferencing and training, Audit and Monitoring, Release Management
Automation | Automate all parts of the process from experimentation to model deployment and data drift management

![Architectural Decisions](/images/architectural-decisions.PNG)

## Getting Started with AI

Your business may be just beginning with AI, many customers are looking into ways to integrate AI/ML solutions. Typically this exploration begins with inference and pre-built services and models like [Azure Cognitive Services](https://azure.microsoft.com/en-us/services/cognitive-services), providing a convenient and easy interface and a collection of tested and pre-trained models.

![Getting Started](/images/getting-started.png)

## Optimize costs and operations

Using a pre-trained model significantly reduces initial research and development costs, sometimes saving many months in research and requiring highly qualified data scientists to train, design and optimize models. Many models are built on the shoulders of the giants, by applying a technique called transfer learning, by leveraging feature extraction layers from an existing model, and adding your own layer to predict classes from extracted features.

But cost optimization is not the only way to optimize costs and operations for a machine learning solution. 

Task | Description
------------ | -------------
Sizing Model Training | Determine compute size for training
Sizing Model Inference | Determine compute size for inference
Monitoring Utilization | Tune VM size by monitoring utilization
Node Clustering | Choose between local, single-node and multi-node compute
Shared Compute | Optimize cost of shared compute resources
Budgets, Cost and Quotas| Plan, manage and share budgets, cost and quota


![Optimize costs and operations](/images/costs.png)

## Optimizing model accuracy

![Optimizing Model Accuracy](/images/accuracy.png)

## Increase scale and performance

![Scale and Performance](/images/azure-portal-metrics.png)

## Compliance and governance

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

