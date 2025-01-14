
## Lab Description :

![image](https://github.com/sh3bu/Portswigger_labs/assets/67383098/3ecb8c6e-4cda-4347-8943-023251558d74)

## Overview :

### Mass assignment vulnerabilities

Mass assignment (also known as auto-binding) can inadvertently create hidden parameters. It occurs when software frameworks automatically bind request parameters to fields on an internal object. Mass assignment may therefore result in the application supporting parameters that were never intended to be processed by the developer.

### Identifying hidden parameters
Since mass assignment creates parameters from object fields, you can often identify these hidden parameters by manually examining objects returned by the API.

For example, consider a PATCH /api/users/ request, which enables users to update their username and email, and includes the following JSON:

```json
{
    "username": "wiener",
    "email": "wiener@example.com",
}
```
