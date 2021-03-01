# ML Data Assets and their Failure Modes

|ML Data Asset|Answers to [FMEA Asset Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#functions)|FMEA Failure Modes<br />(Answers to [FMEA Function Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#failure-modes))|
|:---|:---|:--|
|**_Functional requirements_** model the domain of interest, the problem to be solved, and the task to be executed by the ML model.<br />**_Non-functional requirements_** identify architectural (hardware) and code (software) needs.|- Requirements serve to reach a clear understanding of the business context.<br />-Requirements must articulate a definition of the business goals to be achieved along with the data required to achieve them.<br />- Requirements must not identity an improper model type to be used in the AI system.<br />- Requirements must not use a metrics not suitable to assess the degree to which the goals have been achieved.|- Unclear requirements may lead to poorly accurate AI-ML models.<br />- Requirements may not take into account the adverse effect of non-functional properties mandated by regulations.<br />- Requirements may underestimate the severity of information leaks.|
|**_Raw data_** refers to any type of information gathered at the data management stage, before it is transformed or analyzed in any way.|- Raw data constitute the primary source of information needed to achieve the business goals.<br />- Raw data serve to create an initial data set (not yet ready for analysis) for use in the subsequent stages of the AI life-cycle.|- Raw data may not be sufficiently representative of the domain or unfit the AI-ML model business goal (e.g. due to sample size and population characteristics).<br />- A large volume of raw data does not always imply representativeness: if data selection is biased towards some elements that have similar characteristics (a phenomenon called selection bias) then even a large data set will not be representative enough.|
|**_Pre-processed data_** refers to raw data being transformed (cleaned, organized) so as it is ready to be used by an AI-ML model|- Pre-processed data create a data set suitable for effective statistical analyses.|- Pre-processed data may cause incorrect estimates of ML models’ performance when data preparation is applied before splitting the data for model evaluation.<br />- Performing pre-processing on the entire data set may result in data leakage, where information about test or validation data set is made available to the model in the training data set.|
|**_Labeled data_** refers to sets of scalar or multi-dimensional data items used at the model learning stage. This data is tagged with informative labels, for the purpose of training a supervised ML model.|- Labels make data useful in supervised ML setups.<br />- ML algorithms may use initial labeled data to work with additional unlabeled data.|- Labeled data fail when enough items are deleted or omitted, a sufficient number of spurious labelled data is included into the data set, or enough labels are modified.<br />- Labeled data may cause a classifier to deviate from its expected behavior.|
|**_Validation data_** is also used at the model learning stage, but differs from ordinary labeled data in usage and, usually, in collection circumstances. Validation data sets are mostly used to perform an evaluation of the ML model in-training, e.g. by stopping training (early stopping) when the error on the validation set increases too much, as this is considered a sign of over-fitting.|- Validation data provide an unbiased evaluation of a model fit on the training data set while tuning the hyper-parameters.<br />- Validation data help to deal with issues like over-fitting.|- Validation data may fail when labelled data items are manipulated.<br />- If modified, validation data items can affect how the error computed on the validation data set fluctuates during training.<br />- Even a single modification on the validation set may be enough for introducing a spurious error increase that could cut short the training.|
|**_Augmented data_** is labeled data that is complemented at the model tuning stage by additional data produced by transformations or by generative ML models. Augmentation increases labeled data sets’ diversity, which is supposed to prevent over-fitting.|- Augmented data help to solve the problem of data deficiency by increasing the amount of data available in the training data set.<br />- Data augmentation can be performed in data-space or feature-space.<br />- Augmented data are supposed to prevent over-fitting.|- Augmented data sets may fail due to inconsistency with the training set they are derived from.<br />- Heuristic data augmentation schemes are often tuned manually by humans, and defective augmentation policies may cause ML models to loose rather than gaining accuracy from the augmented data.|
|**_Held-out test cases_** (HTCs) are inputs used to test ML models in production, i.e. in the model maintenance stage. HTCs include special inputs of high interest for the application.|- The rationale for HTCs is that even if an ML model keeps showing good accuracy, its performance on specific inputs may become unacceptable.|<br />- HTCs fail when the ML model’s accuracy metrics computed on them does not correspond to the business goals of the application.<br />- Careless selection of HTCs can trigger unneeded model retraining.|
|**_Inferences_** are results computed by ML models based on real inputs, according to the task of interest in the model deployment and model maintenance stages.|- Inferences serve to produce actionable outputs when live data run into ML models.|- Inferences may fail by showing high entropy, i.e. conveying little information useful for the ML task at hand.|