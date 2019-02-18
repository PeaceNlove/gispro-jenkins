# gispro-jenkins
Manual and scripts for publishing ArcGIS Pro project to ArcGIS Enterprise using Jenkins Build Server

## Introduction ##
ArcGIS Enterprise is often part of a large IT ecosystem. A DTAP is used for databases, applications and when GIS is part of it, also ArcGIS Enterprise or standalone ArcGIS Server. Manually administering the services in ArcGIS Enterprise this Developement, Test, Acceptance and Production street is time consuming and prone to errors. Furtermore, it is not integrated with the continuous deployment which is used for the GIS application consuming the services.
Integrating publishing the mapservices into the continuous deployment therefore has the following advantages:
* Better quality, because mapservices will be published exactly the same from the configuration
* Better performance, because it is very easy to perform an automated performance test every time you deploy a mapservice, making it easy to detect performance problems caused by a change in one of the layers
* Faster publishing, let the build server publish 4 mapservices in parallel, while you're working on something else
* Keep track of changes in the mapservices using Source Control Management (GIT or SVN)

## Components overview ##
* Arcgis Pro 2.2 or higher
* Git Client
* Jenkins
* Jmeter (optional)

## Preparation ##
For this setup, you need a Windows Server, 2012R2 works good. On this server, a Service Account is needed. 

## Installation ##

### Arcgis Pro ###
To publish mapservices, Arpcy is needed and therefore an Arcgis Pro installed on the server is needed. Obtain the installation files from Esri. Arcgis Pro 2.2 and 2.3 have been tested.  
Install Arcgis Pro with the default options.

### Jenkins ### 
'The leading open source automation server, Jenkins provides hundreds of plugins to support building, deploying and automating any project.' This is true and it's free, so download the Windows installer here: https://jenkins.io/download/thank-you-downloading-windows-installer-stable/   
Install Jenkins,    
Go to Windows Services and configure the Jenkins service to run under the Service Account.  
Run the powershell script TODO. This powershell script configures Jenkins Service to interact with the desktop. This setting is only available in the services menu when the service runs under Local System Account, but this account has insufficient privileges. 'interact with the desktop' is required to get font symbology working with custom fonts. If custom fonts are used for point symbols and this 'interact with the desktop' setting is not set, the custom fonts will be replaced with default fonts and the symbology will be ugly.  

Script was taken from here: https://lostechies.com/keithdahlby/2011/08/13/allowing-a-windows-service-to-interact-with-desktop-without-localsystem/

## GIT ## 
Remarks on installing GIT

## Licensing ##
Arcgis Pro has different licensing options
* Named user: when you license Arcgis Pro with a named user account, you need to login as the Service User to configure this. The license connection will get lost sometimes for unknown reasons and Jenkins cannot publish the service in this situation. Don't try to fix this by taking you license offline, because you might experience an error when Arcgis Pro tries to start and you need to ask Esri support to reset your license!
* License Server: If your organization is entitled to floating users licenses for Arcmap, you can convert Pro named user licenses to licenses which you then can configure in your license manager. This works very good with publishing automation.
* Single license: If your organization is entitled to single licenses for Arcmap, you can convert Pro named user licenses to licenses which you then can configure in Arcgis Pro. This works very good with publishing automation.

## Scripts ##
Stuff on scripts