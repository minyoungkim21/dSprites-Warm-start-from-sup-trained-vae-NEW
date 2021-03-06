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


### 1) Unsup-training results with setup-A (Homo-scedastic, s_j = 2.0 * Delta_j)

- We fixed prior p(z) as ground-truth as follows

![p_den_2](https://user-images.githubusercontent.com/44901665/57574468-8976e200-7431-11e9-886c-71b9f98df049.jpg)

#### q(z)

- Before learning starts (ie, the supervised-trained VAE)

![q_den_2](https://user-images.githubusercontent.com/44901665/57694289-412f0e00-7643-11e9-9046-2a42d50d2223.jpg)

- At iter# 100

![q_den_100](https://user-images.githubusercontent.com/44901665/57694291-412f0e00-7643-11e9-8838-2b4c52253761.jpg)

- At iter# 200

![q_den_200](https://user-images.githubusercontent.com/44901665/57694292-41c7a480-7643-11e9-8713-47a583f8d1df.jpg)

- At iter# 300

![q_den_300](https://user-images.githubusercontent.com/44901665/57694293-41c7a480-7643-11e9-8e74-5786bef2af3a.jpg)

- At iter# 400

![q_den_400](https://user-images.githubusercontent.com/44901665/57694295-41c7a480-7643-11e9-81ee-e3ff0d43d2e3.jpg)


#### q(z|x) 

- Before learning starts

![qx_den_2](https://user-images.githubusercontent.com/44901665/57694309-4ab87600-7643-11e9-88c1-bebe847da5d8.jpg)

- At iter# 100

![qx_den_100](https://user-images.githubusercontent.com/44901665/57694310-4ab87600-7643-11e9-8f2a-2ab97883b467.jpg)

- At iter# 200

![qx_den_200](https://user-images.githubusercontent.com/44901665/57694311-4ab87600-7643-11e9-8ba6-94d5300936c9.jpg)

- At iter# 300

![qx_den_300](https://user-images.githubusercontent.com/44901665/57694313-4ab87600-7643-11e9-8042-f20ff7d80ff7.jpg)

- At iter# 400

![qx_den_400](https://user-images.githubusercontent.com/44901665/57694314-4b510c80-7643-11e9-9c3a-ce97d41c2ef6.jpg)


#### Latent traversal

- Before learning starts

![fixed0](https://user-images.githubusercontent.com/44901665/57694347-63c12700-7643-11e9-9f03-26a4a2d8d1be.gif)

- At iter# 100

![fixed0](https://user-images.githubusercontent.com/44901665/57694350-6754ae00-7643-11e9-85f7-6e76ca19cd0c.gif)

- At iter# 200

![fixed0](https://user-images.githubusercontent.com/44901665/57694381-720f4300-7643-11e9-9bfa-26afdb11be8a.gif)

- At iter# 300

![fixed0](https://user-images.githubusercontent.com/44901665/57694392-7c314180-7643-11e9-9335-63b0b8609a2a.gif)

- At iter# 400

![fixed0](https://user-images.githubusercontent.com/44901665/57694412-85baa980-7643-11e9-8895-4ab0eb3d700a.gif)


#### Loss functions and evaluation metrics

- recon loss

![recon](https://user-images.githubusercontent.com/44901665/57694440-966b1f80-7643-11e9-8e9f-d6a2950d35b9.png)

- kl loss

![kl](https://user-images.githubusercontent.com/44901665/57694437-95d28900-7643-11e9-9946-79466b48a599.png)

- metrics

![metrics](https://user-images.githubusercontent.com/44901665/57694439-95d28900-7643-11e9-86ef-1aa2794a087b.png)


----


### 2) Unsup-training results with setup-B (Hetero-scedastic, update both m(x) and s(x))

- We fixed prior p(z) as ground-truth as follows

![p_den_2](https://user-images.githubusercontent.com/44901665/57574468-8976e200-7431-11e9-886c-71b9f98df049.jpg)

#### q(z)

- Before learning starts (ie, the supervised-trained VAE)

![q_den_2](https://user-images.githubusercontent.com/44901665/57693445-26f43080-7641-11e9-8fb7-8bf04d63aac1.jpg)

- At iter# 100

![q_den_100](https://user-images.githubusercontent.com/44901665/57693446-26f43080-7641-11e9-8f0c-9b3eb1ac4a00.jpg)

- At iter# 200

![q_den_200](https://user-images.githubusercontent.com/44901665/57693447-26f43080-7641-11e9-9433-dd16d4c63944.jpg)

- At iter# 300

![q_den_300](https://user-images.githubusercontent.com/44901665/57693448-26f43080-7641-11e9-9496-8a39fc177780.jpg)

- At iter# 400

![q_den_400](https://user-images.githubusercontent.com/44901665/57693449-26f43080-7641-11e9-80f2-1da0cf6337d2.jpg)


#### q(z|x) 

- Before learning starts

![qx_den_2](https://user-images.githubusercontent.com/44901665/57693460-2d82a800-7641-11e9-8e4a-087159a34903.jpg)

- At iter# 100

![qx_den_100](https://user-images.githubusercontent.com/44901665/57693461-2d82a800-7641-11e9-9a8d-c7355031a84b.jpg)

- At iter# 200

![qx_den_200](https://user-images.githubusercontent.com/44901665/57693462-2d82a800-7641-11e9-9a8e-5a36980f74e6.jpg)

- At iter# 300

![qx_den_300](https://user-images.githubusercontent.com/44901665/57693464-2d82a800-7641-11e9-8237-6dd3ec13b936.jpg)

- At iter# 400

![qx_den_400](https://user-images.githubusercontent.com/44901665/57693465-2d82a800-7641-11e9-8a4b-35bc785e2ab4.jpg)


#### Latent traversal

- Before learning starts

![fixed0](https://user-images.githubusercontent.com/44901665/57693609-86ead700-7641-11e9-8fca-7e2b5201731c.gif)

- At iter# 100

![fixed0](https://user-images.githubusercontent.com/44901665/57693628-95d18980-7641-11e9-90ff-8500b857e09d.gif)

- At iter# 200

![fixed0](https://user-images.githubusercontent.com/44901665/57693635-9d912e00-7641-11e9-8a46-26c5f65f7272.gif)

- At iter# 300

![fixed0](https://user-images.githubusercontent.com/44901665/57693657-a681ff80-7641-11e9-887c-4cb16dbbd89b.gif)

- At iter# 400

![fixed0](https://user-images.githubusercontent.com/44901665/57693669-b13c9480-7641-11e9-9c81-9074cd062e47.gif)


#### Loss functions and evaluation metrics

- recon loss

![recon_hetero](https://user-images.githubusercontent.com/44901665/57693839-18f2df80-7642-11e9-8e1b-3910df7ccb3c.png)

- kl loss

![kl_hetero](https://user-images.githubusercontent.com/44901665/57693837-185a4900-7642-11e9-8efe-b9386cad002f.png)

- metrics

![metrics_hetero](https://user-images.githubusercontent.com/44901665/57693838-18f2df80-7642-11e9-9aab-880f4dd2ca7c.png)


