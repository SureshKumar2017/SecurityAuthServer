# SecurityAuthServer

Execute the data.sql
============================================
URLS:
1. Register the username & password in Auth Server using the below POST call.

http://localhost:8082/oauth/users
Request Body:

{
  "userName": "suresh",
  "password": "suresh@123",
  "email": "suresh.kumar@gmail.com",
  "mobile": "9840556777"
}

Date will inserted in auth_user table.

2. Get JWT access token (POST call)

http://localhost:8082/oauth/token
params:
grant_type- password 
username- suresh 
password- suresh@123 

Authorization:
Basic Auth
 Username : test
 Password : temp
 
Response:
{
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NzEzNjA4MTAsInVzZXJfbmFtZSI6InN1cmVzaCIsImp0aSI6ImZiMjk4NWNhLWQ4OGUtNDFmZS1hM2UyLThiMjI1NjMzMzllYiIsImNsaWVudF9pZCI6InRlc3QiLCJzY29wZSI6WyJyZWFkIiwid3JpdGUiXX0.9DwQcAMPraJOsEJz9TyF9uSs9AqKTlqmIUFHxxGsbtE",
    "token_type": "bearer",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NzEzNjIzMTAsInVzZXJfbmFtZSI6InN1cmVzaCIsImp0aSI6ImJkNWJiNjZjLTg4MTctNDhjNi1iNGM3LWE0MzllYWRiOWYyZCIsImNsaWVudF9pZCI6InRlc3QiLCJzY29wZSI6WyJyZWFkIiwid3JpdGUiXSwiYXRpIjoiZmIyOTg1Y2EtZDg4ZS00MWZlLWEzZTItOGIyMjU2MzMzOWViIn0.dHHNLCUHEfxvqz7pbBq1BSmmL_3vCKJfK-L8oFmRIdA",
    "expires_in": 299,
    "scope": "read write",
    "jti": "fb2985ca-d88e-41fe-a3e2-8b22563339eb"
}

3. Verify access token POST call

http://localhost:8082/oauth/check_token
param:
token -     eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NzEzNjA4MTAsInVzZXJfbmFtZSI6InN1cmVzaCIsImp0aSI6ImZiMjk4NWNhLWQ4OGUtNDFmZS1hM2UyLThiMjI1NjMzMzllYiIsImNsaWVudF9pZCI6InRlc3QiLCJzY29wZSI6WyJyZWFkIiwid3JpdGUiXX0.9DwQcAMPraJOsEJz9TyF9uSs9AqKTlqmIUFHxxGsbtE
Authorization:
Basic Auth
 Username : test
 Password : temp
 
Response:
{
    "active": true,
    "exp": 1671360810,
    "user_name": "suresh",
    "jti": "fb2985ca-d88e-41fe-a3e2-8b22563339eb",
    "client_id": "test",
    "scope": [
        "read",
        "write"
    ]
}

4. Get refresh token POST call

http://localhost:8082/oauth/token

param:
grant_type - refresh_token
refresh_token-      eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE2NzEyOTY3NjIsInVzZXJfbmFtZSI6ImhhcmkiLCJqdGkiOiIxOTc2ZDk3Yy1lMWVhLTRhMmItYTgyOC03ZjIwMTMxYmVhZGYiLCJjbGllbnRfaWQiOiJ0ZXN0Iiwic2NvcGUiOlsicmVhZCIsIndyaXRlIl0sImF0aSI6IjljYTljMDY1LWQ4ZDAtNDZlOC1iODQzLTVhMjVmYjAwYzJmZiJ9.ItRUS6U9zdPB5v-c2LqoNI3QaTCM3NDLb4R01yiojnM
Authorization:
Basic Auth
 Username : test
 Password : temp

========================================
To verify the JWT token information using below link
https://jwt.io/
