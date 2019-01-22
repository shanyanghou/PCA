# PCA
# ST5210 Multivariate variable analysis tutorial 5
# R 
X = read.table("data.txt")
pca1 = princomp(X, cor=FALSE)
summary(pca1)
pca1$loadings

pca2 = princomp(X, cor=TRUE)
summary(pca2)
pca2$loadings

## eigenvalue and eigenvector

X = read.table("dataA.txt", header=F)
rownames(X) = X[,1]
X = X[,2:8]
cor(X)   ## correlation

eigen(cor(X))$values   ## eigenvalues
eigen(cor(X))$vector   ## eigenvectors


## PCA after standardized
Y = scale(X)
pc12 = Y %*% eigen(cor(X))$vector[,1:2]
cor(pc12, Y)

var(pc12)

plot(pc12)
text(pc12, label = rownames(X), cex=0.7)
