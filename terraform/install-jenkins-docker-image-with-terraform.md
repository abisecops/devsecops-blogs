# Install jenkins docker image with Terraform

#### Today we are going to install jenkins docker image with the help of terraform. Let's do it:&#x20;

```
mkdir learn-terraform-docker-container
cd mkdir learn-terraform-docker-container
sudo nano main.tf
```

#### Let's create a terraform file to create the docker image of jenkins: 

```bash
sudo nano main.tf
```

```bash
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
}

provider "docker" {}

resource "docker_image" "jenkins" {
  name = "jenkins/jenkins:lts-jdk17"
}

resource "docker_container" "jenkins" {
  image = docker_image.jenkins.name
  name  = "jenkins_server"
  ports {
    internal = 8080
    external = 8080
  }
}
```

<figure><img src="../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

#### Now, init the terraform:&#x20;

```bash
terraform init
```

<figure><img src="../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

#### Format and validate the configuration

```bash
terraform fmt
terraform validate
```

#### Now, check plan and apply

```bash
terraform plan
terraform apply 
# yes if all plan are checked correctly
```

<figure><img src="../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

```
terraform apply
```

<figure><img src="../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

* Prompt **yes** only your configuration is correct: \


<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

* If you're using localhost, you can try: [http://localhost:8080](http://localhost:8080)
* Otherwise you can also try ngrok as I already mention on the [terraform-installation.md](terraform-installation.md "mention")

#### Tmux will be more helpful to you for testing:&#x20;

```bash
tmux -s new jenkins
ngrok http 8080
```

* ctrl + b and then press d to disattach the session
* Later, you can also use

```
tmux attach -t jenkins # to attach the session
```

Your session will run on background.&#x20;

Now access the public URL and here it goes:&#x20;

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

Now, get the password; In my case:&#x20;

```bash
docker ps
docker exec -it a1c2cbf17f72 /bin/bash
cat /var/jenkins_home/secrets/initialAdminPassword

```

<figure><img src="../.gitbook/assets/image (182).png" alt=""><figcaption></figcaption></figure>

Login this admin credentials:&#x20;

<figure><img src="../.gitbook/assets/image (183).png" alt=""><figcaption></figcaption></figure>
