# kenaflowPNP.SMS

[Link to sms77](https://www.sms77.io)

[Link to documentation of kenaflow](https://doc.kenaflow.com)

[Video tutorial at Youtube](https://www.youtube.com/watch?v=H1nt10fP4QE)

# How to send an SMS with sms77.io

It´s quite easy to send an SMS with the business gateway of sms77

This is the request with PowerShell only.

```powershell
  $Request = "https://gateway.sms77.io/api/sms?u=<user>&p=<key>&to=<phone>&type=<type>&text=<message>"
  Invoke-WebRequest -Uri $Request
```

You can find all API specification at there developer plattform [sms77.io API documentation](https://www.sms77.io/de/entwickler/)

In a real example from my own application I defined the user and key in the WFconfig list. For the replacement of variables and parameters I used the Invoke-KFTemplate of **kenaflow**. This workflow responds to a list with the fields "To" with the phone number and "Message" with the message.

```powershell
  $Request = [string](Invoke-KFTemplate -template "https://gateway.sms77.io/api/sms?u=[[sms77.user]]&p=[[sms77.key]]&to={{To}}&type=direct&text={{Message}})
  Invoke-WebRequest -Uri $Request
```
