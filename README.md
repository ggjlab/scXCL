# scXCL
#### A tool defines cell types in Xenopus based on single-cell digital expression
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
# XCL_skin is an example expression matrix from XCL project.
> data(xcl_skin)
> dim(xcl_skin)
[1] 14809   200
# 14809 genes expression value of 200 cells

# scXCL has two parameters , single cell expression matrix(scdata) and 
# the number of most similar cell types
> XCL_result <- scXCL(scdata = xcl_skin, numbers_plot = 3)

# If the inpout gene is from Xenopus tropicalis, please set the parameter Tropicalis to TRUE (default is FALSE).
> XCL_result <- scXCL(scdata = xcl_skin, numbers_plot = 3, Tropicalis=TRUE)
```

The return of scXCL() is a list which contains 4 parts.
* cors_matrix: Pearson correlation coefficient matrix of each cell and cell type.
* top_cors: equals to numbers_plot
* scXCL: the most relevant cell type for each query cell
* scXCL_probility: the top n relevant cell types for each query cell

```R
# open shiny for visualize result for scXCL
scXCL_vis(xcl_result)
```

scXCL_vis() provides a bref function for visualizing and downloading of scXCL results

![scXCL.png](https://s2.loli.net/2022/02/11/UIYtGvnPpBHjuA1.png)
