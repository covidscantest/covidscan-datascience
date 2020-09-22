# **How It Works**
The goal of this project was to harness advancements in Machine Learning to help fight the COVID-19 pandemic by making Deep Learning Neural Networks easy to use for everyone.

# About the system
1. The Web Application
This allows users to upload scans and run prediction models in a web browser.

# 2. Machine Learning Algorithms
These consist of 4 phases, each with a specific analysis occurring:

The first phase predicts the probability of the image being an xray scan at all. We use a CNN (convolutional neural network) that we trained on a set of images that was a mix of xray scans and images of random objects.
The second phase predicts the probability of the image being an xray of healthy lungs. This phase uses DenseNet201 trained on the CheXpert dataset where labels were reduced to binary outcomes (healthy/unhealthy).
The third phase is similar to phase 2, with the exception that it focused on detection pneumonia and other conditions. The same architecture (DenseNet201) and dataset was used (CheXpert).
The last phase is a DenseNet201 network trained on a COVID-19 xray dataset.
Final probabilities are calculated based on the output of each phase, by multiplying the "not detected" outcome of previous phase by the "detected" outcome of current phase.

The table below shows an example with the calculation of the results

Analysis	Probability	Output
Healthy / unhealthy	60%	60%
Pneumonia	50%	20% (50% x 40%)
COVID-19	10%	2% (10% x 20%)
other	--	18% (remaining)

Related links:
Web app source code
Machine learning notebooks
Large Chest X-Ray Dataset https://stanfordmlgroup.github.io/competitions/chexpert/
Hierarchical-Learning-V1 (ensemble) Vingroup Big Data Institute https://arxiv.org/abs/1911.06475
COVID X-Ray dataset https://github.com/ieee8023/covid-chestxray-dataset
Covid detection using Tensorflow https://rubikscode.net/2020/03/23/detection-of-covid-19-in-chest-x-rays-with-deep-learning/

#Final summary
We hope someone will find our work useful either from detection, learning, reference or any other aspect. Keep in mind that this is open source software and you use it at your own risk. Machine learning is a powerful technique, but it is not ultimate truth since every algorithm it has it's limitations as far as predicting power goes. Stay safe and healthy.
