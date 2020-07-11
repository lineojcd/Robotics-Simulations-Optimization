# Jenkins Tutorial
A detailed installation tutorial ```Jenkins Installation Guide.pdf``` can be found in the current folder.
  
## Pre-installation check
**Java8** and **python 3.6+** is need for installing Jenkins. 

To check if you have Java8 or not, type the command in your terminal:
```
java -version
```
To check if you have python3 or not, type the command in your terminal:
```
python3
```

##Install Jenkins on ubuntu
```
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins
```
Now, we are done with Jenkins Installation!

##Jenkins Service
You can start the Jenkins service with the command:
```
sudo systemctl start jenkins
```
You can check the status of the Jenkins service using the command:
```
sudo systemctl status jenkins
```
You can stop the Jenkins service with the command:
```
service jenkins stop
```
## Connect to Jenkins Dashboard 
```
http://localhost:8080/
```
####Authentification for first time connection: 
If you are the first time to connect to Jenkins dashboard, it will ask your password. 
Just follow what it instructed by typing the command at the terminal and copy the password back to unlock Jenkins : 
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```




### [PyTorch & torchvision](http://pytorch.org/)
Follow the instructions in [pytorch.org](http://pytorch.org) for your current setup

### [Visdom](https://github.com/facebookresearch/visdom)
To plot loss graphs and draw images in a nice web browser view
```
pip3 install visdom
```

## Training
### 1. Setup the dataset
First, you will need to download and setup a dataset. The easiest way is to use one of the already existing datasets on UC Berkeley's repository:
```
./download_dataset <dataset_name>
```
Valid <dataset_name> are: apple2orange, summer2winter_yosemite, horse2zebra, monet2photo, cezanne2photo, ukiyoe2photo, vangogh2photo, maps, cityscapes, facades, iphone2dslr_flower, ae_photos

Alternatively you can build your own dataset by setting up the following directory structure:

    .
    ├── datasets                   
    |   ├── <dataset_name>         # i.e. brucewayne2batman
    |   |   ├── train              # Training
    |   |   |   ├── A              # Contains domain A images (i.e. Bruce Wayne)
    |   |   |   └── B              # Contains domain B images (i.e. Batman)
    |   |   └── test               # Testing
    |   |   |   ├── A              # Contains domain A images (i.e. Bruce Wayne)
    |   |   |   └── B              # Contains domain B images (i.e. Batman)
    
### 2. Train!
```
./train --dataroot datasets/<dataset_name>/ --cuda
```
This command will start a training session using the images under the *dataroot/train* directory with the hyperparameters that showed best results according to CycleGAN authors. You are free to change those hyperparameters, see ```./train --help``` for a description of those.

Both generators and discriminators weights will be saved under the output directory.

If you don't own a GPU remove the --cuda option, although I advise you to get one!

You can also view the training progress as well as live output images by running ```python3 -m visdom``` in another terminal and opening [http://localhost:8097/](http://localhost:8097/) in your favourite web browser. This should generate training loss progress as shown below (default params, horse2zebra dataset):

![Generator loss](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/loss_G.png)
![Discriminator loss](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/loss_D.png)
![Generator GAN loss](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/loss_G_GAN.png)
![Generator identity loss](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/loss_G_identity.png)
![Generator cycle loss](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/loss_G_cycle.png)

## Testing
```
./test --dataroot datasets/<dataset_name>/ --cuda
```
This command will take the images under the *dataroot/test* directory, run them through the generators and save the output under the *output/A* and *output/B* directories. As with train, some parameters like the weights to load, can be tweaked, see ```./test --help``` for more information.

Examples of the generated outputs (default params, horse2zebra dataset):

![Real horse](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/real_A.jpg)
![Fake zebra](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/fake_B.png)
![Real zebra](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/real_B.jpg)
![Fake horse](https://github.com/ai-tor/PyTorch-CycleGAN/raw/master/output/fake_A.png)

## License
This project is licensed under the GPL v3 License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments
Code is basically a cleaner and less obscured implementation of [pytorch-CycleGAN-and-pix2pix](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix). All credit goes to the authors of [CycleGAN](https://arxiv.org/abs/1703.10593), Zhu, Jun-Yan and Park, Taesung and Isola, Phillip and Efros, Alexei A.
