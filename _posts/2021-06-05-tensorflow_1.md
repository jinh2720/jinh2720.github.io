---
layout: single
title: "텐서와 넘파이의 차이"
author_profile: true
excerpt: "tensorflow, numpy"
categories:
    - Tensorflow
---

tfrecord로 데이터를 변환하고 tfrecord 파일을 출력하는 과정에서 궁금증이 생겼다. 

tfrecord에 저장되어 있는 이미지의 height 정보를 다음 2가지로 형태로 출력해보았다.

```python
height = image_features['height'] 
height_to_numpy = image_features['height'].numpy()
```

height 와 hegith_to_numpy 를 출력해보면

```python
height:  tf.Tensor(777, shape=(), dtype=int64) # <class 'tensorflow.python.framework.ops.EagerTensor'>
height_to_numpy:  777 # <class 'numpy.int64'>
```

형태로 출력이 된다.  tfrecord에 저장될 때는 자료형이 텐서로 저장이 되는 것이고 이것을 편하게 사용해하던 넘파이로 변환할 수도 있다.  그러면 텐서와 넘파이의 차이는 무엇일까?

- 텐서는 가속기 메모리(GPU, TPU)에서 사용할 수 있다.
- 텐서는 불변성을 가진다. (shape에 대한 불변성)

많은 경우 딥러닝 프로젝트를 진행하면, 모델 패키지를 사용하는 경우가 많을텐데, 텐서플로로 작성되어 있기 때문에 GPU의 활용이 효율적인 것이다. 아마 'pycuda' 라는 라이브러리가 python 연산을 gpu를 이용하여 연산 할 수 있게 해주는 걸로 알고 있는데 다음에 한 번 공부해봐야겠다.



## 텐서와 넘파이 호환성 

- 텐서플로 연산은 자동으로 넘파이 배열을 텐서로 변환한다.
- 넘파이 연산은 자동으로 텐서를 넘파이 배열로 변환한다.

```python
import numpy as np

ndarray = np.ones([3, 3])

""" tensor to numpy """
tensor = tf.multiply(ndarray, 42)
print(tensor) # tensor object

""" numpy to tensor """
print(np.add(tensor, 1)) # numpy object
```



tf.Tensoor와 배열은 메모리 표현을 공유하기 때문에 이러한 변환에 있어서 비용은 저렴하다. 그러나 **tf.Tensor는 GPU 메모리**에 저장될 수 있고, **넘파이 배열은 항상 호스트 메모리**에 저장되므로, 이러한 변환이 **항상 가능한 것은 아니다**. 따라서 GPU에서 호스트 메모리로 복사가 필요하다.



### GPU 가속

대부분의 텐서플로 연산은 GPU를 사용하여 가속화된다. 어떠한 코드를 명시하지 않아도, 텐서플로는 연산을 위해 **CPU 또는 GPU를 사용할 것인지를 자동으로 결정**한다. 필요시 텐서를 CPU와 GPU 메모리 사이에서 복사를 한다. 연산의 의해 **생성된 텐서는 전형적으로 연산이 실행된 장치의 메모리에 의해 실행**된다.

```python
import tensorflow as tf

x = tf.random.uniform([3, 3])

"""GPU의 사용가능 여부"""
print(tf.test.is_gpu_available()) # True

"""X의 텐서가 GPU #0 에 있는지 여부 """
print(x.device.endswith('GPU:0')) # True
```



```python
os.environ['CUDA_VISIBLE_DEVICES']='0' # gpu index
```

위와 같이 GPU 사용을 명시하지 않더라도 GPU로 연산되는 것을 알 수 있다.



그리고 하고자 하는 연산에 대해서 CPU 또는 GPU로 강제할 수도 있다. 

```python
import tensorflow as tf
import time

def time_matmul(x):
  start = time.time()
  for loop in range(10):
    tf.matmul(x, x)

  result = time.time()-start

  print("10 loops: {:0.2f}ms".format(1000*result))

"""CPU에서 강제 실행"""
print("On CPU:")
with tf.device("CPU:0"):
  x = tf.random.uniform([1000, 1000])
  assert x.device.endswith("CPU:0")
  time_matmul(x)

"""GPU #0가 이용가능시 GPU #0에서 강제 실행"""
if tf.test.is_gpu_available():
  print("On GPU:")
  with tf.device("GPU:0"): # Or GPU:1 for the 2nd GPU, GPU:2 for the 3rd etc.
    x = tf.random.uniform([1000, 1000])
    assert x.device.endswith("GPU:0")
    time_matmul(x)
```

결과를 보면,

```python
10 loops: 158.22ms # CPU
10 loops: 540.72ms # GPU
```

아이러니 하게도 CPU가 3배 정도 빠른 결과를 보여주었다. 생각하기에는 아마도 굉장히 간단한 연산이라서 단일 연산처리에 우수한 CPU가 더 빠른 성능을 보인게 아닐까싶다. 아마다 대량의 텐서 연산으로 가게되면 GPU가 병렬처리를 통해 훨씬 더 우수한 성능을 낼 것이다.



## Reference
- https://www.tensorflow.org/tutorials/customization/basics?hl=ko#gpu_%EA%B0%80%EC%86%8D

