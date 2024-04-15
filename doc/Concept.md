# AsciiArtify Kubernetes Deployment Tools

## Introduction
AsciiArtify is a startup dedicated to creating a new software product that uses Machine Learning to transform images into ASCII art. Founded by two young entrepreneurs who are experienced software developers but lack DevOps expertise, the team faced challenges in selecting a technical solution for developing a local Kubernetes cluster. They evaluated three tools: minikube, kind, and k3d.

## Characteristics
### Minikube
- `Supported OS:` Compatible with multiple operating systems: Linux, Windows, and MacOS.
- `Supported Architectures:` Works on various architectures.  
- `Automation Capability:` Provides automated solution for cluster creation and management.
- `Additional Features:` Well-suited for local development and testing, though scalability limitations may be a concern.

### Kind (Kubernetes IN Docker)
- `Supported OS and Architectures:` Compatible with Linux, Windows, and MacOS.
- `Supported Architectures:` Utilizes Docker containers.
- `Automation Capability:` Sets up Kubernetes clusters within Docker containers.
- `Additional Features:` Recommended for local testing use.

### k3d
- `Supported OS and Architectures:` Works on multiple operating systems.
- `Supported Architectures:` Implements Rancher Kubernetes Engine (RKE) in Docker containers.
- `Automation Capability:` Enables quick creation and testing of Kubernetes clusters within Docker containers.
- `Additional Features:` Selected for PoC (Proof of Concept) preparation.

### Comparison

| **Pros and Cons**                               | **Minikube**                                     | **Kind**                                         | **k3d**                                          | **Podman**                                       |
|--------------------------------------------------|--------------------------------------------------|--------------------------------------------------|--------------------------------------------------|--------------------------------------------------|
| **Pros**                                      | + Easy-to-use tool<br>+ Ideal for local development and testing | + Suitable for local development and testing<br>+ Works within Docker containers<br> | + Suitable for local development and testing<br>+ Works within Docker containers<br>+ Quick creation and testing of clusters | + Easy-to-use tool<br>+ Suitable for local development and testing<br>+ Works within Docker containers<br>+ Light-weighted alternative to Docker |
| **Cons**                                      | - Scalability uncertainty<br>- Potential limitations | - Limited information on scalability<br>- Limited community documentation | - Limited documentation<br>- Potential scalability issues | - Limited information on scalability<br>- Limited community documentation |


## Demonstration

### k3d

![k3d](./k3d.gif)


## Conclusion

After practical exploration, k3d stands out as the recommended tool for AsciiArtify's PoC due to its quick cluster setup and user-friendly interface, making it ideal for initial development. However, it's crucial to consider the limited community documentation and potential scalability concerns. Additionally, considering potential licensing concerns with Docker, it's advisable for AsciiArtify to explore using Podman instead. AsciiArtify should carefully weigh the pros and cons before making a final decision.