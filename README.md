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


#### B. Hetero-scedastic q(z|x)

##### - In the sup-training, use q(z|x) = N(z; m(x), s(x)^2)

##### - Then in the unsup training, update both m(x) and s(x)


### 1) Unsup-training results with setup-A

- We fixed prior p(z) as ground-truth as follows

![p_den_2](https://user-images.githubusercontent.com/44901665/57574468-8976e200-7431-11e9-886c-71b9f98df049.jpg)





### 2) Unsup-training results with setup-B (Hetero-scedastic, update both m(x) and s(x))

- We fixed prior p(z) as ground-truth as follows

![p_den_2](https://user-images.githubusercontent.com/44901665/57574468-8976e200-7431-11e9-886c-71b9f98df049.jpg)

#### q(z)

- Before learning starts (ie, the supervised-trained VAE)

![q_den_2](https://user-images.githubusercontent.com/44901665/57693064-34f58180-7640-11e9-9692-2ab0fd927d6b.jpg)

- At iter# 35

![q_den_35](https://user-images.githubusercontent.com/44901665/57693065-34f58180-7640-11e9-827e-966c9d9f0ae5.jpg)

- At iter# 100

![q_den_100](https://user-images.githubusercontent.com/44901665/57693066-34f58180-7640-11e9-8aa8-dc9f220d4c54.jpg)

- At iter# 200

![q_den_200](https://user-images.githubusercontent.com/44901665/57693067-358e1800-7640-11e9-85e5-01ad1eab31ef.jpg)

- At iter# 300

![q_den_300](https://user-images.githubusercontent.com/44901665/57693069-358e1800-7640-11e9-8479-627e9b6d3a12.jpg)

