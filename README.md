# supRPC
Supervised Robust Profile Clustering
Supervised Robust Profile Clustering (supRPC) model is a population-based clustering technique that adjusts for differences that may exist within different subpopulations with consideration for their assocation with a binary outcome. This is an extension of Robust Profile Clustering (RPC) technique. In the RPC model, participants are clustered at two levels: (1) globally, where subjects are assigned to an overall population-level cluster using an overfitted mixture model, and (2) locally, where variations to global patterns are accommodated via a Beta-Bernoulli process dependent on subpopulation differences. This model is jointly modeled with a probit regression model, in order to generate robust global profiles that are informed by the probabity of a positive binary outcome. 


Getting Started

The code and supporting materials are run using MATLAB software. To run the example data, you will need:

supRPC_sim499example.m - run supervised RPC and create output data
drchrnd.m - Dirichlet random generator function
truncnormrnd.m - function file to generate draw from truncated normal random distribution
sim_sRPCdataB499.mat - input simulated data source


The example dataset is a MAT-file that contains the following variables:

sampledata: 4800x50 matrix. This matrix is the input dataset containing subject level data for 50 variables. Each variable assigned a single categorical value (1,2,3,4).
trueG: binary 4x50 matrix. This matrix is used as a reference to illustrate the true probability of allocation for each variable within each subpopulation to global (ν= 1) or local (ν= 0).
subpop_samp: 4800x1 vector. This vector contains subpopulation ID for the 4800 subjects included in the dataset.
true_global: 50x3 matrix. This matrix contains the 3 global profile patterns modally expected. 
true_ci: 4800x1 matrix. This matrix contains the true global profile assignment to each subject.
true_local: 8x50 matrix. This matrix contains the two local profile patterns modally expected for each subpopulation. Rows 1-2 correspond to subpopulation 1. Rows 3-4 correspond to subpopulation 2. Rows 5-6 correspond to subpopulation 3. Rows 7-8 correspond to subpopulation 4.  
true_Li: 4800x1 matrix. This matrix contains the local profile assignment to each subject.
true_xi: 1x7 vector. This row vector contains the true coefficients of the probit regression model
true_y: 4800x1 vector. This column vector contains the true binary outcome for each subject: 1=case, 0=control.
phi_WXtrue: 4800x1 vector. This column vector contains the true probability of outcome for each subject.

Example Output

Execution of the supRPC_sim499example.m file with Example dataset (sim_sRPCdataB499.mat) should generate the following results:

Posterior median estimates of all model parameters (π,λ,θ_0,θ_1,ν,β,) saved as py_simResults499.mat
py_pred:4800x1 vector. This column vector contains the predicted probability of an outcome for each subject
pred_ci: 4800x1 vector. This column vector contains the predicted global profile assignment for each subject
pred_nu: 4x50 matrix. This matrix contains the 
DIC: Deviance Information criterion calculated based on Celeux (DIC-6) with an additional deviance penalty imposed (Spiegalhalter et al., 2014)
t_I0: 3x50 matrix. This matrix contains the predicted global profile pattern based on the posterior modes for all 50 variables. 
y_mse: This value provides the MSE of the predicted and true probability of outcome y
nu_mse: This value provides the MSE of the predicted and true probability of allocation to the global profile 

Authors

Briana Stephenson, Amy Herring, Andrew Olshan
