# BIOMD0000000268: Reed2008

## Installation

Download this repository, and install with distutils

`python setup.py install`

Or, install using pip

`pip install git+https://github.com/biomodels/BIOMD0000000268.git`

To install a specific version (in this example, from the 2014-09-16 BioModels release)

`pip install git+https://github.com/biomodels/BIOMD0000000268.git@20140916`


# Model Notes


This is the model described in the article:  
**A mathematical model of glutathione metabolism.**   
Michael C Reed, Rachel L Thomas, Jovana Pavisic, S. Jill James, Cornelia M
Ulrich and H. Frederik Nijhout, _Theor Biol Med Model_ 2008,5:8;
PubmedID:[18442411](http://www.ncbi.nlm.nih.gov/pubmed/18442411) ;
DOI:[10.1186/1742-4682-5-8](http://dx.doi.org/10.1186/1742-4682-5-8);  
Abstract:  
BACKGROUND: Glutathione (GSH) plays an important role in anti-oxidant defense
and detoxification reactions. It is primarily synthesized in the liver by the
transsulfuration pathway and exported to provide precursors for in situ GSH
synthesis by other tissues. Deficits in glutathione have been implicated in
aging and a host of diseases including Alzheimer's disease, Parkinson's
disease, cardiovascular disease, cancer, Down syndrome and autism.  
APPROACH: We explore the properties of glutathione metabolism in the liver by
experimenting with a mathematical model of one-carbon metabolism, the
transsulfuration pathway, and glutathione synthesis, transport, and breakdown.
The model is based on known properties of the enzymes and the regulation of
those enzymes by oxidative stress. We explore the half-life of glutathione,
the regulation of glutathione synthesis, and its sensitivity to fluctuations
in amino acid input. We use the model to simulate the metabolic profiles
previously observed in Down syndrome and autism and compare the model results
to clinical data.  
CONCLUSION: We show that the glutathione pools in hepatic cells and in the
blood are quite insensitive to fluctuations in amino acid input and offer an
explanation based on model predictions. In contrast, we show that hepatic
glutathione pools are highly sensitive to the level of oxidative stress. The
model shows that overexpression of genes on chromosome 21 and an increase in
oxidative stress can explain the metabolic profile of Down syndrome. The model
also correctly simulates the metabolic profile of autism when oxidative stress
is substantially increased and the adenosine concentration is raised. Finally,
we discuss how individual variation arises and its consequences for one-carbon
and glutathione metabolism.

parameter | orig. article  |  this model  
---|---|---  
Vm_CBS  | 700000  | 420000  
Vm_GNMT  | 245  | 260  
K_sam_GNMT | 32  | 63  
Vr_MTD(mito) | 600000  | 595000  
V_CBS | kinetic law | rearranged  
V_bmetc | 913 | 913.4  
Vm_GR | 8925 | 892.5  
  
This version of the model contains a feeding rhythm as used in figure 5 of the
original article. Four parameters, _breakfast_, _lunch_ _dinner_ and
_fasting_, describe the relative level of amino acids, described by the
parameter _aa_input_ or _Aminoacid_input_, in the blood. To remove the daily
feeding rhythm, either set the parameters for meals and fasting to 1 (or for
figure 3 to 0.333), or remove the assignment rule for the _Aminoacid_input_.
For the steady state evaluations for figure 6, the mealtime parameters were
set to one, which, while making Copasi complain about explicit time
dependency, still gives valid results.

This version of the model differs slightly from the version described in the
supplement, in which contains some typos. It was corrected using the version
of [JWS-online](http://jjj.mib.ac.uk/), created using the original matlab
files, thankfully provided by the articles authors. Many thanks to Jacky Snoep
for his help and support.

In the SBML version of the model the volumes of the mitochondrion, the
cytoplasm and the cell were all set to one to obtain the same equations as
described in the supplemental materials of the article. The total folate is
equally split between the cytosol and the mitochondrion and divided by 3/4 for
the cytosol and 1/4 for the mitochondrion, respectively. To obtain an SBML
model in which the volumes of the compartments, _cytosol_ and _mito_, are
used, the model needs to be altered as follows:  

  * for the initial distribution of folate the terms 3/4 and 1/4 have to be replaced by volumes of cytosol and mitochondria respectively
  * in the transport reactions between mitochondrion and cytosol the stoichiometry of the mitochondrial reactants has to be set from 3 to 1 and in the first part of the according rate laws the factor _mito/3_ should simply be replaced with _mito_.
  * the stoichiometries of _src_ and _dmg_ have to be changed to _cell/mito_ for mitchondrial and _cell/cytosol_ for cytosolic reactions involving these two species (for the relative volumes used in the article this would be 4 for mitochondrial reactions and 1.33333 for cytosolic ones).
While the concentrations stay the same after these alteration, the reaction
fluxes change by a factor of _cytosol_ and _mito_ for cytosolic and
mitchondrial reactions, respectively.

Originally created by libAntimony v1.3 (using libSBML 3.4.1)


