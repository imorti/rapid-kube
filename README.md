# rapid-kube
A quick way to get started with kubernetes, minikube and kube-prompt

# Overview
In this tutorial, we're going to setup ```minikube``` on our local machine. We're going to examine where ```minikube``` stores it's configuration. We'll get `kubectl` configured to use our local cluster. We'll then make use of a tool called ```kube-prompt``` to save ourselves from typing ```kubectl``` on every command. We'll set up some monitoring using ```Heapster```. Finally, we'll get used to using a package manager called ```helm```. Let's get started. 
> From now on we'll assume we're on a MAC. 
# Set up
For this you'll need [virtualbox for MAC OSX](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwi827GU-67WAhVUzWMKHdf2D-cQFggoMAA&url=https%3A%2F%2Fwww.virtualbox.org%2Fwiki%2FDownloads&usg=AFQjCNHg31Pp26-AJ-5fjqSw3azAsjfvpg)

And let's install [Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-via-curl) the kubernetes CLI as well. 

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

Also, notice above the output reads `kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.101`. This means `kubectl` is already configured to point to our local cluster. 

Now, let's get into the dashboard. Run: ```minikube dashboard```. 

You'll see the minikube dashboard which is very close to the Kubernetes Dashboard you've probably seen in demos. 

Click from pods, to deployments to services. Notice: the only thing running is ```kubernetes``` itself. Just to make sure we're properly set up, let's run a few `kubectl` commands to look at our cluster from the command-line. 

Run:
1. `kubectl cluster-info`. You should see this as output: 
```Kubernetes master is running at https://192.168.99.101:8443```
```To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.```
   
Before we run workloads on our `minikube` we need to install [kube-prompt](https://github.com/c-bata/kube-prompt) - you'll thank me. `kube-prompt` is a command-completion tool for use with `kubectl`. 

Run: ```$ brew tap c-bata/kube-prompt```
   
   Then:
``` $ brew install kube-prompt```

This will save us from typing ```kubectl``` a million times. 

2. Now let's run `kube-prompt`. 
3. In our prompt we just have to run `get pods`, `get deployments` and `get services` to see what's running on our cluster. Do so now. 
Notice you can tab on your choices as you type? Yeah, that's `kube-prompt` at work!

