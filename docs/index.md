## Auto-Harmonization of Symbolic Melodies using CNNs


Aldo Aguilar [Email](aldoaguilar2022@u.northwestern.edu)
Alex Reneau[Email](alexreneau2021@u.northwestern.edu)
Yijing Barry Zhang[Email](yijingzhang2021@u.northwestern.edu)
  
Northwestern University Comp_Sci 496, Deep Learning
Professor Bryan Pardo


Check out some of the harmonization produced by our model:  
[song 1]()  
[song 2]()  
 
 
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
* **Loss Function**
* **Sliding Window Method**

### Results

![dataset example](https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize1Accuracy.png?raw=true)  
![dataset example](https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize2Accuracy.png?raw=true)  
![dataset example](https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize4Accuracy.png?raw=true)  
![dataset example](https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize8Accuracy.png?raw=true)  
![dataset example](https://github.com/nub3Ar/AutoHarmonizer/blob/main/docs/WindowSize12Accuracy.png?raw=true)  


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
