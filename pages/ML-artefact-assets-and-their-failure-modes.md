# ML Artefact Assets and their Failure Modes

|ML Artefact Asset|Answers to [FMEA Asset Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#functions)|FMEA Failure Modes<br />(Answers to [FMEA Function Questions](https://github.com/LaraMauri/STRIDE-AI/blob/main/pages/failure-mode-and-effects-analysis-of-AI-ML-systems.md#failure-modes))|
|:---|:---|:--|
|The **_model architecture_** instantiates the ML life-cycle components and combines them to a specific multi-stage AI pipeline.|- The model architecture provides guidance for the software/hardware implementation of the AI pipeline.<br />- The model architecture must not allow inferring details of the training or inference algorithms used in the pipeline.|- The architecture may be too vague or incomplete to guide pipeline implementation.<br />- The architecture may disclose details on the interfaces between the pipeline stages.<br />-	The architecture may disclose details of the training or inference algorithm, facilitating design of vandalism or attacks.|
|The **_models hardware design_** translates the ML models parameters and hyper-parameters into a replicable microprogram, FPGA or  neuromorphic circuit design.|- The model hardware design includes the design and optimization choices for building the hardware implementation of ML models.<br />- The model hardware model must not allow inferring details of the training or inference algorithms by physical inspection.|- The model hardware design choices may support physical side-channels disclosing the model parameters as well as the details of the training or inference algorithm.|
|**_Data and metadata schemata_** are definitions of the semantics of the data entities fed to (or generated by) specific applications of ML. They may be built by specializing a top-level concept-base of standard (like ML-Schema, proposed by the W3C Machine Learning Schema Community Group).|- Data and metadata schemata support the interpretability and interoperability of data among ML models as well as back-to-back seamless connection between the stages of a AI pipeline. <br />- Data and metadata schemata must not expose the purpose of the machine learning models used in the application.|- Metadata may not deliver human interpretability or interoperability of ML models result.<br />- Metadata may facilitate the extraction of the original training set data from the model.|
|**_Learned data indexes_** are ML models to map a key to the position of a data point within a sorted or unsorted array.|- A learned index can learn the sort order or structure of lookup data points and use this information to predict the position or existence of records.<br />- The learned index should not disclose information on the data distribution.|- Learned indexes can disclose information to the data distribution.<br />- Learned indexes can smoothly degrade to low performance.|