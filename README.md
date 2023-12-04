# Classiﬁcation of eye Fundus images based on dictionary learning method

Diabetic retinopathy (DR) is a chronic eye disease characterized by degenerative changes to the retina blood vessels. In this project, we presented a dictionary learning (DL)-based method for automatic detection of DR in digital fundus images. The detection method was based on K-SVD algorithm. In eye fundus classification, the suitable dictionary must have high power for discrimination of the normal and diabetic classes. In each class, we created discriminative bases. For this purpose, dictionary bases with maximum effect for representation of images were considered. The presented approach does not require feature selection.

### The proposed method
We used dictionary learning (DL) based method for classification of eye fundus images. One useful representative DL method for image processing tasks is the K-SVD algorithm. We used this algorithm for designing a dictionary that leads to the best representation for a set of given images. The K-SVD algorithm designs a dictionary using singular value decomposition (SVD) under strict sparsity constraints and it is a generalization of K-means clustering approach. K-SVD algorithm has good representational power but it does not focus on discrimination capability. In our approach, dictionaries had been discriminated. The procedure of our method is shown in Fig.1.

![image](https://github.com/NarjesKarami/Classification-of-eye-Fundus-images-based-on-dictionary-learning-method/assets/78353927/af38e50a-ec2f-4a4c-970d-90ba1c120d73)\ 
Fig.1. The proposed algorithm for classification of color fundus images

### Learning of dictionaries
First the training images were partitioned into block patches. Due to data information protection at the edges of the patches, the patches were considered with overlapping. Patch size should be selected such that each patches containing useful information. Indeed each patch represents a meaningful pattern. If the patch size is set to large, computational complexity is increased and if the small patch size is selected will not be a suitable pattern for each patch.
Then, we applied the K-SVD algorithm for dictionary learning and trained a dictionary for each class. We considered the number of dictionary atoms enough larger than the size of blocks. The dictionary was initialized with the training patches randomly. The algorithm found sparse coefficient for approximations of the training images whilst it preserved the dictionary fixed. Then vice versa, i.e. the dictionary was optimized during the sparse coefficients were kept fixed. This process was repeated until sparsity or representation error reach to a specific value.
### Classification phase
Our classification method had a two-phase process comprising:
- #### Finding the best atoms:
Due to discrimination of dictionaries, best dictionary atoms were selected. In contrast to the other methods, we used the resulting coefficient matrix in the training phase for classification phase. Best atoms have largest elements in sparse coefficient matrix. In this phase, effect of each dictionary atom for representation of images was considered. Atoms with maximum coefficients have more effect for approximating signals. Elements of i-th atom multiply by elements of i-th row of sparse coefficient matrix. So for performance of i-th atom we were considered these elements. Maximum coefficients in each row of sparse coefficient matrix were computed. Then atoms with maximum coefficients remained. ‎0shows sparse coding coefficients energy diagram for normal class. As is clear from one point to the next atom weights change too much, so we consider atoms in this range as the best atoms.

![image](https://github.com/NarjesKarami/Classification-of-eye-Fundus-images-based-on-dictionary-learning-method/assets/78353927/871b03af-e611-4680-b3c6-25227d4052ad)\
Fig2. Coefficients energy diagram

For discriminating of the dictionaries, in each class, we removed atoms with high correlation between atoms of other classes. Fig.3 shows the discrimination best dictionaries of normal and diabetic classes. As it can be seen in Fig.3 (b), atoms like vessels are removed from the dictionaries of diabetic class to have best discriminating atoms of this class.\
<img width="450" alt="image" src="https://github.com/NarjesKarami/Classification-of-eye-Fundus-images-based-on-dictionary-learning-method/assets/78353927/788e8a35-3e6c-4089-a14f-ca86602510f9">\

- #### Classification of test images 
Each test image was divided into overlapping patches. Test images were classified based on using obtained dictionaries of each class. We used the sparse coding coefficients of each class for image classification, instead of reconstruction error. For a test image, we first computed its sparse representation coefficient and then according to L0-norm of coding coefficient we classified a testing image.
### Results and validation
We evaluated the proposed method on 60 right and left fundus images from a public dataset available at (http://misp.mui.ac.ir/). Each image was in JPG format with size 576×720 pixels. For training phase, 20 fundus images for each class were selected, randomly. 40 images and 15 images were used for normal and diabetic test images, respectively. In this work green cannel of fundus RGB image was used. In our experiments, the size of block patches was 20×20 pixels. The blocks had 50% overlapping. The number of dictionary atoms was considered 1600. Correlation coefficient was set to 0.72. The sensitivity and specificity of our method were 88% and 93% respectively. The DSC of the model was 92%.





