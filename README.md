# Real-time-Coherent-Style-Transfer-For-Videos
This is a PyTorch implementation of the paper ReCoNet.
## Abstract
We aim to build a generalisable neural style transfer network for videos with temporal consistency and efficient real time style transfer using any modern GPU. All the past techniques haven't been able to accomplish real-time efficient style transfer either lacking in temporal consistency, nice perceptual style quality or fast processing. Here we have used ReCoNet, which tried to mitigate all these problems.
## ReCoNet
ReCoNet is a feed forward neural network, which stylises videos frame by frame through an encoder and subsequently a decoder, and a VGG loss network to capture the perceptual style of the transfer target.<br>
The temporal loss is guided by occlusion masks and optical flow.<br>
Only the encoder and decoder run during inference which makes ReCoNet very efficient, running above real-time standards on modern GPUs.<br>
The network is illustrated in the figure below:<br>

![enter image description here](https://github.com/skq024/Real-time-Coherent-Style-Transfer-For-Videos/blob/master/network.png)

## Loss functions and optimisation
The network consists of a multi level temporal loss which focuses on temporal coherence at both high level feature maps and the final stylised output. The high level features do not involve the effect of luminance and hence, whereas the finalised output has a luminance term included.<br>
The perceptual losses are calculated using the VGG 16 network, and involve the content loss, style loss and the total variation regularizer. They are calculated on each frame separately and then summed up with the temporal losses for the particular frame.<br>
The final loss function is:<br>
![enter image description here](https://github.com/skq024/Real-time-Coherent-Style-Transfer-For-Videos/blob/master/finalloss.png)
## Requirements
Run the Requirements.txt file to install all the dependencies.
## References
-->[Real Time Coherent Video Style Transfer Network][1]
[1]: https://arxiv.org/pdf/1807.01197.pdf      "Real Time Coherent Video Style Transfer Network" <br>
-->https://pytorch.org/tutorials/advanced/neural_style_tutorial.html\ <br>
-->https://github.com/irsisyphus/reconet/blob/master/network.py <br>
-->https://github.com/NVlabs/PWC-Net/blob/master/PyTorch/models/PWCNet.py 
