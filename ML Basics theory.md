## Scaling Data
### Standardization
**Standardization** rescales data so that it has a *mean* of 0 and a *standard deviation* of 1. <br>
**(𝑥 − 𝜇)/𝜎**

### Normalization
**Normalization** rescales the data into the range [0, 1]. <br>
**(𝑥 −𝑥𝑚𝑖𝑛)/(𝑥𝑚𝑎𝑥 −𝑥𝑚𝑖𝑛)**

## Encoding Categorical Data
There are two common approaches for encoding categorical data: **ordinal encoding** and **one hot encoding**.

### Ordinal Encoding
In ordinal encoding, we simply convert the categorical data into integer codes ranging from `0` to `(number of categories – 1)`. Let's look again at our example table of clothing products:
|SKU|Make	|Color|	Quantity|	Price|
|----|----|------|------|------|
|908721	|Guess	|Blue	|789	|45.33|
|456552	|Tillys	|Red	|244	|22.91|
|789921	|A&F	|Green|	387	|25.92|
|872266|	Guess|	Blue|	154	|17.56|

If we apply ordinal encoding to the `Make` property, we get the following:


|Make	|Encoding|Color|Encoding|
|---|---|---|---|
|A&F	|0|Red |0
|Guess	|1| Green|1|
|Tillys	|2| Blue|2|

Using the above encoding, the transformed table is shown below:

| SKU|Make|Color|Quantity|Price|
|----|----|-----|-------|----|
|908721|1|2|789|45.33|
|456552|2|0|244|22.91|
|789921|0|1|387|25.92|
|872266|1|2|154|17.56|

One of the potential drawbacks to this approach is that it implicitly assumes an order across the categories.

### One-Hot Encoding
**One-hot encoding** is a very different approach. In one-hot encoding, we transform each categorical value into a column. If there are n categorical values, n new columns are added. For example, the Color property has three categorical values: Red, Green, and Blue, so three new columns Red, Green, and Blue are added.

If an item belongs to a category, the column representing that category gets the value 1, and all other columns get the value 0. For example, item 908721 (first row in the table) has the color blue, so we put 1 into that Blue column for 908721 and 0 into the Red and Green columns. Item 456552 (second row in the table) has color red, so we put 1 into that Red column for 456552 and 0 into the Green and Blue columns.

If we do the same thing for the Make property, our table can be transformed as follows:
![image](https://user-images.githubusercontent.com/92245436/148727251-199b1faf-999b-411a-840f-787d69985e01.png)

## Image Data
Let's look a little closer at how an image can be encoded numerically. If you zoom in on an image far enough, you can see that it consists of small tiles, called pixels:

![image](https://user-images.githubusercontent.com/92245436/148728538-1b5765f7-cb87-4b62-836c-a93e2db3d4c5.png)

The color of each pixel is represented with a set of values:

- In **grayscale images** , each pixel can be represented by a **single** number, which typically ranges from 0 to 255. This value determines how dark the pixel appears (e.g., `0`  is black, while `255`  is bright white).
- In **colored images** , each pixel can be represented by a vector of **three** numbers (each ranging from 0 to 255) for the three primary color channels: red, green, and blue. These three red, green, and blue (RGB) values are used together to decide the color of that pixel. For example, purple might be represented as `128, 0, 128` (a mix of moderately intense red and blue, with no green).

The number of channels required to represent the color is known as the **color depth**  or simply **depth**.With an RGB image, `depth = 3` , because there are three channels (Red, Green, and Blue). In contrast, a grayscale image has `depth = 1`, because there is only one channel.

### Encoding an Image
Let's now talk about how we can use this data to encode an image. We need to know the following three things about an image to reproduce it:
- Horizontal position of each pixel
- Vertical position of each pixel
- Color of each pixel

## Text Data
### Normalization
**Lemmatization**  is an example of normalization. A **lemma** is the dictionary form of a word and **lemmatization** is the process of reducing multiple inflections to that single dictionary form. For example, we can apply this to the `is, am, are` example we mentioned above:
| Original text	 | Normalized text |
|-----|---|
|is|be|
|are|be|
|am|be|

### Vectorization 
The goal here is to identify the particular features of the text that will be relevant to us for the particular task we want to perform—and then get those features extracted in a numerical form that is accessible to the machine learning algorithm. Typically this is done by text **vectorization**.

Common approaches include:
- [Term Frequency-Inverse Document Frequency (TF-IDF) vectorization](https://en.wikipedia.org/wiki/Tf%E2%80%93idf)
- [Word embedding, as done with Word2vec or Global Vectors (GloVe)](https://nlp.stanford.edu/pubs/glove.pdf)

Here's what the word importance might look like if we apply it to our example

![image](https://user-images.githubusercontent.com/92245436/148731956-7085782c-5ad7-4a65-8e66-38fc20c99768.png)

Here's what that might look like if we apply it to the normalized text:

![image](https://user-images.githubusercontent.com/92245436/148731764-e60f6e9a-99e6-4c41-993d-656723443411.png)
