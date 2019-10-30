# Loadable Modules - add your own custom features to Mesibo

Imagine, if you could have the ability to process every message between your users, or could add custom features and functionalities. For example, create chatbots, filter profanity, translate messages between sender and recipient, analyze messages with machine learning and AI tools, and more. This can open up a plethora of creative possibilities for your apps.  Now with mesibo modules, all of this is possible!.

Mesibo is designed “**by Developers for Developers**!”. As developers, we understand that a platform is very limited unless it allows its users to build more features and functionalities on it. This is how Mesibo loadable modules come in. 

Mesibo loadable modules let you expand mesibo by adding your own features and functionalities. You can build powerful chatbots, filters, remotely communicate with hardware for IoT and robotics, integrate with Machine learning and Scientific computing backend such as Tensorflow, Dialogflow, Matlab, etc. and much more, keeping your data secure and private in your own premises or private cloud.

This repository contains the Sample Loadable Modules that you can use as reference.Quickly build and load Sample Mesibo modules to see Mesibo Modules in action! 

The complete documentation for Mesibo Modules is available [here](https://mesibo.com/documentation/loadable-modules/)

## List of Sample Modules 

- [Skeleton](https://github.com/mesibo/onpremise-loadable-modules/tree/master/skeleton) Bare bones version of a Mesibo Module that explains the usage of different aspects of the module, various callback functions, callable functions and utilities.

- [Filter](https://github.com/mesibo/onpremise-loadable-modules/tree/master/filter) Profinity filter module to drop messages containing profanity

- [Translate](https://github.com/mesibo/onpremise-loadable-modules/tree/master/translate) Translator module to translate each message before sending it to destination. Sample translate Module provides an example using [Google Translate](https://cloud.google.com/translate)

- [Chatbot](https://github.com/mesibo/onpremise-loadable-modules/tree/master/chatbot) Chatbot module to analyze messages using various AI and machine learning tools like Tensorflow, Dialogflow, etc. and send an automatic reply. Sample Chatbot Module provides an example using [Dialogflow](https://dialogflow.com)

- [Javascript](https://github.com/mesibo/onpremise-loadable-modules/tree/master/js) JavaScript Module to load and call functions in [ECMAScript](http://www.ecma-international.org/ecma-262/5.1/). Sample Javascript Module uses the embeddable JS Engine [Duktape](https://duktape.org)

## Compiling Modules
To compile a Mesibo module, open the sample MakeFile provided in each repo. Change the MODULE to <module name>.

```
MODULE = <module name>
```

Run make from your source directory.

```
sudo make
```
On successful build of your module, verify that the target path should contain your shared library. 
Example, `/usr/lib64/mesibo/mesibo_mod_<module name>.so`

## Loading Modules
To load a Mesibo module provide the configuration in `/etc/mesibo/mesibo.conf`. You can copy the configuration from `sample.conf` provided in each repo, into `/etc/mesibo/mesibo.conf` and modify values accordingly. 

Mount the directory `/path/to/mesibo_mod_<module name>.so` containing your module(.so file) while running the mesibo container. For example, if the module is located at `/usr/lib64/mesibo/`

```
sudo docker run  -v /certs:/certs -v  /usr/lib64/mesibo/:/usr/lib64/mesibo/ \
         -v /etc/mesibo:/etc/mesibo -net host -d mesibo/mesibo <app token> 
```
