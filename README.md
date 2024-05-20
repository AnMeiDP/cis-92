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
| `DATA_DIR` | /data | Directory where database will be stored |
| `DEBUG` | 1 | Setting debugging on |

The ENV variables of **secret.yaml** are...
| Name | Default Value | Description |
| --- | --- | --- | 
| `SECRET_KEY` | sshhhthisisthesecret | Helps ensure security within application | 

**How to apply deploy application on cluster**
```kubectl apply -f pod/POD_NAME ```
```kubectl apply -f service/SERVICE_NAME ```

**How to delete (turn down) application on cluster**
```kubectl delete service/SERVICE_NAME ```

