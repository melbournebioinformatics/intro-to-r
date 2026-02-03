---
title: 'Wrapping Up'
teaching: 10
exercises: 10
---

:::::::::::::::::::::::::::::::::::::: questions 

- How can I save plots to a file?

::::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: objectives

- Save plots to a pdf file in R
- Explain why using the `sessionInfo()` function is good practice

::::::::::::::::::::::::::::::::::::::::::::::::

## Saving plots



We can save plots interactively by clicking Export in the Plots window and saving as e.g. "myplot.pdf". Or we can output plots to pdf using `pdf()` followed by `dev.off()`. We put our plot code after the call to `pdf()` and before closing the plot device with `dev.off()`.

Let's save our last plot.


``` r
pdf("myplot.pdf")
ggplot(data = mygenes_counts, 
       mapping = aes(x = Group_f, y = log2(Count + 1), colour = Group_f)) +
  geom_jitter() +
  facet_wrap(~ gene_symbol) +
  labs(x = "Cell type and stage", y = "Count", title = "Mammary gland RNA-seq data") +
  theme(axis.text.x = element_text(angle = 90)) +
  theme(panel.background = element_blank(),
        panel.grid.major = element_blank(),
        panel.grid.minor = element_blank())
dev.off()
```

-----

## Session Info

At the end of your report, we recommend you run the `sessionInfo()`
function which prints out details about your working environment such as
the version of R yo are running, loaded packages, and package versions.
Printing out `sessionInfo()` at the end of your analysis is good
practice as it helps with reproducibility in the future.


``` r
sessionInfo()
```

``` output
R version 4.5.2 (2025-10-31)
Platform: x86_64-pc-linux-gnu
Running under: Ubuntu 24.04.3 LTS

Matrix products: default
BLAS:   /usr/lib/x86_64-linux-gnu/openblas-pthread/libblas.so.3 
LAPACK: /usr/lib/x86_64-linux-gnu/openblas-pthread/libopenblasp-r0.3.26.so;  LAPACK version 3.12.0

locale:
 [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C              
 [3] LC_TIME=en_US.UTF-8        LC_COLLATE=en_US.UTF-8    
 [5] LC_MONETARY=en_US.UTF-8    LC_MESSAGES=en_US.UTF-8   
 [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                 
 [9] LC_ADDRESS=C               LC_TELEPHONE=C            
[11] LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       

time zone: Etc/UTC
tzcode source: system (glibc)

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

other attached packages:
 [1] lubridate_1.9.4 forcats_1.0.1   stringr_1.6.0   dplyr_1.1.4    
 [5] purrr_1.2.0     readr_2.1.6     tidyr_1.3.2     tibble_3.3.0   
 [9] ggplot2_4.0.1   tidyverse_2.0.0

loaded via a namespace (and not attached):
 [1] vctrs_0.6.5        cli_3.6.5          knitr_1.51         rlang_1.1.6       
 [5] xfun_0.55          stringi_1.8.7      otel_0.2.0         renv_1.1.7        
 [9] generics_0.1.4     S7_0.2.1           glue_1.8.0         hms_1.1.4         
[13] scales_1.4.0       grid_4.5.2         evaluate_1.0.5     tzdb_0.5.0        
[17] yaml_2.3.12        lifecycle_1.0.4    compiler_4.5.2     RColorBrewer_1.1-3
[21] timechange_0.3.0   pkgconfig_2.0.3    farver_2.1.2       R6_2.6.1          
[25] tidyselect_1.2.1   pillar_1.11.1      magrittr_2.0.4     tools_4.5.2       
[29] withr_3.0.2        gtable_0.3.6      
```

-----

## Exercises


::::::::::::::::::::::::::::::::::::: challenge

#### Exercise

1. Download the raw counts for this dataset from [GREIN](http://www.ilincs.org/apps/grein/).
    a. Make a boxplot. Do the samples look any different to the normalised counts?
    b. Make subplots for the same set of 8 genes. Do they look any different to the normalised counts?
2. Download the normalised counts for the GSE63310 dataset from GREIN. Make boxplots colouring the samples using different columns in the metadata file.

:::::::::::::::::::::::::::::::::::::



-----

## Further Reading

- [A short intro to R and tidyverse](https://pmacdasci.github.io/r-intro-tidyverse/)  
- [Top 50 Ggplot Visualisations]( https://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html)  
- [R for Data Science](https://r4ds.had.co.nz/)


::::::::::::::::::::::::::::::::::::: keypoints 

- You can use the `pdf()` function to save plots, and finalize the file by calling `dev.off()`
- The `sessionInfo()` function prints information about your R environment which is useful for reproducibility

::::::::::::::::::::::::::::::::::::::::::::::::

