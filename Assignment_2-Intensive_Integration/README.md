# Intensive Integration
**Adrián Barreno Sánchez (adrian.barreno@alumnos.upm.es), Pablo Mata Aroco (p.mata@alumnos.upm.es), Alberto González Delgado (alberto.gondelgado@alumnos.upm.es), Julian Elijah Politsch (julian.politsch@alumnos.upm.es), Angelo D'Angelo (angelo.dangelo@alumnos.upm.es)**


## What is Intensive Integration?

Intensive Integration is a computer program designed in ruby to searching for interactions between genes and creating a gene interaction newtork wich maximum depth is 4. In addition, the program will search for GO and KEGG annotation of these genes and it will be saved both interaction network and annotations into a file.

###  Collaborative approach
For this assignment, all the members of our group collaborated on an Interaction Network approach based on Ruby Graph Library (RGL) gem facilities, you will find a detailed description of the method below. The final outcome of this script can be seen in [collaborative_approach/documents/final_report_0.55.txt](./collaborative_approach/documents/final_report_0.55.txt).

### Individual approach
I personally worked on a second approach to build Interaction Networks using recursive functions. The differential element of this approach is the InteractionNetwork class, since the rest of the classes are adapted from the collaborative approach code. The final outcome of this script can be seen in [individual_approach/documents/Interaction_report.txt](./individual_approach/documents/Interaction_report.txt).


## Our code:

The problem of finding network modules applies to biological networks as much as any other. Modules in protein interaction networks represent a group of functionally related proteins, interacting with eachother through spacial or biological dependancy. The main problem with the so called interactome comes from how protein-protein interactions are found -biology. This problem is twofold, firstly, there is a large bias to test popular proteins for p-p interactions, such as known oncogen p52. This bias creates a scale free network of degree distribution highly skewed compared to what the real interactome might be in reality (but who knows for sure!). The second problem is the quality of p-p interactions, so called promiscuous proteins such as MHC have a tendency to interact with almost anyone due to their structure. 

Therefor, we choose to filter with a high quality threshold of 0.55, saving only those interactions which we are sure of. Since proteins dont always interact directly, we also consider paths of interaction between A and B such as A <-> X <-> B or even A <-> X <-> Y <-> B, but due to the reality of the small world hypothisis in scale free networks, more then 3 internal nodes gives meaninless results such as A <-> X <-> Y <-> Z <-> B, and are not considered.

Once the full interactome is built in $O(n^(log(n)))$ time, we search the shortest path (if it exists) between each of the *seed genes* (initial input genes). This method gives the advantage of speed, allowing us to quickly identify the functional modules in the network. It also helps us overcome the biases and problems mentioned earlier, as we only consider high quality interactions and limit the number of intermediate nodes in the shortest path. This allows us to obtain more accurate and reliable results.

After identifying the shortest paths between the seed genes, we can then group the proteins in the network into modules based on their functional relatedness. This can be done by clustering the proteins based on their connectivity patterns within the network. For example, proteins that are more densely connected with each other are likely to be functionally related and can be grouped into the same module.

Once the modules have been identified, we can then further analyze them to gain insights into the biological functions of the proteins within each module. This can be done by using tools such as Gene Ontology (GO) enrichment analysis, which can help us identify the biological processes and functions that are over-represented in the modules.

Overall, the problem of finding network modules is an important one for understanding the complex interactions within biological networks. By using methods such as filtering for high quality interactions and identifying shortest paths between seed genes, we can overcome some of the biases and challenges associated with this problem and gain valuable insights into the functional organization of biological networks.

## How to run Intensive Integration?
Download the code as [README file for assignment answers](../README.md) indicates. 

## Requirements:
[rgl-gem](https://rubygems.org/gems/rgl/versions/0.2.2?locale=es)
```
gem install rgl 
```

* [CSV-gem](https://rubygems.org/gems/csv?locale=es)

```
gem install csv
```
## Usage:

To run the program, execute the following command (inside intensive_integration/ folder), adding the arguments recquired:

```
cd assignments_answers/intensive_integration/
```
```
ruby main.rb <genes_file> <output_file> 
```
**Arguments:**
1. **[Genes_file:](documents/ArabidopsisSubNetwork_GeneList.txt)** file that provides a list of target genes that will be used for searching for interactions and annotations.
2. **Output_file**: file where the report will be saved. Here there is an  [ouput txt file using 0.55 cut-off](documents/final_report_0.55.txt) that shows the file generated by the program.

To run the program using the files contained in [files folder](documents/), just execute the following command:
```
ruby main.rb documents/ArabidopsisSubNetwork_GeneList.txt ./documents/output.txt
```
If output pathway specified already exists, the program will ask you if you want to overwrite it. Y/y (yes) or N/n (no) input is expected.



## Output
The output is verbose, it will be saved into a [output txt file](documents/). 

## References

1. https://stackoverflow.com/questions/41149008/case-insensitive-regex-matching-in-ruby
