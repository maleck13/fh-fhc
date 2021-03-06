fhc-account -- Manage your FeedHenry Account Resources
======================================================

## SYNOPSIS

     fhc account upload-resource <destination> <file-path> <resource-type> <config>
       where <destination> is one of : android, iphone or blackberry
       where <file-path> is the absolute path of the file to upload
       where <resource> is one of : certificate (used by iphone and android), privatekey (used by iphone and android), csk or db (used by Blackberry)
       where <config> is one of : debug or distribution (required if destination is iphone, default is debug)
     or
     fhc account upload-resources-batch <destination> <resource-directory>
       where <destination> is one of : android, iphone, blackberry or all
       where <resource-directory> should be the directory where resources are located.
     or 
     fhc account generate-resource <destination> <resource-type> <password>
       where <destination> is one of android or iphone (not supported yet)
       where <resource-type> is one of certificate or csr (certificate signing request, not supported yet)
       where <password> is the password used to encrypt the private key (required)    
  
## DESCRIPTION

This command will try to find the correct type of resources for each destination and upload them automatically. 
To do that, you should organize your resources in the following way: 
 1. If the destination is all, each resource file should have one parent directory indicates its actual destination.
 2. Each resource file should be better use the resource type as its extention or at least part of the name.
 3. Each resource file should have one parent directory inticating its destination.
 4. For ios resources, each of them should have one parent directory indicating its config.
 5. If more than one resource file is found for one set of configuration, no file will be uploaded for that configuration.

  Example:
  --Resources
   |--iphone
     |--debug
       |--developer.certificate
       |--developer.privatekey
   |--android
     |--developer.certificate
     |--developer.privatekey
   |--blackberry
     |--sigtool.csk
     |--sigtool.db

