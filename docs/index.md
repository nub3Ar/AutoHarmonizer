# Auto-Harmonization of Symbolic Melodies using CNNs

**Members**  
Aldo Aguilar ([Email](aldoaguilar2022@u.northwestern.edu))  
Alex Reneau （[Email](alexreneau2021@u.northwestern.edu))  
Yijing Barry Zhang ([Email](yijingzhang2021@u.northwestern.edu))  

**Advisor**  
Northwestern University Comp_Sci 496, Deep Learning
Professor [Bryan Pardo](https://users.cs.northwestern.edu/~pardo/)
 
 
### Music harmonization and Deep Learning
Harmonization is a crucial part of what makes music enjoyable. ([What is harmony?](https://www.youtube.com/watch?v=eRkgK4jfi6M&ab_channel=WIRED)) The ability to generate harmonies requires a very deep understanding of the underlying structures of music pieces. A deep learning model able to learn to harmonize melodies would then give us great insights into how these models learn the structures of music, which can be instrumental to other musical-audio settings.

We would like to build an automatic melody harmonizer from lead sheet music that produces simple chordal accompaniment (in the forms of first inversion triads) for a symbolic melody. We would like to assess this both quantitatively, by checking against the original chord progression, and qualitatively, by assessing whether the chord progression is enjoyable or appropriate for the given melody.


### Experiment Setup
#### Dataset  
![dataset example](https://github.com/nub3Ar/AutoHarmonizer/blob/main/dataformat.png?raw=true)  
The dataset we are using is from a [[paper](https://arxiv.org/ftp/arxiv/papers/1712/1712.01011.pdf)] by the Music & Audio Research Group. The dataset consists of 2252 Western songs from many different genres. They are stored in lead sheet formats like shown in the image above. For our purposes, the only features we are considering are the key_mode and the note_root. We are encoding both the nodes and the chords using a simple dictionary such that we have 27 unique integers for both notes and chords: 2 keys (major/minor) * 13 semintones (12 semitones + rest) + 1 padding token. We decided to include the major/minor information in our notes as well for more information about the tone of the piece.  

 The original dataset used in the paper can be found [[here](http://marg.snu.ac.kr/chord_generation/#)]
* **Model/Loss Function**  
#### Fill in content here 
Model diagram:  
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/diagram%20(2).png?raw=true" align="center" width="450">
<br/>
**Fill in content here**  

#### Sliding Window Method
Our task works under the assumption that there are temporal dependencies for each song. Instead of using a recurrent neural network (like the BLSTM that the original paper used), we implemented a sliding window method to capture temporal dependencies within songs. It enforces that each time step includes a specified number of previous time steps in the current decision.  

Our implementation of the sliding window method is unique in the sense that it does not flatten the current and specified previous feature vectors into one feature vector. Instead, we package the current feature vector and the specified number of previous feature vectors into a matrix by padding all measures to the same length. This is mainly designed such that it's more efficiently fed into a convolutional neural network

Below is an example of this approach:  
original data: [[2, 4, 5], [1, 3, 11, 16], [8, 3, 2], [8, 2, 9], [1], [6]] where each sublist is a measure and each element in those sublists are an encoded semitone (see dataset)  
if we have a window size of 2, then we will be feeding the following to our model:
[[2, 4, 5, 0], [1, 3, 11, 16]], [[1, 3, 11, 16], [8, 3, 2, 0]], [[8, 3, 2, 0], [8, 2, 9, 0]], [[8, 2, 9, 0], [1, 0, 0, 0]], [[1, 0, 0, 0], [6, 0, 0, 0]]  




### Results  
* Quantitative Results  

Below we show the training and testing accuracy history using a window size of 1, 2, 4, and 8 measures.  
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize1Accuracy.png?raw=true" align="center" height="300" width="455">
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize2Accuracy.png?raw=true" align="center" height="300" width="455">
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize4Accuracy.png?raw=true" align="center" height="300" width="455">
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize8Accuracy.png?raw=true" align="center" height="300" width="455">
<br/>

**Fill in content here**  
  
* Qualitative Results  

Check out some of the harmonization produced by our model:  
**Fill in content here**  
[song 1]()  
[song 2]()  

[paper](www.google.com)
