# KerasWrapper
Keras bindings for Pharo

# Installing KerasWrapper

```Smalltalk
Gofer it
    smalltalkhubUser: 'ainfante' project: 'Keras-Wrapper';
    configurationOf: 'KerasWrapper';
    loadDevelopment.
```  
Also remember to follow the instructions of the Help menu to load Python, Tensorflow and Keras. Just open the world menu in Pharo and go to the Installation Guide.

# Simple Example

Here is the XOR simple example in Pharo

```Smalltalk
inputs := {{0 . 0}.
	{0 . 1}.
	{1 . 0}.
	{1 . 1}}.
expectedOutputs := {0 . 1 . 1 . 0}.
model := KNSequentialModel inputDim: 2.
model add: (KNDenseLayer neurons: 8).
model add: KNTanHActivation new.
model add: (KNDenseLayer neurons: 1).
model add: KNSigmoidActivation new.
model compileLoss: KNBinaryCrossentropyLoss new optimizer: (KNSGDOptimizer new learningRate: 0.1).
fitData := (model
		fit: inputs
		labels: expectedOutputs
		epochs: 200) waitForValue.
```

Evaluating the code produce the following:

