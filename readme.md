# MiniFold
## Summary



## Running on your computer

### Re-Training (optional)
Here are the following steps in order to run the code locally or in the cloud:
1. Clone the repo: `git clone https://github.com/styloInt/ScaleProteoFold`
2. Install dependencies: `pip install -r requirements.txt`
3. Get & format the data
	1. Download data [here](https://github.com/aqlaboratory/proteinnet) (select CASP7 text-based format)
	2. Extract/Decompress the data in any directory
	3. Create the `/data` folder inside the `MiniFold` directory and copy the `training_30` file to it. Change extension to `.txt`.
4. Execute data preprocessing notebooks (`preprocessing` folder) in the following order (we plan to release simple scripts instead of notebooks very soon):
	1. `get_proteins_under_200aa.jl`:  - selects proteins under 200 residues - (you will need the [Julia programming language](https://julialang.org/) v1.0 in order to run it)
		1. **Alternatively**: `julia_get_proteins_under_200aa.ipynb` (you will need Julia as well as [iJulia](https://github.com/JuliaLang/IJulia.jl))
	3. `get_angles_from_coords_py.ipynb` - calculates dihedral angles from raw coordinates
	4. `angle_data_preparation_py.ipynb`
5. Run the models!
	1. For **distance prediction**: `predicting_distances.ipynb`
	2. For **angles prediction**: `predicting_angles.ipynb`

If you encounter any errors during installation, don't hesitate and open an [issue](https://github.com/EricAlcaide/MiniFold/issues).

### Predict proteins structures generated by a bactaria

```
	python predictsStructure/predictSequences.py filename_sequence
	
	example : python predictsStructure/predictSequences.py dnaseq.txt
```
Create the folder : predictsStructure/saveResults
It will save the results in this directory

# Limitatons
We had to compute the PSSM(Position-Specific Scoring Matrix). We need to do more extensive tests to check the function.

## Future

The future directions of the project as well as planned/work-in-progress improvements are extensively exposed in the [future.md](future.md) file. In a brief way, some promising ideas:

* Train with crops of 64x64, not windows of 200x200 (and average at prediction time).
* Use data from Multiple Sequence Alignments (MSA) such as paired changes bewteen AAs.
* Use distance map as potential input for angle prediction (or vice versa?) .
* Train with more data (in the cloud?)
* ...

*"Science is a Work In Progress."*


## Limitations

This project has been developed in one week by 1 person and,, therefore, many limitations have appeared.
They will be listed below in order to give a sense about what this project is and what it's not.

* **No usage of Multiple Sequence Alignments (MSA)**: The methods developed in this project don't use [MSA](https://en.wikipedia.org/wiki/Multiple_sequence_alignment) nor MSA-based features as input. 
* **Computing power/memory**: Development of the project has taken part in a computer with the following specs: Intel i7-6700k, 8gb RAM, NVIDIA GTX-1060Ti 6gb and 256gb of storage. The capacity for data exploration, processing, training and evaluating the models is limited.
* **GPU/TPUs for training**: The models were trained and evaluated on a single GPU. No cloud servers were used. 
* **Time**: One week of development during spare time. Ideas that might be worth testing in the future are described [here]().
* **Domain expertise**: No experts in the field. The author knows the basics of Biochemistry and Deep Learnning.
* **Data**: The average paper about Protein Structure Prediction uses a personalized dataset acquired from the Protein Data Bank (PDB). No such dataset was used. Instead, we used a subset of the [ProteinNet](https://github.com/aqlaboratory/proteinnet) dataset from CASP7. Our models are trained with just 150 proteins (distance prediction) and 600 proteins (angles prediction) due to memory constraints. 

Due to these limitations and/or constraints, the precission/accuracy the methods here developed can achieve is limited when compared against SOTA algorithms.


## References
* [DeepMind original blog post](https://deepmind.com/blog/alphafold/)
* [AlphaFold @ CASP13: “What just happened?”](https://moalquraishi.wordpress.com/2018/12/09/alphafold-casp13-what-just-happened/#s2.2)
* [Siraj Raval's YT video on AlphaFold](https://www.youtube.com/watch?v=cw6_OP5An8s)
* [ProteinNet dataset](https://github.com/aqlaboratory/proteinnet)


## Contribute
Hey there! New ideas are welcome: open/close issues, fork the repo and share your code with a Pull Request.
Clone this project to your computer:
 
`git clone https://github.com/EricAlcaide/MiniFold`
 
By participating in this project, you agree to abide by the thoughtbot [code of conduct](https://thoughtbot.com/open-source-code-of-conduct)
 
## Meta
 
* **Author's GitHub Profile**: [Eric Alcaide](https://github.com/EricAlcaide/)
* **Twitter**: [@eric_alcaide](https://twitter.com/eric_alcaide)
* **Email**: ericalcaide1@gmail.com
