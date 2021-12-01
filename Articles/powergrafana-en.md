---
title: PowerGrafana, what is it and how to use it.
description: A tool to programatically manage grafana
tags: 'Powershell, Grafana, Monitoring, Automation'
published: true
---

## PowerGrafana, what is it and what is it used for?  

<!-- <img src="https://raw.githubusercontent.com/javiermarasco/blog/master/images/grafana_logo.png" width="100px" height="100px"> -->


### Lets beggin with a bit of context and how it all started  

Sometimes it happens that we have to monitor some application, service or component (among other things) and the tool that we use or our company uses is [Grafana](https://grafana.com), while we have few things to monitor it is not much of a problem but as we add more elements to the panels it becomes more complex to maintain and / or configure.

Imagine that you have to deploy 20 applications, each one running in an [app service](https://azure.microsoft.com/en-us/services/app-service) so we would surely want to monitor your CPU and Memory usage (to begin with) and surely a few more things.
In this simplistic scenario we have to configure some panels in a dashboard and in each panel put the metrics that we want to show (CPU and Memory) in our case.

This sounds simple but in a short time we will surely need to add another metric or deploy a new version of our application, even worse, we could deploy a new version of some components and not others while we have to keep all the versions (the initial one plus the new one) of each component, as you can see this becomes more and more complex to show in Grafana, it is a lot of time clicking on the interface or (the alternative) editing json files to paste them in the Grafana web interface and generate the dashboards or panels ( believe me that it is very easy to make mistakes when editing those files).

### The alternative

PowerGrafana was created to solve this problem (or try to make it easier to handle) by extracting all the complexity of dealing with the web interface, json files, or even entering the names of the resources to monitor by hand.
Using a simple PowerShell module we can quickly iterate through our resources and for each of them create a panel that shows CPU and Memory usage.

Each command has it's own help, which can be accessed by executing:  

```powershell
PS> Get-Help New-GrafanaDashboard 

NAME
    New-GrafanaDashboard
    
SYNOPSIS
    Creates a dashboard in Grafana
    
    
SYNTAX
    New-GrafanaDashboard [-DashboardName] <Object> [[-Tags] <String[]>] [<CommonParameters>]
    
    
DESCRIPTION
    This cmdlet will create an empty dashboard in Grafana that can be used as starting point to create your grafana monitoring.
    
EXAMPLE
    New-GrafanaDashboard -DashboardName "My new dashboard" -Tags @('Web','Azure','Production')

RELATED LINKS

REMARKS
    To see the examples, type: "Get-Help New-GrafanaDashboard -Examples"
    For more information, type: "Get-Help New-GrafanaDashboard -Detailed"
    For technical information, type: "Get-Help New-GrafanaDashboard -Full"
    For online help, type: "Get-Help New-GrafanaDashboard -Online"
```


## Links

- [Link to PowerGrafana at GitHub](https://github.com/javiermarasco/PowerGrafana)  
- [Link to PowerGrafana at the PowerShell gallery](https://www.powershellgallery.com/packages/PowerGrafana/0.1.0)

