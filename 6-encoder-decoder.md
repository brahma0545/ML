---
layout: page
title: Encoder - Decoder Architecture with subclassing API
step: 6
---
# 1. Writing a custom Layers

before we write custom layers in tensorflow lets see the definition of <b>Layers</b> class


>From the <a href='https://www.tensorflow.org/api_docs/python/tf/keras/layers/Layer'> tf.keras.layers.Layers</a> documentation:
<ul>
<li>this is the class from which all layers inherit.</li>
<li>A layer is a class implementing common neural networks operations, such as convolution, batch norm, etc. These operations require managing weights, losses, updates, and inter-layer connectivity.</li>
<li>Users will just instantiate a layer and then treat it as a callable.</li>
<li>We recommend that descendants of Layer implement the following methods:</li>
<pre>
+--------------------------------------------------------------------+
|<strong> def __init__(self, trainable=True, name=None, dtype=None,</strong>          |
|<strong> dynamic=False, **kwargs):</strong>                                          |
+--------------------------------------------------------------------+
|                                                                    |
|* the properties should be set by the user via keyword arguments.   |
|                                                                    |
|* note that 'dtype', 'input_shape' and 'batch_input_shape' are only applicable to input layers, do not pass these  |
|  keywords to non-input layers.                                     |
+--------------------------------------------------------------------+
|* allowed_kwargs = {'input_shape', 'batch_input_shape', 'batch_size', 'weights', 'activity_regularizer','autocast'}|
+--------------------------------------------------------------------+
</pre>
<pre>
+--------------------------------------------------------------------+
|<strong> def build(self, input_shape)</strong>:                                      |
+--------------------------------------------------------------------+
|                                                                    |
| * Creates the variables of the layer (optional, for subclass implementers). This is a method that implementers of                        |
|   subclasses of `Layer` or `Model`                                 |
|                                                                    |
| * You can override if you need a state-creation step in-between <em><font color='yellow'>layer instantiation</font></em> and <em><font color='yellow'>layer call</font></em>.                                      |
|                                                                    |
| * This is typically used to create weights of `Layer` subclasses.  |
+--------------------------------------------------------------------+
| Arguments:                                                                                                        |
|    input_shape:                                                                                                   |
|    Instance of `TensorShape`, or list of instances of `TensorShape` if the layer expects a list of inputs         |
+--------------------------------------------------------------------+
</pre>

<pre>
+--------------------------------------------------------------------+
| <strong> def call(self, inputs, **kwargs)</strong>:                                 |
+--------------------------------------------------------------------+
| * This is where the layer's logic lives.                           |
+--------------------------------------------------------------------+
|* Arguments:                                                        |
|        inputs: Input tensor, or list/tuple of input tensors.       |
|        **kwargs: Additional keyword arguments.                     |
+--------------------------------------------------------------------+
|* Returns:                                                          |
|        A tensor or list/tuple of tensors.                          |
+--------------------------------------------------------------------+
<a href='https://github.com/tensorflow/tensorflow/blob/r2.1/tensorflow/python/keras/engine/base_layer.py#L310'>check this link for more arguments</a>
</pre>


<pre>
+--------------------------------------------------------------------+
|<strong> def add_weight(self,name=None, shape=None, ..., **kwargs)</strong>:         |
+--------------------------------------------------------------------+
|* Adds a new variable to the layer.                                 |
+--------------------------------------------------------------------+
|* Arguments:                                                        |
|        name : Variable name.                                       |
|        shape: Variable shape. Defaults to scalar if unspecified.   |
|        dtype: The type of the variable. Defaults to `self.dtype` or|
|               float32.                                             |
+--------------------------------------------------------------------+
|* Returns:                                                          |
|        The created variable. Usually either a `Variable` or `ResourceVariable` instance.                                                 |
+--------------------------------------------------------------------+
</pre>
...
there are other functions also availabel, please check this link for better understanding of it
<a href='https://github.com/tensorflow/tensorflow/blob/r2.1/tensorflow/python/keras/engine/base_layer.py'>base_layer.py</a>

</ul>



## 1.1 Example
read mode about `super` function <a href='https://stackoverflow.com/a/27134600/4084039 '>here</a>:
<img src='https://i.imgur.com/1a8N7gH.png' width=600 class='image_cent'>

## 1.2 Resources
Do read <a href='https://www.tensorflow.org/guide/keras/custom_layers_and_models'>this blog</a> for more information:
few screenshots from the above blog

1. <img src='https://i.imgur.com/SDNQgos.png' width=600>
2. <img src='https://i.imgur.com/syqjpux.png' width=600>
3. <img src='https://i.imgur.com/PfmYWno.png' width=600>


# 2. Writing a custom Model
There are three ways to implement a model architecture in TF
  <img src='https://i.imgur.com/n7DBcoo.png' width=400 class='image_cent'>
The third and final method to implement a model architecture using Keras and TensorFlow 2.0 is called model subclassing.

Inside of tf.keras the `Model` class is the root class used to define a model architecture. Since tf.keras utilizes object-oriented programming, we can actually `subclass` the Model class and then insert our architecture definition.

<pre>
    The `Model` class has the same API as `Layer`, with the following differences:
        It exposes built-in training, evaluation, and prediction loops (model.fit(), model.evaluate(), model.predict()).
        It exposes the list of its inner layers, via the `model.layers` property.
        It exposes saving and serialization APIs.
</pre>

> Effectively, the "Layer" class corresponds to what we refer to in the literature as a "layer" (as in "convolution layer" or "recurrent layer") or as a "block" (as in "ResNet block" or "Inception block").

>Meanwhile, the "Model" class corresponds to what is referred to in the literature as a "model" (as in "deep learning model") or as a "network" (as in "deep neural network").

## 2. 1 Example
<pre>
class MyDenseLayer(tf.keras.layers.Layer):
    def __init__(self, num_outputs, **kwargs):
        super().__init__(**kwargs)
        self.num_outputs = num_outputs

    def build(self, input_shape):
        self.kernel = self.add_weight("kernel", shape=[int(input_shape[-1]), self.num_outputs])

    def call(self, input):
        print(input.shape,self.kernel.shape)
        return tf.matmul(input, self.kernel)


class MyModel(Model):
    def __init__(self, num_inputs, num_outputs, rnn_units):
        super().__init__()
        self.dense = MyDenseLayer(num_outputs, name='myDenseLayer')
        <font color='grey'>
        # not thet we can't use LSTM layer or RNN layer, if you want to use LSTM, you need to write like this
        # self.lstmcell = tf.keras.layers.LSTMCell(rnn_units)
        # self.rnn = RNN(self.lstmcell)
        </font>
        self.softmax = Softmax()

    def call(self, input):
        <font color='grey'>
        # output = self.rnn(input)
        </font>
        output = self.dense(input)
        output = self.softmax(output)
        return output

import numpy as np
data = np.zeros([10, 5])
y = np.zeros([10,2])

model  = MyModel(num_inputs=5, num_outputs=2, rnn_units=32)

loss_object = tf.keras.losses.BinaryCrossentropy()
optimizer = tf.keras.optimizers.Adam()

model.compile(optimizer=optimizer,loss=loss_object)
model.fit(data,y, steps_per_epoch=1)

model.summary()
</pre>
__Output__:
<img src='https://i.imgur.com/8HOOu9l.png' class='image_cent'>

<h1 id="encoder-decoder">3. Building Encoder-Decoder Architecture with the custom layers</h1>
__Encoder Architecture__
<img src='https://i.imgur.com/udXhBC2.png' width="100%">

__Decoder Architecture__
<img src='https://i.imgur.com/DHOTX9P.png' width="100%">

__Custom Model Architecture__
<img src='https://i.imgur.com/3IvvNOC.png' width="100%">

__Model compiling and Training__
<pre>
model  = MyModel(encoder_inputs_length=10,decoder_inputs_length=10,output_vocab_size=500)

ENCODER_SEQ_LEN = 30
DECODER_SEQ_LEN = 20

input = np.random.randint(0, 499, size=(2000, ENCODER_SEQ_LEN))
output = np.random.randint(0, 499, size=(2000, DECODER_SEQ_LEN))
target = tf.keras.utils.to_categorical(output, 500)

# loss_object = loss_object = tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True, reduction='none')
optimizer = tf.keras.optimizers.Adam()

model.compile(optimizer=optimizer,loss='sparse_categorical_crossentropy')

model.fit([input, output], output, steps_per_epoch=1)

"""
or you can try this

model.compile(optimizer=optimizer,loss='categorical_crossentropy')
model.fit([input, output], target, steps_per_epoch=1)

"""
model.summary()
</pre>
__Model output/verbose__
<pre>
-------------------- ENCODER --------------------
ENCODER ==> INPUT SQUENCES SHAPE : (?, 30)
ENCODER ==> AFTER EMBEDDING THE INPUT SHAPE : (?, 30, 50)
---------------------------
ENCODER ==> OUTPUT SHAPE (?, 30, 64)
ENCODER ==> HIDDEN STATE SHAPE (?, 64)
ENCODER ==> CELL STATE SHAPE (?, 64)
-------------------- DECODER --------------------
DECODER ==> INPUT SQUENCES SHAPE : (?, 20)
WE ARE INITIALIZING DECODER WITH ENCODER STATES : (?, 64) (?, 64)
---------------------------
FINAL OUTPUT SHAPE (?, 20, 500)
---------------------------
1/1 [==============================] - 4s 4s/step - loss: 6.2145
_________________________________________________________________
Layer (type)                 Output Shape              Param #
=================================================================
encoder (Encoder)            multiple                  54440
_________________________________________________________________
decoder (Decoder)            multiple                  54440
_________________________________________________________________
dense (Dense)                multiple                  32500
=================================================================
Total params: 141,380
Trainable params: 141,380
Non-trainable params: 0
_________________________________________________________________
</pre>


<h1 id="vanilla-seq2seq">4. Vanilla Seq2Seq</h1>
## 4.1 Seq2Seq in training

<p>The Seq2Seq framework relies on the <strong>encoder-decoder</strong> paradigm. The <strong>encoder</strong> <em>encodes</em> the input sequence, while the <strong>decoder</strong> <em>produces</em> the target sequence</p>

<p><strong>Encoder</strong></p>

<p>Our input sequence is <code class="highlighter-rouge">how are you</code>. Each word from the input sequence is associated to a vector \( w \in \mathbb{R}^d \) (via a lookup table). In our case, we have 3 words, thus our input will be transformed into \( [w_0, w_1, w_2] \in \mathbb{R}^{d \times 3} \). Then, we simply run an LSTM over this sequence of vectors and store the last hidden state outputed by the LSTM: this will be our encoder representation \( e \). Let’s write the hidden states \( [e_0, e_1, e_2] \) (and thus \( e = e_2 \))</p>

<img src="https://i.imgur.com/nToLTs2.png" class='image_cent'/>

<p><strong>Decoder</strong></p>

<p>Now that we have a vector \( e \) that captures the meaning of the input sequence, we’ll use it to generate the target sequence word by word. Feed to another LSTM cell: \( e \) as hidden state and a special <em>start of sentence</em> vector \( w_{sos} \) as input. The LSTM computes the next hidden state \( h_0 \in \mathbb{R}^h \). Then, we apply some function \( g : \mathbb{R}^h \mapsto \mathbb{R}^V \) so that \( s_0 := g(h_0) \in \mathbb{R}^V \) is a vector of the same size as the vocabulary.</p>

<script type="math/tex; mode=display">% <![CDATA[
\begin{align*}
h_0 &= \operatorname{LSTM}\left(e, w_{sos} \right)\\
s_0 &= g(h_0)\\
p_0 &= \operatorname{softmax}(s_0)\\
i_0 &= \operatorname{argmax}(p_0)\\
\end{align*} %]]></script>

<p>Then, apply a softmax to \( s_0 \) to normalize it into a vector of probabilities \( p_0 \in \mathbb{R}^V \) . Now, each entry of \( p_0 \) will measure how likely is each word in the vocabulary. Let’s say that the word <em>“comment”</em> has the highest probability (and thus \( i_0 = \operatorname{argmax}(p_0) $\) corresponds to the index of <em>“comment”</em>). Get a corresponding vector \( w_{i_0} = w_{comment} \) and repeat the procedure: the LSTM will take \( h_0 \) as hidden state and \( w_{comment} \) as input and will output a probability vector \( p_1 \) over the second word, etc.</p>

<script type="math/tex; mode=display">% <![CDATA[
\begin{align*}
h_1 &= \operatorname{LSTM}\left(h_0, w_{i_0} \right)\\
s_1 &= g(h_1)\\
p_1 &= \operatorname{softmax}(s_1)\\
i_1 &= \operatorname{argmax}(p_1)
\end{align*} %]]></script>

<p>The decoding stops when the predicted word is a special <em>end of sentence</em> token.</p>

<img src="https://i.imgur.com/WEPJChD.png" alt="Vanilla Decoder" class='image_cent' />

<blockquote>
  <p>Intuitively, the hidden vector represents the “amount of meaning” that has not been decoded yet.</p>
</blockquote>

<p>The above method aims at modelling the distribution of the next word conditionned on the beginning of the sentence</p>

<script type="math/tex; mode=display">\mathbb{P}\left[ y_{t+1} | y_1, \dots, y_{t}, x_0, \dots, x_n \right]</script>

<p>by writing</p>

<script type="math/tex; mode=display">\mathbb{P}\left[ y_{t+1} | y_t, h_{t}, e \right]</script>

the code in the <a href="#encoder-decoder">section 3</a> will in an implementation of the above concept.

## 4.2 Inference
<img src='https://i.imgur.com/cRwEjt6.png' width="100%">
__Output__
<pre>
============================== Inference ==============================
ENCODER ==> INPUT SQUENCES SHAPE : (1, 30)
ENCODER ==> AFTER EMBEDDING THE INPUT SHAPE : (1, 30, 50)
-------------------- started predition --------------------
at time step 0 the word is 0
at time step 0 the word is  [[55]]
at time step 0 the word is  [[55]]
at time step 0 the word is  [[55]]
at time step 0 the word is  [[9]]
at time step 0 the word is  [[50]]
at time step 0 the word is  [[18]]
at time step 0 the word is  [[23]]
at time step 0 the word is  [[56]]
at time step 0 the word is  [[56]]
at time step 0 the word is  [[56]]
at time step 0 the word is  [[56]]
at time step 0 the word is  [[56]]
at time step 0 the word is  [[56]]
at time step 0 the word is  [[56]]
at time step 0 the word is  [[25]]
at time step 0 the word is  [[63]]
at time step 0 the word is  [[25]]
at time step 0 the word is  [[12]]
at time step 0 the word is  [[12]]
at time step 0 the word is  [[3]]
</pre>

<div class="pagination">
  <a class="pagination-item older" href="{{ site.url }}{{ site.baseurl }}/5-loss-functions">&laquo; 5 Loss functions</a>
  <a class="pagination-item newer" href="{{ site.url }}{{ site.baseurl }}/7-seq-seq-models">7 Seq to Seq models &raquo;</a>
</div>
