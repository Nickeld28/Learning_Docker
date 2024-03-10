## Images and structure

### What is a Docker image?

**Docker image** is an immutable template from which you can create containers.

### What is the difference between an image and a container?

Containers have running processes that run and perform tasks, and images are a set of files and instructions needed to run containers. Images are static, while containers are dynamic. Containers are deployed from images.

### Structure of images

Images consist of layers (File Sytem Layers), and each layer is a set of files.

Each image has a base layer and other layers that are added to the base layer.

### Reusing layers in images

The layer system is used so that the same layers can be reused in different images.

During the process of creating containers, the necessary files are assembled according to the layers specified in the image.

Reusing layers is also used when creating custom images.

### What else you need to know about images

All layers in the image are read-only. You cannot make adjustments to the finished image, but you can create new images with the necessary changes.

Images can be easily copied, moved and deleted like regular files.

Images are stored in repositories.

Images may have different versions, which will have differences in some layers.

There are official images that can be downloaded from DockerHub, and there are images created by the community. Developers can share their images.

#### [<<< Back](/Summary.md)
