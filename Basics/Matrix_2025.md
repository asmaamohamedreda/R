
# Data Structure ----------------------------------------------------------

## [Variable, Vectors, List, Matrix, Data Frames]

### Matrix
A Matrix is a container that holds multiple values of the same data type in a table format.

- Matrix is a 2D extension of a vector (1D)
- A matrix has **m** rows and **n** columns

> 🔺 RULE: Any data structure created should be explicitly called or printed to be executed or viewed

### Matrix Examples

```r
mat = matrix(c(1, 2, 3, 4, 5, 6), nrow = 2, ncol = 3)
mat

mat = matrix(seq(1, 20), nrow = 4, ncol = 5)
mat

mat = matrix(seq(1, 20), nrow = 4, ncol = 5, byrow = TRUE)
mat

mat = matrix(data = 1:20, nrow = 5, ncol = 4)
mat

mat = matrix(1:20, nrow = 5, ncol = 4)
mat

mat = matrix(LETTERS[1:24], nrow = 4, ncol = 6)
mat

mat = matrix(letters[1:24], nrow = 4, ncol = 6)
mat
```

# Built-in Functions for Matrix -------------------------------------------

```r
mat = matrix(1:50, nrow = 5, ncol = 10)
mat

rownames(mat) = c("Gene1","Gene2","Gene3","Gene4","Gene5")
mat

colnames(mat) = c("Sample1", "Sample2", ..., "Sample10")
mat

rownames(mat) = paste("Gene", 1:5, sep = "_")
mat

rownames(mat) = paste0("Gene", 1:5)
mat

colnames(mat) = paste0("Sample", 1:10)
mat

colnames(mat) = paste("Sample", 1:10, sep = ".")
mat

colnames(mat) = c(paste0("Normal.", 1:5), paste0("Tumor.", 6:10))
mat

colnames(mat) = c(paste("Normal", 1:5, sep = "_"), paste("Cancer", 6:10, sep = "_"))
mat

colnames(mat) = paste0(c("Normal.", "Tumor."), c(1:10))
mat

colnames(mat) = paste("Sample", letters[1:10], sep = "_")

colnames(mat) = paste0("Col", 1:10)
mat

dim(mat)
View(mat)
dimnames(mat)
range(mat)
t(mat)

summary(mat)

colnames(mat)
ncol(mat)
colSums(mat)
colMeans(mat)

rownames(mat)
nrow(mat)
rowSums(mat)
rowMeans(mat)

# If needed: install.packages("matrixStats")
library(matrixStats)

rowMaxs(mat)
rowMins(mat)
rowMedians(mat)

mat
rowMeans(mat)["Gene_5"]
```

# Matrix Indexing ---------------------------------------------------------

```r
mat = matrix(1:50, nrow = 5, ncol = 10)
mat

mat[2, 4]
mat[3, 2]
mat[4, 6]
mat[2, 9]

mat[4, ]
mat[, 8]
mat[2, ]
mat[, 10]

mat[1:3, 1:3]
mat[1:2, 2:3]
mat[c(2, 4, 5), c(1, 3)]
mat[2, c(1, 6)]

mat[-1, ]
mat[-c(1, 5), ]
mat[, -c(1, 2, 3)]

mat[c(1, 13, 18, 23, 50)]

values <- c(mat[1, 1], mat[3, c(4, 5, 6)], mat[5, 10])
val
val <- c(mat[1, 1], mat[3, 4:6], mat[5, 10])
mat

values = c(mat[1, 1], mat[4, 10])
values
```

# Real Example from Real Data ---------------------------------------------

```r
# exp <- read.delim("expData.txt", row.names = 1)
# exp1 <- read.table("expData.txt", row.names = 1)
# View(exp1)
# df <- read_delim("expData.txt", delim = "	", escape_double = FALSE, trim_ws = TRUE)

# genes = df$...1
# rownames(df) = df$...1
# df = df[-1]
# rownames(df) = genes

dim(exp)
summary(exp)
head(exp)
tail(exp, n = 2)
expMatrix = exp
colnames(exp)  
rownames(exp)
rownames(exp)[1:10]
rowSums(exp)[1:10]

sum(is.na(exp))

Avg.exp = rowMeans(exp)
exp = cbind(exp, Avg.exp)

geneSum = rowSums(exp)
exp = cbind(exp, geneSum)

exp.downregulated = exp[order(exp$Avg.exp), ]
exp.upregulated = exp[order(exp$Avg.exp, decreasing = TRUE), ]

Top_100DownReg = exp.downregulated[1:100, ]
rownames(Top_100DownReg)[1:10]
```
