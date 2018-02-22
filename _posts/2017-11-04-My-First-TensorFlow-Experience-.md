---
title: "My First TensorFlow Experience"
date: 2017-11-04
categories: 
  - Jekyll
---
---

I am planning to make a PhD in Machine Learning if I will get accepted of course :) Therefore, these days I am planning to be attached to
TensorFlow. Firstly, I need to install it and I will follow the official documentation for this, which is 'https://www.tensorflow.org/get_started/get_started'. Firstly, I need to install Python 3.5.2 and add it to path. By the way, I am using
Windows 8.1. 

```
C:\Users\oguz>python --version
Python 3.5.2
```

I learned that there are two versions of TensorFlow, from now on I will refer TensorFlow as TF since it is long to write everytime :). 
First one is using GPU and second one is with CPU. For the beginning CPU version is preferred, therefore I will install this version with
the following command ```pip3 install --upgrade tensorflow```. Actually, at the beginning I was planning to use my company computer but, 
there occured so many proxy issues and I moved back to my PC. 

I successfully installed it, at the end it gave me a warning that ```You are using pip version 8.1.1, however version 9.0.1 is available.
You should consider upgrading via the 'python -m pip install --upgrade pip' command.``` This is a small warning and I updated my pip to 
9.0.1 version. 

```C:\Python\Python35>pip --version
pip 9.0.1 from c:\python\python35\lib\site-packages (python 3.5)
```

After that, I've written the very basic tf code. 

```
>>> import tensorflow as tf
>>> hello = tf.constant('Hello,TF!')
>>> sess = tf.Session()
2017-11-05 18:02:44.670825: I C:\tf_jenkins\home\workspace\rel-win\M\windows\PY\35\tensorflow\core\platform\cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2
>>> print(sess.run(hello))
b'Hello,TF!'
```

Now, we are ready to dig deeper. I will follow the https://www.tensorflow.org/get_started/get_started link. 
