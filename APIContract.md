### BODY POST LOGIN
```json
{
    "email": "admin@gudang.com",
    "password": "123456"
}
```

### EXAMPLE RESPONSE LOGIN SUCCESS
```sql
{
    "meta": {
        "message": "Login user success!",
        "code": 200,
        "status": "success"
    },
    "data": {
        "id": 1,
        "email": "admin@gudang.com",
        "role": "admin_gudang",
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjo2fQ.F-8Wkdr-84JAw0CGhloMpbKFi2QwpXvSbvXBCtoYrHs"
    }
}
```

### EXAMPLE RESPONSE LOGIN ERROR UNAUTHORIZED
```sql
{
    "meta": {
        "message": "Unauthorized user!",
        "code": 401,
        "status": "error"
    },
    "data": null
}
```

### EXAMPLE RESPONSE LOGIN ERROR 400
```sql
{
    "meta": {
        "message": "Error",
        "code": 400,
        "status": "error"
    },
    "data": null
}
```


### BODY POST REGISTER
```json
{
	"name": "admin gudang"
  "email": "admin@gudang.com",
  "password": "123456",
	"role": 2,
	"merchant_id": 1
}
```

### EXAMPLE RESPONSE REGISTER SUCCESS
```sql
{
    "meta": {
        "message": "Register user success!",
        "code": 200,
        "status": "success"
    },
    "data": {
        "id": 2,
        "email": "admin@gudang.com",
		    "name": "admin gudang",
        "role": 2,
		    "merchant_id": 1
    }
}
```

### EXAMPLE RESPONSE REGISTER ERROR UNAUTHORIZED
```sql
{
    "meta": {
        "message": "Unauthorized user!",
        "code": 401,
        "status": "error"
    },
    "data": null
}
```

### EXAMPLE RESPONSE REGISTER ERROR 400
```sh
{
    "meta": {
        "message": "Error",
        "code": 400,
        "status": "error"
    },
    "data": null
}
```
