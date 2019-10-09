# PCA
Prinicipal Component Analysis

Principal component analysis (PCA) is one of a family of techniques for taking high-dimensional data and using the dependencies between the variables to represent it in a more tractable, lower-dimensional basis, without losing too much information.


PCA finds the principal components 
z1,z2....zp  such that each principal component is independent (i.e. perpendicular) to each other and captures as much variance as possible. The principal components are linear combinations of the original features.

The properties of PCA as mentioned in the video are as follows:

They're weighted linear combinations of the original variables.

They're perpendicular to each other.

They capture maximum variance of the data and are ordered.

brief overview of the steps you need to perform PCA while using any dataset :-
1. Import the PCA library:

from sklearn.decomposition import PCA
pca = PCA(svd_solver='randomized', random_state=42)
 

2. Apply PCA on the dataset:

pca.fit(dat)
 

In this step, you apply PCA on the data by passing the dataset as an argument to the pca.fit() function.

3. Check the components:

pca.components_
This will give the PCs of the original dataset. Note that the PCs are aligned along the rows. Thus the first PC is denoted by the first array of the matrix that you obtain by applying this function pca.components_. Take a look at the result that you obtained

 ![image](https://user-images.githubusercontent.com/16449922/66470307-f48f1800-eaa6-11e9-8f73-d1d8edde51d6.png)
 

Thus the first Principal Component or PC is represented by the vector 

[-4.46999485e-01, -8.93998971e-01, -3.09402653e-02]
 

Note that this value can be represented as a linear combination of the original variables. The original variables or the original axes are represented by X(1,0,0) , Y(0,1,0) and Z(0,0,1). Thus when you solve it using the np.linalg.solve function you get the values 

(-0.45, -0.89, -0.03)
Thus  the principal component mentioned above can be represented as follows(the values of the principal component have been rounded off:

[-0.45,-0.89,-0.03] = -0.045[1,0,0] + (-0.89)[0,1,0] + (-0.03)[0,0,1] = -0.45X + (-0.89)Y +(-0.03)Z,  which is a linear combination of the original variables

4. Check variance ratio:

Using the following code you can calculate the variances given by the three principal components:

pca.explained_variance_ratio_
 

which gives us the values as

array([0.85, 0.15, 0.  ])
5. Transform the dataset onto the PCs:

You use the pca.fit_transform() function to project the dataset onto the Principal Component Matrix that you obtained in Step 3. This would result in a new dataset with the Principal Components as the new basis vectors, and the variances along each basis given by the values in Step 4.

dat_new2 = pca.fit_transform(dat)
 
