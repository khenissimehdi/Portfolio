---
title: "Pritunl VPN GCP"
date: 2024-02-11
draft: false
project_tags: ["vpn", "how-to"]
status: "seeding"
summary: "Details on how to host pritunl vpn on gpc"
weight: 1
---

In the digital age, secure network access is paramount. This guide focuses on hosting Pritunl VPN, an open-source VPN solution, on Google Cloud Platform (GCP). Pritunl offers ease of use and advanced security, supporting protocols like OpenVPN and WireGuard. Deploying on GCP leverages reliable infrastructure for scalable, global VPN servers. We'll cover setting up Pritunl on GCP, ensuring a secure, private network for either personal or business use.

### GCP side 

### Creating the instance on GCP
First, we create new E2 instance in one of the us-east1, us-west1, and us-central1 regions. I’m using image Ubuntu 22.04 LTS, we don’t need any SSD, just persistent 10Gb disk, we need to allow HTTP and HTTPS traffic, our VPN server will be available over HTTPs and we need HTTP for LetsEncrypt verification DON'T FORGET to enable port forwarding and add the tag vpn-server we will need it later.


{{< figure src="gcp1.png" width="100%" >}}

{{< figure src="gcp2.png" width="100%">}}


#### Adding firewall rules on GCP 

In the VPC network->Firewall rules we need to add port for our VPN server, I’m using port UDP 18450 you can use another.

Node : On diffrent cloud providers you can skip adding an new firewall rule. 
{{< figure src="gcp3.png" width="100%" >}}

{{< figure src="gcp4.png" width="100%">}}

### Setting up pritunl 

Our instance is now prepared, and we can proceed with installing the Pritunl server. To do this, please SSH into your machine. This can be accomplished through the GCP web UI. Once you have access to your instance, follow the instructions provided in the [Pritunl Documentation](https://docs.pritunl.com/docs/installation) for Ubuntu Jammy.


#### Pritunl Web UI 

##### Level 0 
Once the installation is complete, you can access your admin page through the public IP address provided by GCP. While setting up a domain is recommended for long-term use, for learning purposes, we'll bypass this step here.
{{< figure src="pritunl1.png" width="70%">}}


To initiate the configuration, execute the command `pritunl setup-key` to retrieve the setup key. Initially, the MongoDB URI is pre-configured to connect to the MongoDB server hosted locally. This default setting is appropriate if MongoDB is installed on the same machine as the Pritunl server.

Following this, you will be able to log in using the default credentials, with both the username and password set as 'pritunl'.

Then, during the Initial Setup phase, you will be prompted to enter a Username and create a New Password.

##### Level 1

Now we can start by creating an organization via the UI 

{{< figure src="pritunl2.png" width="100%" >}}

After that we can add user and attach it the organization

{{< figure src="pritunl3.png" width="100%" >}}


Now the last finishing touches are adding a new server 

{{< figure src="pritunl4.png" width="100%" >}}


attach server to the organization 

{{< figure src="pritunl5.png" width="100%" >}}

Proceed by selecting "Start Server" to activate the VPN server. Once the server is up and running, user profiles can be obtained from the Users page. Here, you can download a profile by either clicking the download icon or the profile links option located beside each user's name. These profiles are compatible with the Pritunl client or any OpenVPN-compatible client.

And Voila with these steps completed, your VPN server is now operational.
