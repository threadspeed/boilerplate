---
title: python script Captcha Project GenerateTest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Captcha Project GenerateTest'

Functions in program: 
* `def generate(num_char):`

Modules used in program: 
* `import numpy as np`
* `import random`
* `import string`
* `import matplotlib.pyplot as plt`

## python Captcha Project GenerateTest

Python example: Captcha Project GenerateTest

```python
# Code from https://mathematica.stackexchange.com/questions/143691/crack-captcha-using-deep-learning
from captcha.image import ImageCaptcha
import matplotlib.pyplot as plt
import string
import random
import numpy as np


def generate(num_char):
    characters = string.digits + string.ascii_uppercase
    rand_str = ''.join(random.sample(characters, num_char))
    image = ImageCaptcha().generate_image(rand_str)
    return (image, rand_str)


# images and labels will be in saved to save_dir folder
save_dir = '/home/wenlong/Captcha/'
labels = []

# generate first image
img1, char1 = generate(4)
im1 = np.array(img1)
plt.imsave(save_dir + 'test/testImages/0.png', im1)
labels.append(char1)
if(im1.shape[1] > 160):
    print('warning: processed')
    for j in xrange(im1.shape[1] - 160):
        im1 = np.delete(im1, 160, 1)
rawPix = im1.reshape((3, 60, 160)).flatten()

# generate images
for i in range(499):
    img, char = generate(4)
    im = np.array(img)
    plt.imsave(save_dir + 'test/testImages/' + str(i + 1) + '.png', im)
    labels.append(char)
    print(im.shape)
    if(im.shape[1] > 160):
        print('warning: processed')
        for j in xrange(im.shape[1] - 160):
            im = np.delete(im, 160, 1)
    pix = im.reshape((3, 60, 160)).flatten()
    rawPix = np.concatenate([rawPix, pix])

# save images into binary file
rawPix.tofile(save_dir + 'test/testData.bin')

# save labels
with open(save_dir + 'test/labels.bin', 'w') as f:
    for lb in labels:
        f.write('%s\n' % lb)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
