# ComfyUI Node Dictionary
Explore your ComfyUI installations node classes for their functionality, source code, and more. 

<p align="center"><img src="https://i.imgur.com/XTGyBXN.jpg" />
<a href="https://i.postimg.cc/vQzHqtPC/Screenshot-2023-07-14-135732.png"><img width="300" src="https://i.postimg.cc/vQzHqtPC/Screenshot-2023-07-14-135732.png"></a><a href="https://i.postimg.cc/TYVXyTFB/Screenshot-2023-07-14-135610.png"><img width="300" src="https://i.postimg.cc/TYVXyTFB/Screenshot-2023-07-14-135610.png"></a><a href="https://i.postimg.cc/rFXkFDnS/Screenshot-2023-07-14-135706.png"><img width="300" src="https://i.postimg.cc/rFXkFDnS/Screenshot-2023-07-14-135706.png"></a></p>

# Installation

The easiest way to install Node Dictionary is to install to ComfyUI Portable, then simply [downlaod and extract this archive](https://drive.google.com/file/d/1MiBKIu9jHD9rjrBgCjDCSMcCzuFrpT-Q/view?usp=sharing) to your base directory where your `run_nvidia_gpu.bat` and `run_cpu.bat` files. Then launch `run_comfy_dictionary.bat` to start the Node Dictionary server. 


## Manual installation

- Clone or downlaod a zip of the repo.
- Move `comfy_dictionary.py` to ComfyUI folder of ComfyUI installation. (Ex: `C:\ComfyUI_windows_portable\ComfyUI`)
- Create a `run_comfy_dictionary.bat` wherever you'd like and and launch it with the Python version you're executing ComfyUI with. Usually the portables `python_embedded`.
- #### run_comfy_dictionary.bat:
```batch
C:\ComfyUI_windows_portable\python_embeded\python.exe -s C:\ComfyUI_windows_portable\ComfyUI\comfy_dictionary.py

pause
```
- Run your `run_comfy_dictionary.bat` file. Your browser will open to `http://127.0.0.1:8189` During first run, a database mapping all relevant class information will be created to be loaded on subsequent runs.

### Launch Flags

 - `--no-source-code` - Don't scrape, store, or display source code from node classes.
 - `--update-classes` - Update the database for any changes to node classes.
 - `--update-plist` - Download a new version of the ComfyUI Manger plugin list.
 - `--no-plist` - Do not download or display ComfyUI Manager plugin list.
 - `--offline` - Do not use online functionality.
 - `--no-pygments` - Do not use Pygments source code highlighting.
 - `--no-browser` - Do not launch system browser when the server launches.
 - `--image_paths` - Specify extra image gallery paths like `--image_paths "C:\Users\node_dictionary\Pictures, C:\other\output\folder"`
 - `--purge-cache` - Clear the gallery thumbnail cache on startup.
 - `--no-gallery` - Disable *all* image galleries **(not implemented)**

### Requirements 
 -  [ComfyUI](https://github.com/comfyanonymous/ComfyUI)
 -  Pygments (Will install on launch if not present)

# For Developers

Node Dictionary is a endeavor with the hopes to bring documentation through node development. There are two ways to provide information to Node Dictionary to help represent your nodes. Pull Requests to improve upon, and expand the software are welcomed. This is a communtiy project. 

## `MANIFEST` dict
Information can be provided about the custom_node, or module by including a `MANIFEST` dict. 

### Example:
```python
MANIFEST = {
    "name": "ACME Nodes", # The title that will be displayed on Node Class menu,. and Node Class view
    "version": (1,2,5), # Version of the custom_node or sub module
    "author": "Bugs R. Bunny", # Author or organization of the custom_node or sub module
    "project": "https://example.com/warnerbrosdiffusion", # The address that the `name` value will link to on Node Class Views
    "description": "ACME brand nodes for ComfyUI", # The description of the custom_node or sub  module
}
```

## Node Attributes

Node-specific information can be provided via the nodes themselves with node class attributes. 

- HTML can be provided in the `DESCRIPTION` attribute to format your node documenation.
- General remote information can be linked with the `URL` attribute
- Images (such as workflows) can be provided in the `IMAGES` attribute

```python
        DESCRIPTION = "<strong>ACME Brand Nodes</strong> intends to bring the most potent custom_nodes to ComfyUI with <i>explosive</i> power!"
        URL = { 
            "Example Workflow": "https://warnerbrosdiffusion.com/workflows/acme.json",
            "Youtube Channel": "https://youtube.com/warnerbrosdiffusion/",
        }
        IMAGES = [
            "https://example.com/warnerbrosdiffusion/workflows/acme-image.png",
            "https://example.com/warnerbrosdiffusion/workflows/acme-image-2.png",
            "https://example.com/warnerbrosdiffusion/workflows/acme-image-3.png",
        ]
```
