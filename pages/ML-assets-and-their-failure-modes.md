# ML Assets and their Failure Modes

- [Data](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/ML-data-assets-and-their-failure-modes.md#data)
- [Models](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/ML-data-assets-and-their-failure-modes.md#models)
- [Artefacts](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/ML-data-assets-and-their-failure-modes.md#artefacts)

## Data

|ML Data Asset|Answers to [FMEA Asset Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#functions)|FMEA Failure Modes<br />(Answers to [FMEA Function Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#failure-modes))|
|:---|:---|:---|
|**_Functional requirements_** model the domain of interest, the problem to be solved, and the task to be executed by the ML model. **_Non-functional requirements_** identify architectural (hardware) and code (software) needs.|<ul><li> Requirements serve to reach a clear understanding of the business context. </li><li> Requirements must articulate a definition of the business goals to be achieved along with the data required to achieve them. </li><li> Requirements must not identity an improper model type to be used in the AI system. </li><li> Requirements must not use a metrics not suitable to assess the degree to which the goals have been achieved. </li></ul> | <ul><li> Unclear requirements may lead to poorly accurate AI-ML models. </li><li> Requirements may not take into account the adverse effect of non-functional properties mandated by regulations. </li><li> Requirements may underestimate the severity of information leaks. </li></ul>|
|**_Raw data_** refers to any type of information gathered at the data management stage, before it is transformed or analyzed in any way.| <ul><li> Raw data constitute the primary source of information needed to achieve the business goals. </li><li> Raw data serve to create an initial data set (not yet ready for analysis) for use in the subsequent stages of the AI life-cycle. </li></ul> | <ul><li> Raw data may not be sufficiently representative of the domain or unfit the AI-ML model business goal (e.g. due to sample size and population characteristics). </li><li> A large volume of raw data does not always imply representativeness: if data selection is biased towards some elements that have similar characteristics (a phenomenon called selection bias) then even a large data set will not be representative enough. </li></ul> |
|**_Pre-processed data_** refers to raw data being transformed (cleaned, organized) so as it is ready to be used by an AI-ML model| <ul><li> Pre-processed data create a data set suitable for effective statistical analyses. </li></ul> | <ul><li> Pre-processed data may cause incorrect estimates of ML models’ performance when data preparation is applied before splitting the data for model evaluation. </li><li> Performing pre-processing on the entire data set may result in data leakage, where information about test or validation data set is made available to the model in the training data set. </li></ul> |
|**_Labeled data_** refers to sets of scalar or multi-dimensional data items used at the model learning stage. This data is tagged with informative labels, for the purpose of training a supervised ML model. | <ul><li> Labels make data useful in supervised ML setups. </li><li> ML algorithms may use initial labeled data to work with additional unlabeled data. </li></ul> | <ul><li> Labeled data fail when enough items are deleted or omitted, a sufficient number of spurious labelled data is included into the data set, or enough labels are modified. </li><li> Labeled data may cause a classifier to deviate from its expected behavior. </li></ul> |
|**_Validation data_** is also used at the model learning stage, but differs from ordinary labeled data in usage and, usually, in collection circumstances. Validation data sets are mostly used to perform an evaluation of the ML model in-training, e.g. by stopping training (early stopping) when the error on the validation set increases too much, as this is considered a sign of over-fitting.| <ul><li> Validation data provide an unbiased evaluation of a model fit on the training data set while tuning the hyper-parameters. </li><li> Validation data help to deal with issues like over-fitting. </li></ul> | <ul><li> Validation data may fail when labelled data items are manipulated. </li><li> If modified, validation data items can affect how the error computed on the validation data set fluctuates during training. </li><li> Even a single modification on the validation set may be enough for introducing a spurious error increase that could cut short the training. </li></ul> |
|**_Augmented data_** is labeled data that is complemented at the model tuning stage by additional data produced by transformations or by generative ML models. Augmentation increases labeled data sets’ diversity, which is supposed to prevent over-fitting.| <ul><li> Augmented data help to solve the problem of data deficiency by increasing the amount of data available in the training data set. </li><li> Data augmentation can be performed in data-space or feature-space. </li><li> Augmented data are supposed to prevent over-fitting. </li></ul> | <ul><li> Augmented data sets may fail due to inconsistency with the training set they are derived from. </li><li> Heuristic data augmentation schemes are often tuned manually by humans, and defective augmentation policies may cause ML models to loose rather than gaining accuracy from the augmented data. </li></ul> |
|**_Held-out test cases_** (HTCs) are inputs used to test ML models in production, i.e. in the model maintenance stage. HTCs include special inputs of high interest for the application.| <ul><li> The rationale for HTCs is that even if an ML model keeps showing good accuracy, its performance on specific inputs may become unacceptable. </li></ul> | <ul><li> HTCs fail when the ML model’s accuracy metrics computed on them does not correspond to the business goals of the application. </li><li> Careless selection of HTCs can trigger unneeded model retraining. </li></ul> |
|**_Inferences_** are results computed by ML models based on real inputs, according to the task of interest in the model deployment and model maintenance stages.| <ul><li> Inferences serve to produce actionable outputs when live data run into ML models. </li></ul> | <ul><li> Inferences may fail by showing high entropy, i.e. conveying little information useful for the ML task at hand. </li></ul>|

## Models

|ML Model Asset|Answers to [FMEA Asset Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#functions)|FMEA Failure Modes<br />(Answers to [FMEA Function Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#failure-modes))|
|:---|:---|:--|
|**_Hyper-parameters_** (HPs) are meta parameters associated with any AI-ML algorithm that do not have dependency on the input data, and whose value is set before the learning process begins. They are defined by trial-and-error using model space search techniques.| <ul><li> HPs are used for model-space search and identification of the best AI-ML model. </li><li> Their value defines the training and structure of the AI-ML model. </li><li> HPs should not change during training. </li></ul> | <ul><li> HPs may fail to deliver the size and configuration for the model that makes its training and operation feasible. </li><li> HPs may be used as fitting knobs, e.g. tampering with them to make the model over-fitted to specific training data. </li></ul> |
|**_Model parameters_** are variables that are internal to the model (e.g., the weights in a NN, or the centroids in a clustering algorithms) and whose value can be computed by fitting the given input data to the model.| <ul><li> Parameters determine the inferences (i.e. the actual outputs) computed by the AI-ML model. </li><li> Parameters should not reveal information about the training data or the HPs. </li></ul> | <ul><li> Parameters fail when the AI-ML model’s output computed according to them is such that the model’s performance in executing the task (classification, prediction, anomaly detection) is poor. </li><li> Parameters can be used as covert channels to encode hidden information in the inferences. </li></ul> |
|**_Data pre-processing algorithms_** are techniques employed to improve information quality by cleaning, integrating and transforming data.| <ul><li> Data pre-processing has the purpose to convert incomplete or defective raw data into improved training data to provide improved AI-ML model’s performance. </li><li> The data pre-processing algorithm should not degrade raw data value. </li><li> Data pre-processing should not harvest information about the data statistics. </li></ul> | <ul><li> Data pre-processing algorithms fail when errors in the definition of the data conversion generate flawed or defective training data. </li><li> Data pre-processing may be used to achieve other data properties (e.g., anonymity). </li></ul> |
|**_Trained models_** are AI-ML supervisioned models whose internal parameters have been adjusted by training to achieve a minimum of the error function that defines the distance between actual and expected outputs.| <ul><li> Trained models perform a task (like regression, prediction or anomaly detection) computing inferences on test input data. </li></ul> | <ul><li> Trained models fail when the discrepancy between the training data seen during the learning process and inference is so high to cause a drop in performance in production. </li></ul> |
|**_Deployed models_** are AI-ML supervisioned models whose parameters are assumed to be stable, and to which users can submit inputs and receive inference outputs.| <ul><li> Deployed models perform a task (like regression, prediction or anomaly detection) computing inferences in production. </li></ul> | <ul><li> Deployed models fail when the AI-ML task is not performed at the desired performance (e.g. accuracy) level. </li><li> Deployed models can be doctored to compute inferences aimed to benefit malicious third parties. </li></ul> |

## Artefacts

|ML Artefact Asset|Answers to [FMEA Asset Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#functions)|FMEA Failure Modes<br />(Answers to [FMEA Function Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#failure-modes))|
|:---|:---|:--|
|The **_model architecture_** instantiates the ML life-cycle components and combines them to a specific multi-stage AI pipeline.| <ul><li> The model architecture provides guidance for the software/hardware implementation of the AI pipeline. </li><li> The model architecture must not allow inferring details of the training or inference algorithms used in the pipeline. </li></ul> | <ul><li> The architecture may be too vague or incomplete to guide pipeline implementation. </li><li> The architecture may disclose details on the interfaces between the pipeline stages. </li><li>	The architecture may disclose details of the training or inference algorithm, facilitating design of vandalism or attacks. </li></ul> |
|The **_models hardware design_** translates the ML models parameters and hyper-parameters into a replicable microprogram, FPGA or neuromorphic circuit design.| <ul><li> The model hardware design includes the design and optimization choices for building the hardware implementation of ML models. </li><li> The model hardware model must not allow inferring details of the training or inference algorithms by physical inspection. </li></ul> | <ul><li> The model hardware design choices may support physical side-channels disclosing the model parameters as well as the details of the training or inference algorithm. </li></ul> |
|**_Data and metadata schemata_** are definitions of the semantics of the data entities fed to (or generated by) specific applications of ML. They may be built by specializing a top-level concept-base of standard (like ML-Schema, proposed by the W3C Machine Learning Schema Community Group). | <ul><li> Data and metadata schemata support the interpretability and interoperability of data among ML models as well as back-to-back seamless connection between the stages of a AI pipeline. </li><li> Data and metadata schemata must not expose the purpose of the machine learning models used in the application. </li></ul> | <ul><li> Metadata may not deliver human interpretability or interoperability of ML models result. </li><li> Metadata may facilitate the extraction of the original training set data from the model. </li></ul> |
|**_Learned data indexes_** are ML models to map a key to the position of a data point within a sorted or unsorted array.| <ul><li> A learned index can learn the sort order or structure of lookup data points and use this information to predict the position or existence of records. </li><li> The learned index should not disclose information on the data distribution. </li></ul> | <ul><li> Learned indexes can disclose information to the data distribution. </li><li> Learned indexes can smoothly degrade to low performance. </li></ul> |
