## Sharing files among devices through Python through your WiFi router or not

You got a scenario where you need to share a large file or multiple large files between your two devices.

### Prerequisite:

- A computer with Python3 installed
- A common internet network between your source and destination devices

### Setup

- run the following command in your source computer from the folder where your source file is present.

``` bash
$ python -m http.server
```

- Get the IP of your source computer through *ifconfig/ipconfig* based on your OS.
- Go to your destination device and open a browser.
- Type in the `<IP>:8000` on the browser address bar


### Example

source:

``` bash
$ python -m http.server
Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
```
destination:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1610989940817/pndIWmpCf.png)

right-click on the desired file and click on `save link as` to save the file on the destination.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1610990001459/K-nMBbtlg.png)

That's it. :) 

### Bonus tip:

- You can transfer files of any size.
- You can create a zip file of an entire folder and transfer it.
- The receiver device can be any device (feature phone, tablet, etc.) it just needs to connect with the same network and should have a browser.

### Question for you

- Do you need the internet to transfer the files?

<span>Photo by <a href="https://unsplash.com/@kellysikkema?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Kelly Sikkema</a> on <a href="https://unsplash.com/s/photos/share?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>