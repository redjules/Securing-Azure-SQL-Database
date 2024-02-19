# Securing Azure SQL Database

In this project, we are going to focus on five objectives:

- create a basic application environment consisting of a virtual network, Linux VM, and SQL Database

- limit network access to your Azure SQL Database by utilizing server-level firewall IP rules and virtual network access

- create database users and roles to easily manage permissions in your database

- enable Auditing and Temporal Tables to monitor executed queries and changes to your data

- configure a backup policy for your Azure SQL Database

We will do the following tasks:

Task 1: Setting up your environment

we create a VM and subnet:

![Screenshot 2024-02-19 at 14 55 04](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/ac0f844c-4abd-4c5b-bdd8-6602c90345e2)

![Screenshot 2024-02-19 at 14 55 32](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/4fbbe987-91d8-4819-8c2f-d4f79095bfee)

![Screenshot 2024-02-19 at 14 56 52](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/ac4262bf-a297-4831-b71c-0b55eb3a9c69)


we create a SQL database instance:

![Screenshot 2024-02-19 at 14 57 27](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/25179ef6-ef7d-4bee-ae7d-869ed38d08f6)

![Screenshot 2024-02-19 at 14 58 09](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/7dd5e3a5-1441-4d08-931f-0961fbaa6f5e)


Task 2: Limiting network access to your database

go to the SQL database resource, copy the server name:

![Screenshot 2024-02-19 at 15 40 17](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/997d7e80-85b0-4eb0-8fa8-4f52705284a4)

and open SQL Server Management Studio:

![Screenshot 2024-02-19 at 15 42 42](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/ca4281ef-97a9-4126-96b2-27dc3969b060)

go to Firewall settings in Azure and click on ClientIP address:

![Screenshot 2024-02-19 at 15 49 22](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/d2b830cb-ec5f-4228-a4d1-1a99217b438f)

click connect SSH on the VM:

![Screenshot 2024-02-19 at 15 51 05](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/091309bc-5c3e-4e67-8c55-234851ec6fc1)

put the private key:

![Screenshot 2024-02-19 at 15 51 46](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/b7ecda4f-a8f8-4b80-b584-a3de07816d47)

go to shell:

![Screenshot 2024-02-19 at 15 52 13](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/56b3ab0e-2735-492a-88aa-483503b4bf38)

upload the private key. Write step 2 and run step 4:

![Screenshot 2024-02-19 at 15 53 35](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/16d44510-7c5a-4f66-a4ec-8fe002f86c20)

Now you are connected to a VM

Copy the instructions on install tools file (task 2) and paste it in the shell:

![Screenshot 2024-02-19 at 15 54 29](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/e1c43eac-b1e3-46e7-9276-33fca65543b5)

write the following commands:

![Screenshot 2024-02-19 at 15 55 18](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/0e9ed8ab-7eef-4fa9-8d65-bad230be2b06)

put No in section "Allow Azure services to access this server":

![Screenshot 2024-02-19 at 15 56 16](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/9841eb27-c21c-403d-9f5f-fd8685d53f1d)

Add an existing VM:

![Screenshot 2024-02-19 at 15 57 22](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/8b38159d-1dbf-4f9a-a4af-d3959b7ae161)

Create a private endpoint on Private Link Center:

![Screenshot 2024-02-19 at 15 58 33](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/cdc2fac2-a8a2-416d-8e41-d1c5f47141e1)

repeat on shell nslookup command:

![Screenshot 2024-02-19 at 15 59 21](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/0899bd32-4e50-4fcf-b7ab-b015c0536e63)

Task 3: Creating a dedicated database user for your application

Set admin in Active Directory admin and go to SQL Server Management Studio:

![Screenshot 2024-02-19 at 16 02 06](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/0ff35c17-3f4f-4daf-85ec-a68639def77c)

![Screenshot 2024-02-19 at 16 04 17](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/67fe3943-c30c-4d80-a370-f75ff7da6531)

Task 4: Azure SQL Database Auditing and Temporal Tables

Go to SQL Server and Auditing and click On and Storage:

![Screenshot 2024-02-19 at 16 07 23](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/9edae5ad-b1eb-48a6-868c-676bbc405bf4)

Go to SQL Server Management Studio and write the commands:

![Screenshot 2024-02-19 at 16 08 14](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/5eb216b0-7833-4461-b39e-fc74461588a5)

![Screenshot 2024-02-19 at 16 09 02](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/caee841a-0aa3-45fb-b63d-c2ad4fe6e790)


![Screenshot 2024-02-19 at 16 09 56](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/773488f9-d040-43d3-9301-74c4e1e78a54)

View Audit Logs in Azure:

![Screenshot 2024-02-19 at 16 10 29](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/9b4db12d-1e89-4934-8ef0-9091c2319d16)

![Screenshot 2024-02-19 at 16 11 16](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/ff8c3d6d-0b38-44ce-82a6-72178a326a58)

Task 5: Defining a backup policy for you Azure SQL Database

go to Backup and retention policies:

![Screenshot 2024-02-19 at 16 12 31](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/2f8f178f-e792-4bd8-ba4b-9330c638e8fc)

Define the backup policy and apply:

![Screenshot 2024-02-19 at 16 13 31](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/62078fb3-ffd3-4675-9487-3c224300f639)

Go to restore database:

![Screenshot 2024-02-19 at 16 14 10](https://github.com/redjules/Securing-Azure-SQL-Database/assets/106017493/435b8980-923e-42af-9ef4-30591edf43d8)



