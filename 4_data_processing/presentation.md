# Module 4: Herbarium Image Processing for Deep Learning

---


## Computer vision models are great at learning attributes of our data that we can see, so visually inspecting our data to think about potential biases is crucial.

---

### Important Considerations

* Are you building a model with data from multiple institutions?

* If not, were all the sheets imaged with the same camera and lighting setup?
 
* (A cautionary tale about this.)

---

### Mercury staining project

![](https://i.imgur.com/mRg9nGT.jpg)


---

### Mercury staining project

![](https://i.imgur.com/PqcVlob.jpg)

* Schuettpelz et al., 2017, *Biodiversity Data Journal*:  https://doi.org/10.3897/BDJ.5.e21139

---

### Important Considerations

* Are you building a model with data from multiple institutions?

* If so, there are invaribaly institution-specific, but NOT plant-specific attributes that a computer vision model can mistakenly use to classify images.

---

### Important Considerations

* Color bars, lighting, labels, barcodes, handwriting/typed text, stamps, etc. have the potential to produce a misleading model.

* Image segmentation is one way to minimize these potential issues.

---

### Image Segmentation

---

* Image segmentation means classifying the pixels in an image into different categories.

* You might want to segment "plant" from "not plant," or be even more specific and segment "labels," "fruits," etc.

* Breakthroughs in this area come from the medical field.

---

### A segmented femur

![](https://i.imgur.com/IkdrZuZ.png)

---

* The SI Data Science Lab (datascience.si.edu) built a segmentation model for ferns that segments plant material from the background of herbarium sheets.
 
* Paper in *APPS* (White et al., 2020): http://dx.doi.org/10.1002/aps3.11352

* Code on GitHub: https://github.com/sidatasciencelab/fern_segmentation

---

### How we built a segmentation model

* Used OpenCV, PlantCV, and some manual work in Photoshop to develop a ground-truth dataset of 400 "masks."

* Masks = images of identical resolution that define the identity of each pixel in the original image.

---

### An original herbarium sheet

![](https://i.imgur.com/FXH5r94.jpg)

---

### An original herbarium sheet


![](https://i.imgur.com/uvVqVrq.jpg)


---

### A ground-truth mask


![](https://i.imgur.com/QyEU3La.jpg)


---

### How we built a segmentation model

* We then trained a U-Net with these 400 ground-truth masks.

* The U-Net learned what the boundaries of fern shapes generally look like.

* Then we could segment all 800,000 ferns from GBIF very rapidly, which could then be used as training data for a species classification model.

---

### Data Augmentation and Transformation

* Data augmentation and transformation can help prevent over-fitting.

* Ideally, a species classification model can identify species no matter which way they are mounted, and whether or not the whole plant is included on the sheet.

* Methods include random cropping, lighting contrast changes, flipping, zooming, and warping.



