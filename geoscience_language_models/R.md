# Load libraries

```         
#load libraries

library(tidyverse)


```

# Load word vectors in Word2Vec format

```         
#load data using tidyverse functions
myvecs      <- read_table("C:/Uni_Work_DLC/Research/Finished_model/dataset_A_full_11-07-2023-18-35-42/vectors.txt", skip = 1, col_names = TRUE)
mydf        <- as.data.frame(myvecs)
```

# Create a list of vocabularies to filter

```         
myvocab <- c("claystone", "clay", "sandstone")
#, "sand", "silt", "siltstone", "gravel", "conglomerate"
```

# Filter preferred vocabularies

```         
mydf_filter <-  filter(mydf, mydf[,1] %in% myvocab)
```



# Prepare data for pca

```         
forpca <-   mydf_filter %>%
        dplyr::select(-X1) %>%
        as.data.frame()
```

# Calculate PCA

```         
mypca <-    prcomp(forpca) 
plot(mypca)
biplot(mypca)
summary(mypca)
```



