# causalMGM
causalMGM is an R package that allow users to learn undirected and directed (causal) graphs over mixed data types (i.e., continuous and discrete variables). To learn a directed graph over mixed data, it first calculates the undirected graph (Sedgewick *et al*, 2016) and then it uses local search strategies to prune-and-orient this graph (Sedgewick *et al*, 2017).

## R Library Requirement
R >= 3.4.0,
Java >= 1.7.0,
[rJava](https://cran.r-project.org/web/packages/rJava/index.html)

## Installation for Mac OS X Users
Note: If legacy Java 1.6 version is installed in the computer alongside higher versions, RStudio call of rJava will default to Java 1.6. In this case causalMGM will fail to run. Please remove Java 1.6 (or place it in another directory) before installing causalMGM.

- Install JDK Tools
- Reconfigure R installation for Java in the terminal
```
$ sudo R CMD javareconf
```
- Manually load libjvm.dylib in R (e.g., in RStudio)
```R
> dyn.load('/path/to/libjvm.dylib')
e.g.:
> dyn.load('/Library/Java/JavaVirtualMachines/jdk1.8.0_65.jdk/Contents/Home/jre/lib/server/libjvm.dylib')
```
- Install the R library requirements:
```R
> install.packages("rJava")
```
- Install causalMGM from github:
```R
> library(devtools)
> install_github("benoslab/causalMGM")
> library(causalMGM)
```

## Installation for non-Mac OS Users
- Install the R library requirements:
```R
> install.packages("rJava")
```
- Install causalMGM from github:
```R
> library(devtools)
> install_github("nehaabraham/causalMGM")
> library(causalMGM)
```

## Example
```R
> mgm_init() # Initialize MGM
# FOR EXAMPLE DATASET 
> dataset <- loadSampleData() # loads sample dataset, use loadData() to load own dataset
> undgraph <- mgm(dataset) # learn the undirected graph over 'dataset'
Please enter the continuous-continuous lambda value: 0.16
Please enter the continuous-discrete lambda value: 0.2
Please enter the discrete-discrete lambda value: 0.3
> mgm.pc_stable(dataset, undgraph) # learn the directed graph using 'undgraph' as skeleton to guide local searches.
```

## Contact
The causalMGM R package is developed by Neha Abraham and the [Benos lab](http://www.csb.pitt.edu/Faculty/benos/). Please contact <mgmquery@pitt.edu> with any questions.
