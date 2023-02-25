# Autenticación
Login
<code>POST /login</code>

### Campos de solicitud

| Path        | Tipo        | Descripción   |
| :---        |    :----   |          :--- |
| username    | String      | El nombre de usuario de inicio de sesión   |
| password    | String      | La contraseña de inicio de sesión      |

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
PathTypeDescription`user_name`

`String`

The designated username the same as the common name, emailAddress, or phoneNumber

`name`

`String`

The name of user

`description`

`String`

The description of user

`organization`

`String`

The organization of user

`visit_purpose`

`String`

The visit purpose of user

`email_address`

`String`

The email address of user

`phone_number`

`String`

The phone number of user

`password`

`String`

The user password of user

`email_password_delivery`

`String`

The email password delivery of user

`sms_password_delivery`

`String`

The SMS password delivery of user

`user_group_id`

`Number`

The group ID of user




