# rapid-kube
A quick way to get started with kubernetes, minikube and kube-prompt

# Overview
In this tutorial, we're going to setup ```minikube``` on our local machine. We're going to examine where ```minikube``` stores it's configuration. We'll then make use of a tool called ```kube-prompt``` to save ourselves from typing ```kubectl``` on every command. We'll set up some monitoring using ```Heapster```. Finally, we'll get used to using a package manager called ```helm```. Let's get started. 
> From now on we'll assume we're on a MAC. 
# Set up
For this you'll need [virtualbox for MAC OSX](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwi827GU-67WAhVUzWMKHdf2D-cQFggoMAA&url=https%3A%2F%2Fwww.virtualbox.org%2Fwiki%2FDownloads&usg=AFQjCNHg31Pp26-AJ-5fjqSw3azAsjfvpg)

Let's get ```minikube``` on our local machine. Go to [https://github.com/kubernetes/minikube/releases]. 
Run the command for the latest release:
 ```curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.22.1/minikube-darwin-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/```

This will take a few minutes. This will install ```minikube``` on your machine and make it available in your terminal by copying it to ```/usr/local/bin```. This should take care of any PATH issues. 
Once this is done, notice: in your $HOME dir there is no ```.minikube``` directory. 

Now run ```minikube start```

This will take another few minutes as it has to download the .iso to set up the VM. 

Once complete, run ```ls -ltr ~/.minikube```
You'll see all the ```minikube``` setup files are stored here. (Important for later)

Now check VirtualBox, you'll see the ```minikube``` vm is running. 

Run ```minikube status```. 

```minikube status
   minikube: Running
   cluster: Running
   kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.101
```

Now, let's get into the ```minikube dashboard```. 


