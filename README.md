# Active probing to highlight approaching transitions to ictal states in coupled neural mass models

This repository contains a Python translation of Wendling's CA1 neural mass model [[1]](https://doi.org/10.1046/j.1460-9568.2002.01985.x) and it's modified version to generate figures in the Manuscript "Active probing to highlight approaching transitions to ictal states in coupled neural mass models". This manuscript evaluates the use of probing stimuli for seizure forecasting in this neuronal computational model. This is done by simulating the model's simulated neuronal activity (or simulated local field potential - LFP) while it's dynamics gradually shift from normal neuronal activity towards an ictal (or seizure) state. In general, this gradual change of underlying system parameters is not observable just by looking at features extracted from the model's output, but is detectable when perturbations are applied to it. 

The original model consists which consists of four coupled population subsets and based on the global cellular organization of the hippocampus; excitatory main cells (pyramidal cells), excitatory interneurons, inhibitory neurons with slow kinetics (O-LM neurons, with IPSCs mediated by dendritic synapses) and inhibitory neurons with fast kinetics (soma-projecting Basket Cells). The model input is white noise applied to the main excitatory cells. One instance of this model is referred to as a population set. 

In the modified model, two population sets are coupled through main excitatory cells with a coupling gain K. Periodic stimuli are summed to the original model's white noite input to main excitatory cells. Thoughout a simulation, t

Following the manuscript's methods:
1. Activity of two population sets is simulated, while a specific parameter (excitability, slow inhibition or coupling gain) is linearly changed from the beginning up to the end of the simulation. Probing stimuli are applied to one or both population sets every 2 seconds. Different simulations are done, increasing stimulation amplitude.
2. From the simulated LFP of instances from each model configuration, extract a set of features: variance, skewness, kurtosis, lag-1 autocorrelation from each population set, and mutual information between the neuronal activity of both population sets.
3. plot resulting feature series for some stimuli amplitude values
4. correlate feature series with parameter varied to induce seizure state (or simulation time)


**SimFeatures.py** does steps 1 and 2 - simulate several model configurations (I-A,I-B,I-K, II-A,II-B,II-K) and save extracted features from each one to .npy files. Correlation measures between features and shifted parameters are also calculated and saved to .pkl files. Block 3 of the script simulates an instance of the model in configuration I-A with and without probing stimuli to generate Figure 2 from the paper.

**Make_figs.py** loads the extracted features and generates the figures showed in the manuscript.



Vinícius Rezende Carvalho
Núcleo de Neurociências
Programa de Pós-Graduação em Engenharia Elétrica - UFMG
vrcarva@ufmg.br
vrezendecarvalho@mgh.harvard.edu
