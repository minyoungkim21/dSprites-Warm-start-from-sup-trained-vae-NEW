# dSprites: Warm-start from the VAE model trained with full supervision (Additional Results)

### 0) Setups

#### A. Homo-scedastic q(z|x) 

##### - In the sup-training, use q(z|x) = N(z; m(x), s^2), ie, s(x) = s for all x

##### - Then in the unsup training, update only m(x) while fixing s as:

- s = (1e-4)/3 fixed -- already done in: 
https://github.com/minyoungkim21/dSprites-Warm-start-from-VAE-trained-with-supervision/edit/master/README.md

- s = s* fixed (where s* = MLE stdev from sup-training, ie, s* = sqrt( 1/N \sum_n (z^n - m*(x^n))^2 ) for the optimal m*())

--> Actually, s* = (shape: 0.0023, size: 0.0098, rotation: 0.278, x-pos: 0.005, y-pos: 0.005)
--> The results were similar to s = (1e-4)/3

- s_j = 2.0 * Delta_j (where Delta_j = gap b/w two adjacent GT z_j points, eg, Delta_shape = 0.9)


#### B. Hetero-scedastic q(z|x) = N(z; m(x), s(x)^2)

Oncesup-trained,


### 1) Train VAE with full supervision

#### Fully labeled factors (scaled to [-1,1])
- z1 (shape; card=3) = {-0.9, 0, 0.9}
- z2 (size; card=6) = {-0.9, -0.54, -0.18, 0.18, 0.54, 0.9}
- z3 (rotation; card=40) = {-0.9, -0.88, ..., 0.88, 0.9}
- z4 (x-pos, card=32) = {-0.9, -0.87, ..., 0.87, 0.9}
- z5 (y-pos, card=32) = {-0.9, -0.87, ..., 0.87, 0.9}

#### Learning p(x|z) and q(z|x) with observed (x,z)
- Decoder: Maximize \sum_{(x,z)} \log p(x|z) 
- Encoder: Maximize \sum_{(x,z)} \log q(z|x) with sigma of q(z|x) fixed to small value (eg, (1e-4)/3). Ie, only learn the mean function


### 2) Now, standard (unsupervised) VAE learning with initial model from 1)

- We fixed prior p(z) as follows: (z1, z2, z3, z4, z5)

![p_den_2](https://user-images.githubusercontent.com/44901665/57574468-8976e200-7431-11e9-886c-71b9f98df049.jpg)

- sigma of q(z|x) also fixed to ((1e-4)/3). Ie, only learn the mean function.
