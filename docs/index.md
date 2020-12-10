## Auto-Harmonization of Symbolic Melodies using CNNs

**Members**  
Aldo Aguilar ([Email](aldoaguilar2022@u.northwestern.edu))  
Alex Reneau （[Email](alexreneau2021@u.northwestern.edu))  
Yijing Barry Zhang ([Email](yijingzhang2021@u.northwestern.edu))  

**Advisor**  
Northwestern University Comp_Sci 496, Deep Learning
Professor [Bryan Pardo](https://users.cs.northwestern.edu/~pardo/)


 
 
### Music harmonization and Deep Learning
Harmonization is a crucial part of what makes music enjoyable. [What is harmony?](https://www.youtube.com/watch?v=eRkgK4jfi6M&ab_channel=WIRED) The ability to generate harmonies requires a very deep understanding of the underlying structures of music pieces. A deep learning model able to learn to harmonize melodies would then give us great insights into how these models learn the structures of music, which can be instrumental to other musical-audio settings.

We would like to build an automatic melody harmonizer from lead sheet music that produces simple chordal accompaniment (in the forms of first inversion triads) for a symbolic melody. We would like to assess this both quantitatively, by checking against the original chord progression, and qualitatively, by assessing whether the chord progression is enjoyable or appropriate for the given melody.

### Our Project

### Experiment Setup
* **Dataset**  
![dataset example](https://github.com/nub3Ar/AutoHarmonizer/blob/main/dataformat.png?raw=true)  
The dataset we are using is from a [paper](https://arxiv.org/ftp/arxiv/papers/1712/1712.01011.pdf) by the Music & Audio Research Group. The dataset consists of 2252 Western songs from many different genres. They are stored in lead sheet formats like shown in the image above. For our purposes, the only features we are considering are the key_mode and the note_root.
 The original dataset used in the paper can be found [here](http://marg.snu.ac.kr/chord_generation/#)
* **Model**  
Model diagram:  
![model diagram]()

* **Loss Function**
* **Sliding Window Method**  
Our task works under the assumption that there are temporal dependencies for each song. Instead of using a recurrent neural network (like the BLSTM that the original paper used), we implemented a sliding window method to capture temporal dependencies within songs. It enforces that each time step includes a specified number of previous time steps in the current decision.  
Our implementation of the sliding window method is unique in the sense that it does not flatten the current and specified previous feature vectors into one feature vector. Instead, we package the current feature vector and the specified number of previous feature vectors into a matrix. The motivation for building this input representation for each time step was that it would provide a data representation that was optimal to feed into a convolutional neural network.  
Below is an example of this approach:  
original data: [[2, 4, 5], [1, 3, 11, 16], [8, 3, 2], [8, 2, 9], [1], [6]] where each sublist is a measure and each element in those sublists are an encoded semitone (see dataset)  
if we have a window size of 2, then we will be feeding the following to our model:
[[2, 4, 5, 0], [1, 3, 11, 16]], [[1, 3, 11, 16], [8, 3, 2, 0]], [[8, 3, 2, 0], [8, 2, 9, 0]], [[8, 2, 9, 0], [1, 0, 0, 0]], [[1, 0, 0, 0], [6, 0, 0, 0]]




### Results  
* Quantitative Results  

Below we show the training and testing accuracy history using a window size of 1, 2, 4, and 8 measures. 
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize1Accuracy.png?raw=true" align="left" height="300" width="450">
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize2Accuracy.png?raw=true" align="left" height="300" width="450">
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize4Accuracy.png?raw=true" align="left" height="300" width="450">
<img src="https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize8Accuracy.png?raw=true" align="left" height="300" width="450">



* Qualitative Results  

Check out some of the harmonization produced by our model:  
[song 1]()  
[song 2]()  

[paper](www.google.com)



### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
