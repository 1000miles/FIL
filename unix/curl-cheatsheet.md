
## cURL Cheat Sheet

### Get a copy of a file

**1. Get a copy of a file from an external resource into the current directory of your local computer**

Example:

```bash
curl -X GET https://raw.githubusercontent.com/Asquera/wheelmap-devenv/master/Vagrantfile > Vagrantfile
```

### Retrieve infos

**1. Get infos (flag: `i`) from a website into your command line tool:**

```bash
$ curl -i  example.com
```

Output Example:
```
HTTP/1.1 200 OK
Cache-Control: max-age=604800
Content-Type: text/html
Date: Wed, 25 May 2016 20:47:12 GMT
Etag: "359670651+ident"
Expires: Wed, 01 Jun 2016 20:47:12 GMT
Last-Modified: Fri, 09 Aug 2013 23:54:35 GMT
Server: ECS (fll/0786)
Vary: Accept-Encoding
X-Cache: HIT
x-ec-custom-error: 1
Content-Length: 1270

<!doctype html>
<html>
<head>
    <title>Example Domain</title>

    <meta charset="utf-8" />
    <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
</head>

<body>
<div>
    <h1>Example Domain</h1>
    <p>This domain is established to be used for illustrative examples in documents. You may use this
    domain in examples without prior coordination or asking for permission.</p>
    <p><a href="http://www.iana.org/domains/example">More information...</a></p>
</div>
</body>
</html>
```

**2. Follow a website URL that has been moved to another domain with the flag `-L`:**

```bash
$ curl -L example.com
```

## Download Files

**1. Download and save a file with the same name into your current directory from a URL with the flag `-O`:**

```bash
$ curl -O https://github.com/1000miles/FIL/blob/master/security/passphrase.png
```

Output Example:
```bash
% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                               Dload  Upload   Total   Spent    Left  Speed
100 32554    0 32554    0     0  22949      0 --:--:--  0:00:01 --:--:-- 22957
```

**2. Download and save a file into your current directory rename it as you want by using the flag `-o`:**

```bash
$ curl -o "password.png" https://github.com/1000miles/FIL/blob/master/security/passphrase.png
```

**3. Check for the file with the the pipe `|` and `grep`:**

```bash
$ ls -la | grep password.png
```

Output Example:
```bash
-rw-r--r--   1 1000miles  staff  32554 May 25 23:05 password.png
```

## HTTP-Requests

**1. Send a http-request (-X) using the method GET to a web server to retrieve infos:**

```bash
$ curl -X GET example.com
```

**2. Send a http-request (-X) using the method POST to a web server:**

```bash
$ curl -X POST example.com
```

**3. Send a http-request (-X) using the method PUT to a web server:**

```bash
$ curl -X PUT example.com
```

**4. Send a http-request (-X) using the method POST to a web server with the flag `d` (data) as part of the request-body and pass in params:**

```bash
$ curl -X POST -d "firstname=Johnny&lastname=Crash" example.com
```

**5. Send a http-request (-X) using the method POST to a web server with the flag `d` (data) as part of the request-body and pass in params in JSON-format:**

```bash
$ curl -X POST -d "{\"name\":\"Johnny\"}" example.com
```

### Send a file

**1. Make sure to create a file with params in JSON-format, e.g. myfile.json. Now send a http-request and pass in the file to the web server with the prefix `@``.**

```bash
$ curl -X POST -d @myfile.json example.com
```

**2. Send a http-request and pass in form parameters with the flag `-F` along with params for the header flag `-H`:**

```bash
$ curl -X POST -F user[firstname]=Johnny -F user[lastname]=Crash -F foo=bar \
  example.com -H "Accept: application/json"
```

**3. Send a http-request and upload a file with form parameters, this time using the path to your file:**
```bash
$ curl -X POST -F user[firstname]=Johnny -F user[lastname]=Crash -F foo=bar \
  -F user[image]=@path/to/password.png example.com/page
  -H "Accept: application/json"
```

### Set headers

**1. Send header params with your http-request using the method POST:**
```bash
$ curl -X POST -d @myfile.json example.com \
  -H "Accept: application/json" -H "X-Auth: 98765432"
```

### Basic Auth

**2. Send a http-request (-X) with login credentials (username:password) to a server using the method POST:**

```bash

$ curl -X POST -u "username:password" example.com/login
```

**3. Send a http-request with login credentials to a server using the method POST:**

```bash

$ curl -i -u "username:password" example.com/login
```

**4. Login in with the `-u` flag, save the session cookie that is returned, and pass that session cookie back again:**

```bash

$ curl -X POST -D headers -u "user:password" \
  example.com/login

  or do the more verbose way:

$ curl -X POST --dump-header headers -u "user:password" \
  example.com/login
```

Note: By using the flag `-D` you make a dump and save it into a file in the current directory of your local computer.

**5. Store the cookies of a http-request and send it to the web server:**

```bash

$ curl -X POST -c saved_cookies.txt -u "user:password" \
  example.com/login
```

**6. Pass back the headers with the flag `b` to a web server:**

```bash

$ curl -b headers example.com/page
```

```bash

$ curl -b file.txt example.com/page2
```
Note: With the flag `-b` and a file we pass back the content of the file.
