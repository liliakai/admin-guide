# PhishDetect Node

PhishDetect is a set of tools designed to provide additional protection to individuals at risk from phishing attacks. PhishDetect is composed of a server, generally called a **PhishDetect Node**, and a number of clients, including a [browser extension](https://github.com/phishdetect/phishdetect-extension) and other applications. For details on how to use PhishDetect (as a user, rather than as an administrator) please refer to the official [Help](https://phishdetect.io/help/) page.

A PhishDetect Node serves two main purposes.

#### Collection of known malicious indicators

It exposes a **REST API** interface that offers a **collection of known malicious indicators**, distributed in a hashed form, that clients can check potential suspicious elements against. For exampe, the [PhishDetect Browser Extension](https://github.com/phishdetect/phishdetect-extension) regularly contacts this REST API to fetch hashed malicious domain names and blocks visits to a site matching any of those domain names. Additionally, it integrates with Gmail web interface and it checks the sender of any opened email, against the list of hashed malicious email addresses also offered by the REST API of the configured PhishDetect Node.

#### Analyze suspicious unknown links and pages

It exposes a **Web GUI** that allows to **dynamically check a suspicious URL or HTML of a page** to identify elements indicative of a potential phishing page. For example, through buttons and context menu items added by the PhishDetect Browser Extension, a user can request the configured PhishDetect Node to check a suspicious link that was sent to them before actually visiting it.

---

Essentially, a PhishDetect Node is the core component in the ecosystem of PhishDetect tools. This guide will provide you instructions on how to setup and configure a PhishDetect Node of your own. The first step, is to read on [what are the reasons to setup and run one](why.md).
