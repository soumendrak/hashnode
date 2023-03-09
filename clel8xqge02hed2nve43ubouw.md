---
title: "10 Python Libraries Every AI/ML Developer Should Know"
seoTitle: "Top 10 Python Libraries for AI/ML Developers"
seoDescription: "10 Python Libraries for AI/ML Devs: Requests, NumPy, Pandas, Matplotlib, Scikit-learn, Keras, TensorFlow, PyTorch, NLTK, and BeautifulSoup"
datePublished: Sun Feb 26 2023 10:26:39 GMT+0000 (Coordinated Universal Time)
cuid: clel8xqge02hed2nve43ubouw
slug: 10-python-libraries-every-aiml-developer-should-know
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1676651780964/3d80f53c-4980-47d9-aef3-06daad710f82.png
tags: ai, python, machine-learning, ml, python-beginner

---

1. Requests - Requests is a library used for making HTTP requests in Python. It provides support for handling HTTP methods like GET, POST, and DELETE, and includes features like request headers and authentication.
    

Example code snippet:

```python
# Handwritten
import requests

response = requests.get('https://jsonplaceholder.typicode.com/posts')
print(response.json())
```

1. BeautifulSoup – BeautifulSoup is a library used for web scraping in Python. It provides support for parsing HTML and XML documents and includes features like navigating the document tree and extracting data.
    
    ```python
    import requests
    from bs4 import BeautifulSoup
    
    url = 'https://en.wikipedia.org/wiki/Python_(programming_language)'
    
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    
    title = soup.title.string
    
    print(title)
    ```
    
2. NumPy – NumPy is a library used for scientific computing with Python. It provides support for large, multi-dimensional arrays and matrices, and includes a large collection of mathematical functions to operate on these arrays.
    
    Example code snippet:
    
    ```python
    import numpy as np
    
    a = np.array([1, 2, 3])
    b = np.array([4, 5, 6])
    
    c = a + b
    
    print(c)
    
    # Output
    [5 7 9]
    ```
    
3. Pandas – Pandas is a library used for data manipulation and analysis. It provides support for handling tabular data, including reading and writing various data formats, filtering, sorting, grouping data, and much more.
    
    Example code snippet:
    
    ```python
    import pandas as pd
    
    data = {'Name': ['Alice', 'Bob', 'Charlie', 'David'],
            'Age': [25, 32, 18, 47],
            'Gender': ['F', 'M', 'M', 'M']}
    
    df = pd.DataFrame(data)
    
    print(df)
    
    # Output
           Name  Age Gender
    0     Alice   25      F
    1       Bob   32      M
    2   Charlie   18      M
    3     David   47      M
    ```
    
4. Matplotlib – Matplotlib is a library used for creating data visualizations in Python. It provides support for creating various types of plots, including line, bar, scatter, and more.
    
    Example code snippet:
    
    ```python
    import matplotlib.pyplot as plt
    
    x = [1, 2, 3, 4, 5]
    y = [2, 4, 6, 8, 10]
    
    plt.plot(x, y)
    plt.xlabel('X-axis')
    plt.ylabel('Y-axis')
    plt.title('Line Plot')
    
    plt.show()
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1676629103108/38bd74a9-ea0b-4c77-a333-f5f85ab330af.png align="center")
    
5. Scikit-learn – Scikit-learn is a library used for machine learning in Python. It provides support for various machine learning algorithms, including classification, regression, and clustering.
    
    Example code snippet:
    
    ```python
    from sklearn.datasets import load_iris
    from sklearn.model_selection import train_test_split
    from sklearn.neighbors import KNeighborsClassifier
    
    iris = load_iris()
    
    X_train, X_test, y_train, y_test = train_test_split(iris.data, iris.target, test_size=0.2)
    
    knn = KNeighborsClassifier(n_neighbors=3)
    knn.fit(X_train, y_train)
    
    print(knn.score(X_test, y_test))
    0.9333333333333333
    ```
    
6. Keras – Keras is a high-level neural networks API written in Python. It provides support for building and training deep learning models, with a focus on enabling fast experimentation.
    
    Example code snippet:
    
    ```python
    import keras
    from keras.models import Sequential
    from keras.layers import Dense
    
    model = Sequential()
    model.add(Dense(10, input_dim=4, activation='relu'))
    model.add(Dense(3, activation='softmax'))
    
    model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
    
    print(model.summary())
    ```
    
    Output:
    
    ```plaintext
    Model: "sequential"
    ________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense (Dense)               (None, 10)                50        
                                                                     
     dense_1 (Dense)             (None, 3)                 33        
                                                                     
    =================================================================
    Total params: 83
    Trainable params: 83
    Non-trainable params: 0
    _________________________________________________________________
    None
    ```
    
7. TensorFlow – TensorFlow is a library used for machine learning and deep learning in Python. It provides support for building and training various types of neural networks, including convolutional neural networks and recurrent neural networks.
    
    Example code snippet:
    
    ```python
    import tensorflow as tf
    
    model = tf.keras.Sequential([
        tf.keras.layers.Dense(10, input_shape=(4,), activation='relu'),
        tf.keras.layers.Dense(3, activation='softmax')
    ])
    
    model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy'])
    
    print(model.summary())
    ```
    
    Output:
    
    ```plaintext
    Model: "sequential_1"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense_2 (Dense)             (None, 10)                50        
                                                                     
     dense_3 (Dense)             (None, 3)                 33        
                                                                     
    =================================================================
    Total params: 83
    Trainable params: 83
    Non-trainable params: 0
    _________________________________________________________________
    ```
    
8. PyTorch – PyTorch is a library used for machine learning and deep learning in Python. It provides support for building and training various types of neural networks, and includes features like automatic differentiation and GPU acceleration.
    

Example code snippet that demonstrates the use of PyTorch to create and train a simple neural network:

```python
import torch
import torch.nn as nn
import torch.nn.functional as F


class Net(nn.Module):

    def __init__(self):
        super(Net, self).__init__()
        # 1 input image channel, 6 output channels, 5x5 square convolution
        # kernel
        self.conv1 = nn.Conv2d(1, 6, 5)
        self.conv2 = nn.Conv2d(6, 16, 5)
        # an affine operation: y = Wx + b
        self.fc1 = nn.Linear(16 * 5 * 5, 120)  # 5*5 from image dimension
        self.fc2 = nn.Linear(120, 84)
        self.fc3 = nn.Linear(84, 10)

    def forward(self, x):
        # Max pooling over a (2, 2) window
        x = F.max_pool2d(F.relu(self.conv1(x)), (2, 2))
        # If the size is a square, you can specify with a single number
        x = F.max_pool2d(F.relu(self.conv2(x)), 2)
        x = torch.flatten(x, 1) # flatten all dimensions except the batch dimension
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x


net = Net()
print(net)
```

Output:

```plaintext
Net(
  (conv1): Conv2d(1, 6, kernel_size=(5, 5), stride=(1, 1))
  (conv2): Conv2d(6, 16, kernel_size=(5, 5), stride=(1, 1))
  (fc1): Linear(in_features=400, out_features=120, bias=True)
  (fc2): Linear(in_features=120, out_features=84, bias=True)
  (fc3): Linear(in_features=84, out_features=10, bias=True)
)
```

1. NLTK – NLTK is a library used for natural language processing in Python. It provides support for various tasks, including text classification, sentiment analysis, and part-of-speech tagging.
    

Example code snippet:

```python
import nltk

nltk.download('punkt')
text = "This is a sample sentence. It contains multiple sentences."
sentences = nltk.sent_tokenize(text)

print(sentences)
```

Output:

```plaintext
['This is a sample sentence.', 'It contains multiple sentences.']
```

### Conclusion

In conclusion, Python has a vast collection of libraries that make it an incredibly versatile language for a wide range of applications, from web development to machine learning. In this blog post, we've highlighted 10 Python libraries that every AI/ML developer should know, each with its unique features and use cases.

Of course, this list is by no means exhaustive, and there are many other libraries worth exploring. But with the knowledge gained from these libraries, developers can continue to expand their skills and build innovative solutions to real-world problems.