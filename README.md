# Autenticación
Login
<code>POST /login</code>

### Campos de solicitud

| Path        | Tipo        | Descripción   |
| :---        |    :----   |          :--- |
| username    | String      | El nombre de usuario de inicio de sesión   |
| password    | String      | La contraseña de inicio de sesión (Requiere mínimo 8 caracteres, que tienen que contener mayúsculas, símbolos y números )      |

### HTTP Request

```JSON
POST /login HTTP/1.1
Host: accesspoint-tacobell.up.railway.app/api
Content-Length: 65
Content-Type: application/json

{
  "password" : "mi-contraseña",
  "username" : "mi-usuario"
}
```
### cURL Request
```PHP
$ curl 'accesspoint-tacobell.up.railway.app/api/login' -i -X POST \
    -H 'Content-Type: application/json' \
    -d '{
  "password" : "mi-contraseña",
  "username" : "mi-usuario"
}'
```

### Campos de respuesta

| Path          | Tipo        | Descripción   |
| :---          |    :----   |          :--- |
| access_token  | String      | El token de acceso con formato JWT      |
| token_type    | String      | El tipo de token, actualmente solo admite "Bearer" |
| expires_in    | Number      | La vida útil en segundos del token de acceso    |

### Respuesta de inicio de sesión exitosa
```JSON
HTTP/1.1 200 OK
Pragma: no-cache
X-XSS-Protection: 1; mode=block
Expires: 0
X-Content-Type-Options: nosniff
Content-Length: 2033
Content-Type: application/json;charset=UTF-8
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
Cache-Control: no-cache, no-store, max-age=0, must-revalidate

{
  "access_token" : "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkBjdXN0MDAxLmNvbSIsInVzZXJfaWQiOjEsInJvbGUiOiJBZG1pbmlzdHJhdG9yIiwib3duZXJfaWQiOjEwMiwiZGF0YV9jZW50ZXIiOiJVU19XRVNUIiwic2NvcGVzIjpbImxvZ291dCIsImF1dGgiLCJhdXRoOnIiLCJ0b2tlbjpuZXciLCJwZXJtOmNoZWNrIiwibHJvIiwibHJvOnIiLCJhY2NvdW50IiwiYWNjb3VudDpyIiwidmlxOmJhY2t1cCIsInVzZXIiLCJ1c2VyOnIiLCJoaXEiLCJoaXE6ciIsIm9yZyIsIm9yZzpuZXciLCJvcmc6ZGVsIiwib3JnOnJlbmFtZSIsImhpcS5jdHgiLCJoaXEuY3R4OnIiLCJoaXEuY3R4OnciLCJkZXZpY2UiLCJkZXZpY2U6ciIsImRldmljZTpsaXN0IiwiZGV2aWNlOnZpZXciLCJkZXZpY2U6bmV3IiwiZGV2aWNlOmRlbCIsImRldmljZTpjbGkiLCJkZXZpY2U6ZGVwbG95IiwiZGV2aWNlOm1hbmFnZSIsImRldmljZTp1bm1hbmFnZSIsImRldmljZTpyZWJvb3QiLCJkZXZpY2U6cmVzZXQiLCJjbGllbnQiLCJjbGllbnQ6ciIsImxvY2F0aW9ucyIsImxvY2F0aW9uczpyIiwibmV0d29yay1wb2xpY3kiLCJwb2xpY3k6c3NpZCIsIm5ldHdvcmstcG9saWN5OnIiLCJzc2lkIiwic3NpZDpyIiwicGNnOmtleSIsInBjZzprZXk6ciIsInN1YnNjcmlwdGlvbnMtd2ViaG9vayIsInN1YnNjcmlwdGlvbnMtd2ViaG9vazpyIiwiY2NnIiwiY2NnOnIiLCJsb2ciLCJsb2c6ciIsImN3cCIsImN3cDpyIiwic21zLXRtcGwiLCJzbXMtdG1wbDpyIiwiY2xhc3MtcnVsZSIsImNsYXNzLXJ1bGU6ciIsInVzZXItcHJvZmlsZSIsInVzZXItcHJvZmlsZTpyIiwicmFkaXVzLXByb3h5IiwicmFkaXVzLXByb3h5OnIiLCJyYWRpdXMtc2VydmVyIiwicmFkaXVzLXNlcnZlcjpyIiwidXNlcmdyb3VwIiwidXNlcmdyb3VwOnIiLCJkZXBsb3ltZW50IiwiZGVwbG95bWVudDpyIiwiYWQtc2VydmVyIiwiYWQtc2VydmVyOnIiLCJhbGVydCIsImFsZXJ0OnIiLCJhcHAiLCJhcHBsaWNhdGlvbjpyIiwibDMtYWRkcmVzcy1wcm9maWxlIiwibDMtYWRkcmVzcy1wcm9maWxlOnIiLCJ2bGFuLXByb2ZpbGUiLCJ2bGFuLXByb2ZpbGU6ciIsImVuZHVzZXIiLCJlbmR1c2VyOnIiLCJyYWRpdXMtY2xpZW50LW9iamVjdCIsInJhZGl1cy1jbGllbnQtb2JqZWN0OnIiLCJsZGFwLXNlcnZlciIsImxkYXAtc2VydmVyOnIiLCJlbWFpbC10ZW1wbGF0ZSIsImVtYWlsLXRlbXBsYXRlOnIiLCJjZXJ0aWZpY2F0ZSIsImNlcnRpZmljYXRlOnIiLCJyYWRpby1wcm9maWxlIiwicmFkaW8tcHJvZmlsZTpyIl0sImN1c3RvbWVyX2lkIjoxLCJjdXN0b21lcl9tb2RlIjowLCJoaXFfZW5hYmxlZCI6dHJ1ZSwib3JnX2lkIjowLCJxdW90YSI6Ijc1MDA7dz0zNjAwIiwic2hhcmQiOiJVUyIsImlzcyI6ImFwaS5leHRyZW1lY2xvdWRpcS5jb20iLCJpYXQiOjE2NzcwMzUwOTUsImV4cCI6MTY3NzYzOTg5NX0.EQIPqYfKHZt-XWAk4o0Pdk-ArRhAXEvEVwWJnpDkm7Q",
  "token_type" : "Bearer",
  "expires_in" : 604800
}
```

### Respuesta de inicio de sesión fallida

```JSON
HTTP/1.1 401 Unauthorized
Pragma: no-cache
X-XSS-Protection: 1; mode=block
Expires: 0
Content-Length: 92
X-Content-Type-Options: nosniff
Content-Type: application/json
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
Cache-Control: no-cache, no-store, max-age=0, must-revalidate

{
  "error_code" : "AUTH_TOKEN_REVOKED",
  "error_id" : "bcfe97b5092f4101a3b69417a6328ba4"
}
```

# Crear usuario final
<code>POST /crear-usuario</code>

### Campos de solicitud

| Path                      | Tipo          | Descripción   |
| :---                      |    :----      |          :--- |
| user_name                 | String        | El nombre de usuario designado es el mismo que el nombre común, la dirección de correo electrónico o el número de teléfono |
| name                      | String        | El nombre del usuario                                             |
| description               | String        | La descripción del usuario                                        |
| organization              | String        | La organización del usuario.                                      |
| visit_purpose             | String        | El propósito de la visita del usuario.                            |
| email_address             | String        | La dirección de correo electrónico del usuario.                   |
| phone_number              | String        | El número de teléfono del usuario.                                |
| password                  | String        | La contraseña de usuario de usuario                               |
| email_password_delivery   | String        | La entrega de la contraseña de correo electrónico del usuario.    |
| sms_password_delivery     | String        | La entrega de la contraseña de SMS del usuario                    |
| user_group_id             | Number        | El ID del grupo del usuario                                       |

### HTTP Request
```JSON
POST /crear-usuario HTTP/1.1
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkBjdXN0MDAxLmNvbSIsInVzZXJfaWQiOjEsInJvbGUiOiJBZG1pbmlzdHJhdG9yIiwib3duZXJfaWQiOjEwMiwiZGF0YV9jZW50ZXIiOiJVU19XRVNUIiwic2NvcGVzIjpbImxvZ291dCIsImF1dGgiLCJhdXRoOnIiLCJ0b2tlbjpuZXciLCJwZXJtOmNoZWNrIiwibHJvIiwibHJvOnIiLCJhY2NvdW50IiwiYWNjb3VudDpyIiwidmlxOmJhY2t1cCIsInVzZXIiLCJ1c2VyOnIiLCJoaXEiLCJoaXE6ciIsIm9yZyIsIm9yZzpuZXciLCJvcmc6ZGVsIiwib3JnOnJlbmFtZSIsImhpcS5jdHgiLCJoaXEuY3R4OnIiLCJoaXEuY3R4OnciLCJkZXZpY2UiLCJkZXZpY2U6ciIsImRldmljZTpsaXN0IiwiZGV2aWNlOnZpZXciLCJkZXZpY2U6bmV3IiwiZGV2aWNlOmRlbCIsImRldmljZTpjbGkiLCJkZXZpY2U6ZGVwbG95IiwiZGV2aWNlOm1hbmFnZSIsImRldmljZTp1bm1hbmFnZSIsImRldmljZTpyZWJvb3QiLCJkZXZpY2U6cmVzZXQiLCJjbGllbnQiLCJjbGllbnQ6ciIsImxvY2F0aW9ucyIsImxvY2F0aW9uczpyIiwibmV0d29yay1wb2xpY3kiLCJwb2xpY3k6c3NpZCIsIm5ldHdvcmstcG9saWN5OnIiLCJzc2lkIiwic3NpZDpyIiwicGNnOmtleSIsInBjZzprZXk6ciIsInN1YnNjcmlwdGlvbnMtd2ViaG9vayIsInN1YnNjcmlwdGlvbnMtd2ViaG9vazpyIiwiY2NnIiwiY2NnOnIiLCJsb2ciLCJsb2c6ciIsImN3cCIsImN3cDpyIiwic21zLXRtcGwiLCJzbXMtdG1wbDpyIiwiY2xhc3MtcnVsZSIsImNsYXNzLXJ1bGU6ciIsInVzZXItcHJvZmlsZSIsInVzZXItcHJvZmlsZTpyIiwicmFkaXVzLXByb3h5IiwicmFkaXVzLXByb3h5OnIiLCJyYWRpdXMtc2VydmVyIiwicmFkaXVzLXNlcnZlcjpyIiwidXNlcmdyb3VwIiwidXNlcmdyb3VwOnIiLCJkZXBsb3ltZW50IiwiZGVwbG95bWVudDpyIiwiYWQtc2VydmVyIiwiYWQtc2VydmVyOnIiLCJhbGVydCIsImFsZXJ0OnIiLCJhcHAiLCJhcHBsaWNhdGlvbjpyIiwibDMtYWRkcmVzcy1wcm9maWxlIiwibDMtYWRkcmVzcy1wcm9maWxlOnIiLCJ2bGFuLXByb2ZpbGUiLCJ2bGFuLXByb2ZpbGU6ciIsImVuZHVzZXIiLCJlbmR1c2VyOnIiLCJyYWRpdXMtY2xpZW50LW9iamVjdCIsInJhZGl1cy1jbGllbnQtb2JqZWN0OnIiLCJsZGFwLXNlcnZlciIsImxkYXAtc2VydmVyOnIiLCJlbWFpbC10ZW1wbGF0ZSIsImVtYWlsLXRlbXBsYXRlOnIiLCJjZXJ0aWZpY2F0ZSIsImNlcnRpZmljYXRlOnIiLCJyYWRpby1wcm9maWxlIiwicmFkaW8tcHJvZmlsZTpyIl0sImN1c3RvbWVyX2lkIjoxLCJjdXN0b21lcl9tb2RlIjowLCJoaXFfZW5hYmxlZCI6dHJ1ZSwib3JnX2lkIjowLCJxdW90YSI6Ijc1MDA7dz0zNjAwIiwic2hhcmQiOiJVUyIsImlzcyI6ImFwaS5leHRyZW1lY2xvdWRpcS5jb20iLCJpYXQiOjE2NzcwMzUwNzMsImV4cCI6MTY3NzYzOTg3M30.PkfZBCYt_8a4GwADJPisNTgUyErUlduL8IgaFSsJ1_g
Host: accesspoint-tacobell.up.railway.app/api
Content-Type: application/json
Content-Length: 316

{
  "user_group_id" : 1,
  "name" : "test-user-1",
  "user_name" : "test-user-1",
  "organization" : "DEFAULT",
  "visit_purpose" : "GUEST",
  "description" : "this is test user1",
  "email_address" : "test1@google.com",
  "phone_number" : "123456789",
  "password" : "***",
  "sms_password_delivery" : "123456789"
}
```

### Campos de respuesta
| Path                      | Tipo          | Descripción   |
| :---                      |    :----      |          :--- |
| id                        | Number       | La identificación del usuario | 
| create_time               | String        | La última hora de creación |
| update_time               | String        | La última hora de actualización |
| org_id                    | Number        | El identificador de la organización
| name                      | String        | El nombre del usuario                                             |
| user_name                 | String        | El nombre de usuario designado es el mismo que el nombre común, la dirección de correo electrónico o el número de teléfono |
| description               | String        | La descripción del usuario                                        |
| organization              | String        | La organización del usuario.                                      |
| visit_purpose             | String        | El propósito de la visita del usuario.                            |
| email_address             | String        | La dirección de correo electrónico del usuario.                   |
| phone_number              | String        | El número de teléfono del usuario.                                |
| password                  | String        | La contraseña del usuario                                         |
| email_password_delivery   | String        | La entrega de la contraseña de correo electrónico del usuario.    |
| sms_password_delivery     | String        | La entrega de la contraseña de SMS del usuario                    |
| user_group_id             | Number        | El ID del grupo del usuario                                       |
| user_group_name           | String        | El nombre del grupo de usuarios                                   |
| approval_type             | String        | El tipo de aprobación                                             |
| expired_time              | Number        | El tiempo de expiración de la contraseña                          |

### HTTP Request
```JSON
HTTP/1.1 200 OK
Content-Length: 580
Pragma: no-cache
RateLimit-Limit: 7500;w=3600
X-XSS-Protection: 1; mode=block
Expires: 0
X-Content-Type-Options: nosniff
RateLimit-Remaining: 7438
Content-Type: application/json;charset=UTF-8
Strict-Transport-Security: max-age=31536000 ; includeSubDomains
Cache-Control: no-cache, no-store, max-age=0, must-revalidate

{
  "id" : 1,
  "create_time" : "2023-02-22T03:04:33.000+0000",
  "update_time" : "2023-02-22T03:04:33.000+0000",
  "org_id" : 0,
  "name" : "test-user-1",
  "description" : "this is test user1",
  "email_address" : "test1@google.com",
  "phone_number" : "123456789",
  "password" : "***",
  "user_name" : "test-user-1",
  "organization" : "DEFAULT",
  "visit_purpose" : "GUEST",
  "email_password_delivery" : "",
  "sms_password_delivery" : "123456789",
  "user_group_id" : 1,
  "user_group_name" : "TEST-USER-GROUP-1",
  "approval_type" : "NO_APPROVAL",
  "expired_time" : 300
}
```
### cURL Request
```PHP
$ curl 'accesspoint-tacobell.up.railway.app/api/crear-usuario' -i -X POST \
    -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkBjdXN0MDAxLmNvbSIsInVzZXJfaWQiOjEsInJvbGUiOiJBZG1pbmlzdHJhdG9yIiwib3duZXJfaWQiOjEwMiwiZGF0YV9jZW50ZXIiOiJVU19XRVNUIiwic2NvcGVzIjpbImxvZ291dCIsImF1dGgiLCJhdXRoOnIiLCJ0b2tlbjpuZXciLCJwZXJtOmNoZWNrIiwibHJvIiwibHJvOnIiLCJhY2NvdW50IiwiYWNjb3VudDpyIiwidmlxOmJhY2t1cCIsInVzZXIiLCJ1c2VyOnIiLCJoaXEiLCJoaXE6ciIsIm9yZyIsIm9yZzpuZXciLCJvcmc6ZGVsIiwib3JnOnJlbmFtZSIsImhpcS5jdHgiLCJoaXEuY3R4OnIiLCJoaXEuY3R4OnciLCJkZXZpY2UiLCJkZXZpY2U6ciIsImRldmljZTpsaXN0IiwiZGV2aWNlOnZpZXciLCJkZXZpY2U6bmV3IiwiZGV2aWNlOmRlbCIsImRldmljZTpjbGkiLCJkZXZpY2U6ZGVwbG95IiwiZGV2aWNlOm1hbmFnZSIsImRldmljZTp1bm1hbmFnZSIsImRldmljZTpyZWJvb3QiLCJkZXZpY2U6cmVzZXQiLCJjbGllbnQiLCJjbGllbnQ6ciIsImxvY2F0aW9ucyIsImxvY2F0aW9uczpyIiwibmV0d29yay1wb2xpY3kiLCJwb2xpY3k6c3NpZCIsIm5ldHdvcmstcG9saWN5OnIiLCJzc2lkIiwic3NpZDpyIiwicGNnOmtleSIsInBjZzprZXk6ciIsInN1YnNjcmlwdGlvbnMtd2ViaG9vayIsInN1YnNjcmlwdGlvbnMtd2ViaG9vazpyIiwiY2NnIiwiY2NnOnIiLCJsb2ciLCJsb2c6ciIsImN3cCIsImN3cDpyIiwic21zLXRtcGwiLCJzbXMtdG1wbDpyIiwiY2xhc3MtcnVsZSIsImNsYXNzLXJ1bGU6ciIsInVzZXItcHJvZmlsZSIsInVzZXItcHJvZmlsZTpyIiwicmFkaXVzLXByb3h5IiwicmFkaXVzLXByb3h5OnIiLCJyYWRpdXMtc2VydmVyIiwicmFkaXVzLXNlcnZlcjpyIiwidXNlcmdyb3VwIiwidXNlcmdyb3VwOnIiLCJkZXBsb3ltZW50IiwiZGVwbG95bWVudDpyIiwiYWQtc2VydmVyIiwiYWQtc2VydmVyOnIiLCJhbGVydCIsImFsZXJ0OnIiLCJhcHAiLCJhcHBsaWNhdGlvbjpyIiwibDMtYWRkcmVzcy1wcm9maWxlIiwibDMtYWRkcmVzcy1wcm9maWxlOnIiLCJ2bGFuLXByb2ZpbGUiLCJ2bGFuLXByb2ZpbGU6ciIsImVuZHVzZXIiLCJlbmR1c2VyOnIiLCJyYWRpdXMtY2xpZW50LW9iamVjdCIsInJhZGl1cy1jbGllbnQtb2JqZWN0OnIiLCJsZGFwLXNlcnZlciIsImxkYXAtc2VydmVyOnIiLCJlbWFpbC10ZW1wbGF0ZSIsImVtYWlsLXRlbXBsYXRlOnIiLCJjZXJ0aWZpY2F0ZSIsImNlcnRpZmljYXRlOnIiLCJyYWRpby1wcm9maWxlIiwicmFkaW8tcHJvZmlsZTpyIl0sImN1c3RvbWVyX2lkIjoxLCJjdXN0b21lcl9tb2RlIjowLCJoaXFfZW5hYmxlZCI6dHJ1ZSwib3JnX2lkIjowLCJxdW90YSI6Ijc1MDA7dz0zNjAwIiwic2hhcmQiOiJVUyIsImlzcyI6ImFwaS5leHRyZW1lY2xvdWRpcS5jb20iLCJpYXQiOjE2NzcwMzUwNzMsImV4cCI6MTY3NzYzOTg3M30.PkfZBCYt_8a4GwADJPisNTgUyErUlduL8IgaFSsJ1_g' \
    -H 'Content-Type: application/json' \
    -d '{
  "user_group_id" : 1,
  "name" : "test-user-1",
  "user_name" : "test-user-1",
  "organization" : "DEFAULT",
  "visit_purpose" : "GUEST",
  "description" : "this is test user1",
  "email_address" : "test1@google.com",
  "phone_number" : "123456789",
  "password" : "***",
  "sms_password_delivery" : "123456789"
}'
```
