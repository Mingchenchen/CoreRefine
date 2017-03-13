# CoreRefine
This script generates a Resfile that allows better core packing of a protein.



## DESCRIPTION:
This script does the following:

1. prints out a Resfile that allows better core packing of a protein, the core is calculated by the SASA (solvent-accessible surface area) of each amino acid within the protein. The Resfile code should result in a better packed protein core.

Combining information from these references (2,3,8,9) I found that these chosen amino acids fits them all, thus the Resfile code is chosen as follows:
If the amino acids in the protein's core is part of the loop, then mutate the residue to one of the following amino acids:	AVILPFWM
If the amino acids in the protein's core is part of the helix, then mutate the residue to one of the following amino acids:	AVILFWM
If the amino acids in the protein's core is part of the sheet, then mutate the residue to one of the following amino acids:	AVILFWM

This script was written to run on GNU/Linux using python 3, it was not tested in Windows or MacOS.
This script will mostly be useful to refine a protein's core packing after a Rosetta FFL (Fold From Loop) computation, but can still be used to refine any protein's core.
Contact the author at sari.sabban@gmail.com for any questions regarding this script.



## HOW TO USE:
To use follow these steps:

1. Install biopython by running the following command in terminal (python3 -m pip install biopython) you need pip to be installed, if you do not have it you can install it in linux by running the following command in terminal (sudo apt-get install python3-pip).
2. Install DSSP in linux by running the following command in terminal (sudo apt-get install dssp).
3. Install numpy (python3 -m pip install numpy).
4. All files must be in the same directory as this script.
5. Run by navigating to the working directory then typing this in the command line:
`./CoreRefine.py FINENAME.pdb > Resfile`
6. Run refinement and generate 1000 structures using the following command:
`${Rosetta}/main/source/bin/rosetta_scripts.linuxgccrelease -s FILENAME.pdb -parser:protocol relax_design.xml -ex1 -ex2 -nstruct 1000`
7. The relax_design.xml script is a spesific rosetta script written in Bruno Correia's lab, contact lab to request a copy.



## REFERENCES:
1. Refere to the paper by (Koga et.al., 2012 - [PMID: 23135467](https://www.ncbi.nlm.nih.gov/pubmed/23135467)) Methods section's Sequence Design Protocol for more explanation on protein refinement and each layer's SASA parameters.
2. Refere to the paper by (Correia et.al., 2014 - [PMID: 24499818](https://www.ncbi.nlm.nih.gov/pubmed/24499818)) for details about the Rosetta Fold From Loop (FFL) protocol.
3. Refere to this [webpage](goo.gl/NsQubf) for details about Rosetta LayerDesign Protocol and which amino acids should be in which layer.
4. Refere to this [webpage](http://biopython.org/wiki/The_Biopython_Structural_Bioinformatics_FAQ) for how to use BioPython.
5. Refere to the references (Cock et.al., 2009 - [PMID: 19304878](https://www.ncbi.nlm.nih.gov/pubmed/19304878)) and (Hamelryck and Manderick, 2003 - [PMID: 14630660](https://www.ncbi.nlm.nih.gov/pubmed/14630660)) regarding the applications used here from biopython.
6. Refere to the references (Kabsch W. and Sander C., 1983 - [PMID: 6667333](https://www.ncbi.nlm.nih.gov/pubmed/6667333)) regading DSSP.
7. Refere to the reference (Tien et.al., 2013 - [PMID: 24278298](https://www.ncbi.nlm.nih.gov/pubmed/24278298)) regarding Wilke SASA parameters.
8. Refere to this [webpage](http://p53.iarc.fr/AAProperties.aspx) for the proterties of different amino acids.
9. Refere to this [webpage](http://www.bmrb.wisc.edu/referenc/choufas.shtml) for the Chou-Fasman helix/sheet propensities i.e. which secondary structure prefers which amino acids, The page information is taken from the following reference (Prevelige, P. Jr. and Fasman, G.D., "Chou-Fasman Prediction of the Secondary Structure of Proteins," in Prediction of Protein Structure and The Priniciples of Protein Conformation (Fasman, G.D., ed.) Plenum Press, New York, pp. 391-416 (1989).).