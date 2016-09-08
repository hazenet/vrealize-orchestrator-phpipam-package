# vRealize Orchestrator package for interaction with phpIPAM

Package Version: 0.0.1  
Developed on vRealize Orchestrator 7.0.1  
Against phpIPAM v1.25 rev002  

Developed by Mads Fog Albrechtslund  
Website: https://hazenet.dk  
Twitter: @Hazenet  

## Information

This package is developed in a similar way as the default VMware package included with vRealize Orchestrator.  
That means you are free to view, duplicate and export the workflows, but you are not able to edit the workflows directly.

The reason for this, is so I can maintain workflow ID's for future revisions of the package.  

Because of this, it is not directly possible to delete this package again, just like the default VMware packages.  
But it can be manualy delete, by enabling the follow setting in the vRO Workflow Designer client.  

Tools -> User Preferences... -> General -> Delete non empty folder permitted

When that setting is enabled, it is possible to delete non-editable workflows, complete folders with workflows and folders inside.  
This setting allows the delete of both these phpIPAM related workflows and VMware default workflows.  
SO BE VERY CAREFUL WHEN USING THIS SETTING  
AND DISABLE IT IMMEDIATELY AFTER  

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





