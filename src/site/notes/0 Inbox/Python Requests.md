---
{"dg-publish":true,"permalink":"/0-inbox/python-requests/","created":"2025-10-05T14:30:40.341+07:00","updated":"2025-10-05T14:57:45.642+07:00"}
---

`import requests`
Use `httpbin.rog` to check for example of simple HTTP request and response

## Basic of sending and receiving response
```python
import requests
response = requests.get("https://httpbin.org/get")
print(response.status_code)
res_json = response.json() # return JSON (dictionary), will also return 'origin' which is the sender ip-address
print(response.content)
del res_json['origin'] # remove 'origin' from the json
print(res_json)
```

## Sending GET Resposne
```python
response = requests.get("https://httpbin.org/get?name=Make&age=25") #passing argument
params = {
    "name" : "Mike",
    "age" : 25
}
response = requests.get("https://httpbin.org/get", params = params) #another way of passing the argument
```

## Sending POST Response
```python
# sending the data via post request -> the best practice is to call it "payload" instead of params.
payload = {
    "name" : "Mike",
    "age" : 25
}
response = requests.post("https://httpbin.org/post", data = payload) #passing argument
```


## Catching 404 code response
``` python
response = requests.get("https://httpbin.org/status/404") # 404 is when you don't find sometthing
print(response.status_code)
if response.status_code == requests.codes.not_found: #this way you don't have to remember it is 404 code, it is from the requests module, codes package
    print("Not Found")
else:
    print(response.status_code)
```

## User-Agent
an identification that tell the webserver what software are you using.
sometimes the webserver may block you if you request using certain user-agent
you can specify user-agent manually

``` python
headers = {
	"User-Agent" : "HelloWorld/1.1" # You can customize this one to be other user-agent such as WebBrowser from iPhone etc.
}
response = requests.get("https://httpbin.org/user-agent",headers=headers)
```

## Specifying the content we are accepting from the requests.
This will send a response and accept the image file
If you don't select the "accept" via header, it may return 406

```python
headers = {
	"Accept" : "image/png" #can be image/jpg
}
response = requests.get("https://httpbin.org/get",headers=headers)

with open("myimage.png","wb") as f:
	f.write(response.content)

```

## Specifying the timeout and raise an exception or just continue
```python
# This is an except of the code's pattern that can be used to test for a server if it is working without raising an exception that some the code from running.
for _ in [1,2,3]:
    try:
        response = requests.get("https://httpbin.org/delay/2", timeout = 3) #if longer than 3, raise an exception.
        print(response.json())
    except:
        continue
```

## Specifying proxies server
```python

proxies = {
	"http" : "139.99.237.62:80",
	"https" : "139.99.237.62:80" #you should not use this if it is not https url.
}
response = requets.get("http://httpbin.org/get", proxies = proxies)
#the response will give the origin of the proxies server.

```