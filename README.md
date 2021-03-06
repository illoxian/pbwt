# pbwt with missing data
This tool is the implementation of the positional Burrows Wheeler Transform with the handling capabilities of missing data (GAPs), with the final aim of finding Maximal Perfect Haplotype Blocks in a n-ary matrix of haplotypes.


The tool takes as input: 
* **n-ary matrix** (a binary matrix as stardard input) with the addition of the wildcard symbol (\*). Input must be given as a plain text file, any extension accepted. For clarity you may use `.bm` extension for binary matrices and `.bmw` for binary matrices with gaps; `.txt` is fine too.
* **query** parameter (-q=integer) for stopping the computation at a given column index, useful for outputting a (prefix) and d (divergence) arrays.
    (Defaults to last index)
* **minimum rows** parameter (-min_r=integer) used to specify the min row count of a single block
    (Defaults to 2)
* **minimum width** parameter (-min_w=integer) used to specify the min column count of a single block
    (Defaults to 1)
* **alphabet** parameter (-a=integer\[2-9\]) used to specify the alphabet cardinality. This tool implement the multi-allelic pbwt, hence here you need to specify the alphabet size (wildcard symbol excluded)
    (Defaults to 2 - sigma(0,1))
* **profiler** parameter (-p=bool) used to run the profiler during the execution, used in producton
    (Defaults to false)

## Download and Usage

In order to use this tool you have to install `go_lang` into your system, version 1.16 or above recommended. Check [golang official site](https://go.dev/dl/) or use a conda environment.

Then run 
```
git clone https://github.com/illoxian/pbwt.git
```

into your terminal or, alternatively, download the zip file from [github](https://github.com/illoxian/pbwt) and unpack it. 

Reach the pbwt folder and then build the project
```
cd pbwt
go build
```

You are almost done! Try an execution with 
```
./pbwt test_files/small.bmw
```

Stardard usage is  `./pbwt [parameters] "pathToInput"` (plese make sure to insert all the needed parameters before the file path)

```
./pbwt -q=4 -a=2 -min_w=2 -min_r=3 test_files/small.bmw
```

For more informations run ```./pbwt -?```


## Execution examples

Running examples can be found under the `test_files` folder.

An execution example has been saved [here](https://github.com/illoxian/pbwt/blob/main/docs/execution_examples/report_toy.txt) and shows the exection of the tool taking `./test_files/toy.bmw` as input.

## Adding wildcards to your input

If you are looking to add wildcards to your matrix, feel free to use the tool under the `./wildcadd` folder.

Basic usage of the tool

```
cd ./wildcadd
go build
./wildcadd -o="outputPath" -r="wildcardRate" "pathtofile"
```
* `-r` is mandatory
* `-o` defaults to `./` (same path as the input file) so can be avoided
