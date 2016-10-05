# vRealize Orchestrator package for interaction with phpIPAM

Package Version: 0.0.3
Developed on vRealize Orchestrator 7.0.1
Against phpIPAM v1.26 rev030 (Commit 6aff3873fa496d0611c47d574aead5b650516698) 

Developed by Mads Fog Albrechtslund  
Website: [https://hazenet.dk](https://hazenet.dk)  
Twitter: [@Hazenet](https://twitter.com/Hazenet)  

## Download

The package can be downloaded from the [Repository Releases page](https://github.com/hazenet/vrealize-orchestrator-phpipam-package/releases)  

## Information

This package is developed in a similar way as the default VMware packages included with vRealize Orchestrator.  
That means you are free to view, duplicate and export the workflows, but you are not able to edit the workflows directly.

The reason for this, is so I can maintain workflow ID's for future revisions of the package.  

Because of this, it is not directly possible to delete this package again, just like the default VMware packages.  
But it can be manualy delete, by enabling the follow setting in the vRO Workflow Designer client.  

Tools -> User Preferences... -> General -> Delete non empty folder permitted

When that setting is enabled, it is possible to delete non-editable workflows, complete folders with workflows and folders inside.  
This setting allows the delete of both these phpIPAM related workflows and VMware default workflows.  

**SO BE VERY CAREFUL WHEN USING THIS SETTING**  
**AND DISABLE IT IMMEDIATELY AFTER**  

## Installed content

The package installs:  

Workflows -> Library -> phpIPAM  
Actions -> net.phpipam  
Configurations -> phpIPAM  
Packages -> net.phpipam  

## Usage

**Step 1 - Create phpIPAM App ID**  
In phpIPAM web-interface, go to Administration -> API  
  
Click "Create API key"

* Choose a "appid", which is a short unique identifier that will be part of the API URL, e.g. "vro" or "myapp"
* Leave the generate "App code"
* Select Permissions, recommed "Read / Write / Admin" for full functionality
* App Security, I have only tested it with "none"

**Step 2 - Add phpIPAM Rest Host**  
Run the following workflow in vRO Workflow Designer  

Workflows -> Library -> phpIPAM -> Configuration -> phpIPAM - Add REST Host  

Configure it with a "Configuration Type" of "Basic" and a "Shared Session" for "Authentication"  

**Step 3 - Use the provided workflows**  
All workflows have a INPUT of "phpIPAM Token", this is a optional INPUT.  
If nothing is provided, the workflow it retrive a phpIPAM Token automatically.  

For longer sequences of phpIPAM related workflows, consider  getting a phpIPAM Token as the first step in the sequence, to lessen the load on the phpIPAM Server.  

**Step 4 - Enable/Disable logging of the REST Responses**  
Included in the package is a Action called "loggingOfResponse".  
This Action is used in the workflow "phpIPAM - Execute REST Request".  
To decide whether or not to enable this logging feature, use the Configuration Element "phpIPAM Logging", which has a Attribute called "loggingOfResponse".  


