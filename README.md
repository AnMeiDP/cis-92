# My CIS-92 Project 
This repository has the starter code for CIS-92. From Mike Matera.

By: AnMei Dasbach-Prisk

## Configuration
The ENV variables of **config.yaml** are...
| Name | Default Value | Description |
| --- | --- | --- | 
| `PORT` | 8000 | Port that application listens on | 
| `STUDENT_NAME` | AnMei STU | Placeholder for author name |
| `SITE_NAME` | * | Placeholder for application name |
| `DEBUG` | 1 | Setting debugging on |
| `POSTGRES_DB` | mysite | Postgres database name |
| `POSTGRES_HOSTNAME` | postgres-postgresql | Network address of database server |

The ENV variables of **secret.yaml** are...
| Name | Default Value | Description |
| --- | --- | --- | 
| `SECRET_KEY` | sshhhthisisthesecret | Helps ensure security within application | 
| `POSTGRES_PASSWORD` | this-is-a-bad-password | Database password | 
| `POSTGRES_USER` | mysiteuser | Postgres username | 

The parameters of **values-postgres.yaml** are...
| Name | Default Value | Description |
| --- | --- | --- | 
| `auth.username` | mysiteuser | Name for custom user to create |
| `auth.password` | this-is-a-bad-password | Password for custom user to create |
| `auth.database` | mysite | Database name |
| `auth.postgresPassword` | another-really-bad-password | Password for postgres admin user |

It is important that you change these default values, because if you don't it can potentially leave your database vulnerable

Database resource requests in **values-postgres.yaml**
| Resource | Default Value | Description |
| --- | --- | --- | 
| `memory` | 512Mi | Min. memory | 
| `cpu` | 500m | Min. CPU | 
| `ephemeral-storage` | 100Mi | Min. storage | 

**How to deploy application on cluster**  
Launch services   
```kubectl apply -f pod/POD_NAME ```  
```kubectl apply -f service/SERVICE_NAME ```  
Launch external database via HELM  
```helm install postgres oci://registry-1.docker.io/bitnamicharts/postgresql --values values-postgres.yaml```  
Install postgres client  
```sudo apt install postgresql-client```  
Connect to postgres via port forwarding (since database is connected to cloud)  
```kubectl port-forward service/postgres-postgresql 5432:5432```  
In a second terminal access database via shell  
```psql -h localhost -U mysiteuser mysite ```  
Once in shell now you can  ```create table``` and ```insert``` data


**How to delete (turn down) application on cluster**  
Clean up database  
```helm uninstall postgres```   
```kubectl delete pvc/data-postgres-postgresql-0```  
Turn of other app services (save that coin!)  
```kubectl delete service/SERVICE_NAME ```

