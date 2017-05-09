﻿# PRODUCTINVENTORY-CTK-CTK
Installing and Running the Product Inventory CTK
The Product inventory CTK is dependent on the installation of node.js and Newman to work.
The installation instructions for Newman are found here: https://www.getpostman.com/docs/newman_intro
Node.js can be downloaded and installed from:
http://nodejs.org/download/ 
Once Node.js and Newman are installed download and unzip the PRODUCTINVENTORY-CTK ZIP file within your test directory.

You should see the following files:
-TMForum - TMForumProductInventoryAPITestCollectionV#.postman_collection: the postman collection for the Mandatory tests
-TMFENV : the Environment variable for the REST API Endpoint

Open the TMVENV file and change the following host value to match your endpoint. Note that by default the environment is pointing to the Sandbox endpoint. 
{
          "key": "Host",
          "value": "http://env-0693795.jelastic.servint.net:8080",
          "type": "text",
          "name": "Host",
          "enabled": true
}
now look for the ProductinventoryApi key and change it so that it matches the URL for the inventory resource:
{
          "key": "ProductinventoryApi",
          "value": "{{Host}}/DSProductinventory/api/ProductinventoryApi/v2",
          "type": "text",
          "name": "ProductinventoryApi",
          "enabled": true
}
Save the new values and exit.

Go to your test directory and type the following command:

> newman -c TMForumProductInventoryAPITestCollectionV#.postman_collection -e TMFENV -H inventoryCTKResult.html -o inventoryCTKResult.json

where inventoryCTKResult.html and inventoryCTKResult.json will contain the results of the CTK execution. You should see something like the following example:

Iteration 1 of 1
request [object Object]
request typeobject
201 651ms POST  /inventory http://env-0693795.jelastic.servint.net:8080/DSDSProductinventory/api/DSProductinventory/v2/DSProductinventory
  ✔ Content-Type is present application/json
  ✔ Status code is 201
  ✔ Response contains ID 13208
  ✔ Response contains HREF
  ✔ POST Body Response equals Request Body

201 187ms POST Productinventoryinventory copy http://env-0693795.jelastic.servint.net:8080/DSProductinventory/api/DSProductinventory/v2/DSProductinventory
  ✔ Content-Type is present application/json
  ✔ Status code is 201
  ✔ Response contains ID 13263
  ✔ Response contains HREF
  ✔ POST Body Response equals Request Body
200 62ms /current copy http://env-0693795.jelastic.servint.net:8080/DSProductinventory/subscriber/api/current
204 67ms delete hub by id copy http://env-0693795.jelastic.servint.net:8080/DSDSProductinventory/api/DSProductinventory/v2/hub/13262
  ✔ Successful DELETE request13262
Summary:
Parent                    Pass Count  FailCount
-------------------------------------------------------------
Folder inventory test         18         0
Folder hub test               8         0
Total                        26         0

If they are no failures then you have passed the CTK and your API is conformant with all
the Mandatory features.

The results of the CTK are also in  the inventoryCTKResult.html
While all the information related to the execution of the CTK will be contained in the inventoryCTKResult.json file


