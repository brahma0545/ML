---
layout: page
title: Attention Mechanism Explained
nav_title: loss functions
step: 7
---

We have seen the Encoder Decoder architecture in the previous blog, now lest check if we can do any better than passing last layer timestep outputs to first timestep of decoder.

Most of this blog will be based on <a href='https://arxiv.org/pdf/1508.04025.pdf'>this paper.

<!-- <iframe src="https://arxiv.org/pdf/1508.04025.pdf" width="100%" height="500px"> -->
<object width="100%" height="500" type="application/pdf" data="https://arxiv.org/pdf/1508.04025.pdf?#zoom=85&scrollbar=0&toolbar=0&navpanes=0">
    <p>Insert your error message here, if the PDF cannot be displayed.</p>
</object>
 its not mandotory to go through this paper, i will try to simplify things. But It will be very nice if you can spend some time to go through it.

 Most of this blog will be based on the images that i have created in using powerpoint.

<img src='https://i.imgur.com/OgxuAaM.jpg' width="100%">

<img src='https://i.imgur.com/7VhsNER.jpg' width="100%">

<img src='https://i.imgur.com/FIUe33r.jpg' width="100%">

<img src='https://i.imgur.com/aAGSfN1.jpg' width="100%">

<img src='https://i.imgur.com/oEyRXSB.jpg' width="100%">
credit: <a href ='https://guillaumegenthial.github.io/assets/img2latex/seq2seq_attention_mechanism_new.svg'>https://guillaumegenthial.github.io</a>

<ol>
<li>
<ul>
<li><img src='https://i.imgur.com/wX7RtF8.jpg' width="100%"></li>
<li><img src='https://i.imgur.com/Vh01Sf3.jpg' width="100%"></li>
<li><img src='https://i.imgur.com/Vh01Sf3.jpg' width="100%"></li>
<li><img src='https://i.imgur.com/JWOD8JM.jpg' width="100%"></li>
</ul>
</li>

<li>
<ul>
<li><img src='https://i.imgur.com/A17EPNJ.jpg' width="100%"></li>
</ul>
</li>

<li>
<ul>
<li><img src='https://i.imgur.com/S08e16r.jpg' width="100%"></li>
</ul>
</li>

<li>
<ul>
<li><img src='https://i.imgur.com/1eB1Mrl.jpg' width="100%"></li>
</ul>
</li>

<li>
<ul>
<li><img src='https://i.imgur.com/3f7graC.jpg' width="100%"></li>
</ul>
</li>

</ol>
<img src='https://i.imgur.com/WyKmkOF.jpg' width="100%" >
Note: I am not including the full code here, as this is the part of the assignments of <a href='https://classroom.appliedcourse.com/'>appliedaicourse</a>

<div class="pagination">

  <a class="pagination-item older" href="{{ site.url }}{{ site.baseurl }}/6-encoder-decoder">&laquo; 6 Encoder Decoder Architecture</a>
  <a class="pagination-item newer" href="{{ site.url }}{{ site.baseurl }}/7-seq-seq-models">3 Backpropagation &raquo;</a>
</div>
