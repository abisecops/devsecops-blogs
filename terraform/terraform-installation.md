# Terraform installation

#### Let's install **Terraform** on our ubuntu server:&#x20;

<pre class="language-bash"><code class="lang-bash"># Update and install gnupg, software-properties-common
sudo apt-get update &#x26;&#x26; sudo apt-get install -y gnupg software-properties-common
<strong>#Install the HashiCorp GPG key
</strong><strong>wget -O- https://apt.releases.hashicorp.com/gpg | \
</strong>gpg --dearmor | \
sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
#Verify the key's fingerprint.
gpg --no-default-keyring \
--keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
--fingerprint
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update -y
# install terraform
sudo apt-get install terraform -y
</code></pre>

#### Verify the installation:&#x20;

```sh
 terraform -help
```

* We have successfully installed terraform in our system.&#x20;

Add any subcommand to `terraform -help` to learn more about **what it does and available options**.

```bash
terraform -help plan
```

#### &#x20;<a href="#enable-tab-completion" id="enable-tab-completion"></a>

#### Enable tab completion :  :thumbsup: <a href="#enable-tab-completion" id="enable-tab-completion"></a>

```bash
terraform -install-autocomplete
```

<figure><img src="../.gitbook/assets/image (181).png" alt=""><figcaption></figcaption></figure>

* Terraform has .tf extension file.&#x20;

a) Create a file main.tf then:&#x20;

```bash
terraform init
```

b) Format and validate the configuration:&#x20;

```bash
terraform fmt #format
```

```bash
terraform validate #validate
```

c) Then check the plan:&#x20;

```bash
terraform plan
```

d) Now, apply the config

```bash
terraform apply 
# :? yes ; in case all configuration/plan is correct
```

* Now check to the website. I installed nginx here.

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

* &#x20;If you also wanna try, check [install-jenkins-docker-image-with-terraform.md](install-jenkins-docker-image-with-terraform.md "mention")

