# scXCL
#### A tool defines cell types in zebrafish based on single-cell digital expression
At first scXCL is a breif R package for large scale data(large DGE) from scXCL online function [Xenopus Cell Landscape](http://bis.zju.edu.cn/XCL/index.html) ,to alleviate burdens of our main Server.

Now we add a UI for visulizing the scXCL reuslt.

Installation
-----
```R
#This require devtools  
install.packages('devtools')
library(devtools)
# scXCL requires ggplot2/reshape2/plotly/shiny/shinythemes/shiny
install_github("ggjlab/scXCL")
```

Quick Start
----
```R
library(scXCL)
# XCL_caudalfin is an example expression matrix from XCL project.
> data(XCL_caudalfin)
> dim(XCL_caudalfin)
[1] 2000   380
# 2000 genes expression value of 380 cells

# scXCL has two parameters , single cell expression matrix(scdata) and 
# the number of most similar cell types
> XCL_result <- scXCL(scdata = XCL_caudalfin, numbers_plot = 3)
```

The return of scXCL() is a list which contains 4 parts.
* cors_matrix: Pearson correlation coefficient matrix of each cell and cell type.
* top_cors: equals to numbers_plot
* scHCL: the most relevant cell type for each query cell
* scHCL_probility: the top n relevant cell types for each query cell

```R
# open shiny for visualize result for scHCL
scHCL_vis(hcl_result)
```

scXCL_vis() provides a bref function for visualizing and downloading of scXCL results

![scXCL.png](https://i.loli.net/2020/07/05/8PQ3seyUIaEHZXf.png)
