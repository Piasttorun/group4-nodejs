

First, we created our Azure Virtual Network which we made sure was located in the UK South region and we gave the address space of 10.0.0.0/16.
As the NodeJS app has both an app and database we created two subnets, one for each vm.
The app vm has an address space of 10.0.2.0/16. and the database vm has an address space of 10.0.3.0/16.

We then moved onto creating out virtual machines. We created the database virtual machine first, so that it would be ready to use once we started to create and test the app vm.

We made sure the database vm was located in the UK south region, used the Ubuntu 18.04 LTS image and was a size equivalent to the t2.micro in AWS. We chose the Standard B1s size as it seemed to be the most similar. We then allowed port 20 for SSH and port 27017 which is the default port for MongoDB.

Once we SSH’d in we upgraded and updated and then installed MongoDB version 3.2.x as requested. We then configured MongoDB to allow access from any IP address so we could test the database. We then restarted, started and enabled MongoDB.

We then moved onto creating the app VM. The location, image and size remained the same as the database VM but we also allowed port 3000 for database access and port 80 for HTTP.

We then used manual commands to update and upgrade, install and start Nginx, install node JS version 12, change the DB_Host environment variable to include the ip address of the database virtual machine within the correct MongoDB endpoint. We then cloned and cd’d into our github repo, installed npm, seeded the database and ran the app.

We then tested our app by going to port 3000 to make sure we could view the sparta app page and then the ‘/posts’ endpoint to make sure we could view the data from our database.

We then created scripts from the manual commands we had used, and created fresh VM’s to test them. Once we knew the scripts worked, we then created new VM’s that used them as user data.
![Uploading image.png…]()
