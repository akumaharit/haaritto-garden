---
{"dg-publish":true,"permalink":"/introduction/","created":"2025-09-14T21:39:04.055+07:00","updated":"2025-09-14T21:41:02.089+07:00"}
---

### Intro 
https://www.tutorialspoint.com/sap_abap/index.htm
SAP run with its SAP kernel, SAP code is stored in the SAP database (not an external file like other programming language)

![Object Directory Entry Prompt.png](/img/user/3%20Resources/Attachment/Object%20Directory%20Entry%20Prompt.png)

 Any change you do through SAP will prompt you to create object directory, choose the "development class" to choose the transport route that we want to use for the development. IF you don't want to transport it anywhere, just click 'local object'
 - Anytime you use local object, it will be automatically assigned development class to `$tmp`
 - When activating the objects, ALWAYS active one object at a time #tounderstand 
 - Everytime you **ACTIVE** the object, it will automatically **SAVE** the object before activating.

