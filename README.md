# PhishDetect Node

PhishDetect is a set of tools designed to provide additional protection to individuals at risk from phishing attacks. PhishDetect is composed of a server, generally called a **PhishDetect Node**, and a number of clients, including a [browser extension](https://github.com/phishdetect/phishdetect-extension) and other applications.

A PhishDetect node serves two purposes:

1. It offers a collection of known malicious indicators, distributed in a hashed form, that clients can check potential suspicious (e.g. an email sender, or a website visit) against.

2. It allows to dynamically scan for suspicious links as well as HTML pages for potential phishing.

This guide will provide you instructions on how to setup and configure a PhishDetect Node of your own. The first step, is to read on [why to run a PhishDetect Node](why.md).
