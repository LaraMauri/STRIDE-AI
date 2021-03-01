# Mapping Artefact Assets' Failure Modes to CIA<sup>3</sup>-R Hexagon

| Asset | Properties | Threats | Known attacks|
|:---|:---|:---|:---|
|Model architecture|Authenticity,<br />Confidentiality|Spoofing,<br />Disclosure|Man-in-the-Middle attacks use knowledge of the pipeline structure and interfaces to inject malicious data tailored to maximise damage.|
|Model hardware design|Confidentiality|Disclosure|Side-Channel attacks to ML hardware implementations attacks use physical observation of the hardware operation to  estimate parameters of the ML model implemented by the circuit.|
|Data and metadata schemata|Confidentiality|Disclosure|Model inversion attacks exploit knowledge about a model’s input features (e.g. representation interval, types) for carry out extraction of the original training set data from the model.|
|Data indexes|Integrity|Tampering|Index poisoning attacks target the learned index’s data probability distributions to imperceptibly degrade the index performance.|
