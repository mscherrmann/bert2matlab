# Export BERT models from Huggingface to Matlab for NLP

This toolbox exports pre-trained BERT transformer models from Python into Matlab and stores the models such that they can be directly used with the Mathworks' BERT implementation. 
This allows for example to use a pre-trained German BERT model (like GBERT) from HuggingFace and use it directly for NLP applications, without having to rely on accessing Python from Matlab:
* We have tested to export models from PyTorch and TensorFlow. 
* Pre-trained models for a downstream task are supported. This comprises text-classification (e.g.multiclass or multilabel models), token-classification (e.g. for named entity recognition NER) or question-answering models.   
* Models with a different structure then BERT (like Roberta etc.) are not supported.
* Only models that use the word-piece tokenizer are currently supported.

The workflow comprises:
* Install Python (we have only tested Python 3.9.x)
* Extract the toolbox in a specific folder (e.g. “exportBertToMatlab”) and add it to the Matlab path. 
* Generate an environment using the “bert2matlab.yml” provided in our “Python”-folder. This installs PyTorch, TensorFlow, and HuggingFace’s “transformers” libraries, to be able to import the pre-trained Python models. GPU support is not necessary. 
* A specific IDE is not necessary to export models, you can use the Python command line interface. 
* For example, these commands will export a plain, pre-trained German BERT model from HuggingFace, where the import syntax consists of the HuggingFace model name, the type of model (“none”, “text-classification”, or “token-classification”), and the model format (“tf” or “pt”):

		# Open command window
		cd "...\exportBertToMatlab\Python
		python
		# Plain pre-trained BERT model
		from helperFunctions import modelToMatlab 
		modelToMatlab("bert-base-german-cased",None,"tf") #(tensorflow model)

* For the Python syntax to import a model from HugingFace, see the included "MinimalExample.txt" file.
* Use the "readBertFromPython.m" function to load the model into Matlab and use powerful NLP.

By default, the models are imported into the subfolder “Models”, but you can optionally provide any path where to store the imported model.
We provide demo files to test the imported models both in Python as well as in Matlab (after import). 


We have tested to import several models, comprising plain BERT models and models with downstream tasks for NER, sentiment, multilabel classification etc. But we cannot guarantee that the code works for all BERT implementations. 
The code is provided solely for illustrative purposes. We can neither guarantee that it works nor that it's free of errors, and do not take on any liability. 
The code/toolbox is licensed under the BSD License.
Cite As

Moritz Scherrmann (2023). export BERT to MATLAB: Load pre-trained BERT models (https://www.mathworks.com/matlabcentral/fileexchange/125305-export-bert-to-matlab-load-pre-trained-bert-models), MATLAB Central File Exchange. Retrieved April 28, 2023.
