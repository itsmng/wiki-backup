## Introduction

Thank you for downloading the ITSM-NG ticket manager app!
Before installation, you should know some issues:
+ The language of the application is only French
+ Some ITSM-NG plugins that modify ticket mechanics may not be compatible

## Installation

### ITSM-NG web part

Go to Setup/General/API, you will find the URL of the API.
You need to set some settings:
+ Enable Rest API = Yes

+ Enable login with credentials = Yes

+ Enable login with external token = No

### ITSM-NG app part

When you launch for first time ITSM-NG app, you will have an error. It's normal because this app needs 2 things:
+ URL of the API

+ Connection API token

#### URL of the API
you will find it Setup/General/API of ITSM-NG web.\
example: http://xx.xx.xx.xx/itsm-ng/apirest.php/
```
⚠ Don't forget to keep the "/" at the end of URL ⚠
```

#### Connection API token
You need to create your token with your ITSM-NG login and password.
```
login:password
```
convert to base64 with https://www.base64encode.org/ for example.