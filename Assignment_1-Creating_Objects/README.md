# Creating Objects

**Adrián Barreno Sánchez (adrian.barreno@alumnos.upm.es), Pablo Mata Aroco (p.mata@alumnos.upm.es), Alberto González Delgado (alberto.gondelgado@alumnos.upm.es)**

## What is Creating Objects?

Creating Objects is a computer program designed in ruby to simulate planting 7g of seeds from a seed stock geneback, uptading the genebank information. In addition, the program is designed for proceesing the information and determinate which genes are genetically-linked. 

## How to run Creating Objects?

To run the program, execute the following command inside the current directory, adding the arguments recquired:

```
ruby Proccessing.rb <seed_stock_data_file> <gene_information_file> <cross_data_file> <output_file> 
```
**Arguments:**
1. **[Seed stock data file:](files/seed_stock_data.tsv)** file where current information of the seed stock genebank is located.
2. **[Gene information file:](files/gene_information.tsv)** file where information of mutants phenotypes is included.
3. **[Cross data file:](files/cross_data.tsv)** file where the information of observed crossings is located
4. **Output**: file where the updated information of seed stock gene bank is saved after planting the seeds. An example of the report that could be helpful is contained.

You can run the analysis of the files above executing the following command:
```
ruby Proccessing.rb ./files/seed_stock_data.tsv ./files/gene_information.tsv ./files/cross_data.tsv ./files/output.tsv  
```
If output pathway specified already exists, the program will ask you if you want to overwrite it. Y/y (yes) or N/n (no) input is expected. The program will also ask you the desired amount of seeds to plant.

## Output
The output is verbose, it will be printed in the standar output channel.

If some of the seeds from seed bank get out of stock, a Warning message indicating the seed stock name. In addition, the current status of the seed bank will be both printed and saved into output file.

The genes that are genetically linked will be also printed. The stadistics parameters used in this program corresponds to three degrees of freedom [Concept of Chi-Square Test | Genetics](https://www.yourarticlelibrary.com/fish/genetics-fish/concept-of-chi-square-test-genetics/88686)

## References

1. https://parzibyte.me/blog/2019/02/09/leer-escribir-archivos-csv-ruby/ [30/10/2022]
2. https://stackoverflow.com/questions/28488422/how-to-check-the-number-of-arguments-passed-with-a-ruby-script [02/11/2022]
3. https://github.com/abscondment/statistics2/blob/master/test/sample_tbl.rb [02/11/2022]
4. https://www.toptal.com/ruby/ruby-metaprogramming-cooler-than-it-sounds [31/10/2022]
5. https://guides.rubygems.org/rubygems-basics/#installing-gems [02/11/2022]
6. https://www.honeybadger.io/blog/how-to-exit-a-ruby-program/ [28/10/2022]
7. https://code-maven.com/argv-the-command-line-arguments-in-ruby [01/11/2022]
8. https://www.yourarticlelibrary.com/fish/genetics-fish/concept-of-chi-square-test-genetics/88686 [04/11/2022]
9. https://learn.co/lessons/ruby-gets-input [05/11/2022]
