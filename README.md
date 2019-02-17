# gispro-jenkins
Manual and scripts for publishing ArcGIS Pro project to ArcGIS Enterprise using Jenkins Build Server

##Introduction##
ArcGIS Enterprise is often part of a large IT ecosystem. A DTAP is used for databases, applications and when GIS is part of it, also ArcGIS Enterprise or standalone ArcGIS Server. Manually administering the services in ArcGIS Enterprise this Developement, Test, Acceptance and Production street is time consuming and prone to errors. Furtermore, it is not integrated with the continuous deployment which is used for the GIS application consuming the services.
Integrating publishing the mapservices into the continuous deployment therefore has the following advantages:
* Better quality, because mapservices will be published exactly the same from the configuration
* Better performance, because it is very easy to perform an automated performance test every time you deploy a mapservice, making it easy to detect performance problems caused by a change in one of the layers
* Faster publishing, let the build server publish 4 mapservices in parallel, while you're working on something else
* Keep track of changes in the mapservices using Source Control Management (GIT or SVN)
