# Why to setup a PhishDetect Node

A **PhishDetect Node** is a server running a PhishDetect service, normally the web interface that a PhishDetect Browser Extension can be configured to use. By default, the extension is configured to use a PhishDetect Node located at **node.phishdetect.io** that is operated by the cretors of PhishDetect.

However, we encourage the creation of independent Phishdetect Nodes whenever possible. There are multiple reasons why you would want to setup your own PhishDetect Node:

1. While there might be several ways for an attacker to identify a PhishDetect Node connecting to the phishing kits (for example by fingerprinting the instrumented headless Google Chrome browser), the most obvious way is by blacklisting the originating IP address. Because the default `node.phishdetect.io` is publicly accessible and is not meant to be resistant to be resistant to fingerprinting, it might be the case that careful attackers might notice it and block it. **By running your own PhishDetect Node you will be able to diversify and reduce the risk of getting blacklisted.**

2. While we do the best to protect users' privacy, **you might want to run your own PhishDetect Node to reduce exposure of potential personal or private information** (see our [Privacy Policy](/help/privacy/) for more details on what data could be collected).

3. If you work for an organization or are part of a group of people who might benefit from using PhishDetect, you might want to run your own Node in order to more directly support your peers and have some visibility over the suspicious links they might receive. Because PhishDetect is free software, you can also modify to better suit your or your organization's needs and perhaps integrate it in other existing workflows and processes.
