# ZAP by Checkmarx Scanning Report

ZAP by [Checkmarx](https://checkmarx.com/).


## Summary of Alerts

| Risk Level | Number of Alerts |
| --- | --- |
| High | 0 |
| Medium | 0 |
| Low | 0 |
| Informational | 5 |




## Alerts

| Name | Risk Level | Number of Instances |
| --- | --- | --- |
| Authentication Request Identified | Informational | 3 |
| Information Disclosure - Suspicious Comments | Informational | 1 |
| Modern Web Application | Informational | 3 |
| Session Management Response Identified | Informational | 49 |
| User Agent Fuzzer | Informational | 24 |




## Alert Detail



### [ Authentication Request Identified ](https://www.zaproxy.org/docs/alerts/10111/)



##### Informational (High)

### Description

The given request has been identified as an authentication request. The 'Other Info' field contains a set of key=value lines which identify any relevant fields. If the request is in a context which has an Authentication Method set to "Auto-Detect" then this rule will change the authentication to match the request identified.

* URL: http://localhost:8000/login
  * Method: `POST`
  * Parameter: `username`
  * Attack: ``
  * Evidence: `password`
  * Other Info: `userParam=username
userValue=foo-bar@example.com
passwordParam=password
referer=http://localhost:8000/login
csrfToken=csrf_token`
* URL: http://localhost:8000/login
  * Method: `POST`
  * Parameter: `username`
  * Attack: ``
  * Evidence: `password`
  * Other Info: `userParam=username
userValue=test.admin@admin.fi
passwordParam=password
referer=https://localhost:8000/login
csrfToken=csrf_token`
* URL: http://localhost:8000/login
  * Method: `POST`
  * Parameter: `username`
  * Attack: ``
  * Evidence: `password`
  * Other Info: `userParam=username
userValue=testadmin@admin.fi
passwordParam=password
referer=https://localhost:8000/login
csrfToken=csrf_token`

Instances: 3

### Solution

This is an informational alert rather than a vulnerability and so there is nothing to fix.

### Reference


* [ https://www.zaproxy.org/docs/desktop/addons/authentication-helper/auth-req-id/ ](https://www.zaproxy.org/docs/desktop/addons/authentication-helper/auth-req-id/)



#### Source ID: 3

### [ Information Disclosure - Suspicious Comments ](https://www.zaproxy.org/docs/alerts/10027/)



##### Informational (Low)

### Description

The response appears to contain suspicious comments which may help an attacker.

* URL: http://localhost:8000/static/index.js
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `from`
  * Other Info: `The following pattern was used: \bFROM\b and was detected in likely comment: "// Retrieve reservations from the API and update the table", see evidence field for the suspicious comment/snippet.`

Instances: 1

### Solution

Remove all comments that return information that may help an attacker and fix any underlying problems they refer to.

### Reference



#### CWE Id: [ 615 ](https://cwe.mitre.org/data/definitions/615.html)


#### WASC Id: 13

#### Source ID: 3

### [ Modern Web Application ](https://www.zaproxy.org/docs/alerts/10109/)



##### Informational (Medium)

### Description

The application appears to be a modern web application. If you need to explore it automatically then the Ajax Spider may well be more effective than the standard one.

* URL: http://localhost:8000/cookiepolicy
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `<script src="/static/footer.js"></script>`
  * Other Info: `No links have been found while there are scripts, which is an indication that this is a modern web application.`
* URL: http://localhost:8000/privacypolicy
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `<script src="/static/footer.js"></script>`
  * Other Info: `No links have been found while there are scripts, which is an indication that this is a modern web application.`
* URL: http://localhost:8000/terms
  * Method: `GET`
  * Parameter: ``
  * Attack: ``
  * Evidence: `<script src="/static/footer.js"></script>`
  * Other Info: `No links have been found while there are scripts, which is an indication that this is a modern web application.`

Instances: 3

### Solution

This is an informational alert and so no changes are required.

### Reference




#### Source ID: 3

### [ Session Management Response Identified ](https://www.zaproxy.org/docs/alerts/10112/)



##### Informational (Medium)

### Description

The given response has been identified as containing a session management token. The 'Other Info' field contains a set of header tokens that can be used in the Header Based Session Management Method. If the request is in a context which has a Session Management Method set to "Auto-Detect" then this rule will change the session management to use the tokens identified.

* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `03f0e72e-00c0-4fa3-9425-32ca0c918d64`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `1200b3b2-3485-494a-b6b3-1628effeb84d`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `19f5fcfd-9447-49d5-a96f-18015fb57a05`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `21cce8e6-e461-402d-958f-dc44041fdf1b`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `39554517-7203-4d90-960e-bfe19145efbc`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `3c30af93-fc0a-43bf-b66c-c47e3b69ab4f`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `4afc3840-a50a-48fc-8a37-347f1276952c`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `561cd9d2-8b2c-4786-a7a6-a49f6e88a29f`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `62c42980-6877-4835-88eb-1c6d842de8e8`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `8602238e-115f-4379-b1c6-3b26a7b2f9e8`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `8a6c0ee0-753e-4d56-a9e1-eca93b8848ce`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `9666f97e-b3bf-43de-acba-f3609c44dec1`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `a0bd8b13-5074-4451-b77e-932a5b560d54`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `a22ef460-ab5e-4e0d-acb9-ad716d8c8823`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `a9104d1c-6fd4-4d9f-87e6-9d9a66d6430e`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `c35384ab-5c12-4fb9-a32f-2f2d056ef813`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `c7d9ab38-aa75-4239-82df-5d9f995f715d`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `cc006f4a-8bce-404c-9024-3c99533f951f`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `d7a472ed-d00b-46e1-97ab-d81f406dafb8`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `d879dca8-ca46-45c8-a623-f809a846e5a7`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `e75cda89-53e8-402d-b765-8914f1f3932a`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `e8170060-e47f-4043-b78e-9bed2c74dae8`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `e9eb3c9e-69af-4693-95a8-2d1ef4e035fd`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `f3386b95-4ca0-4dfb-9b54-ebd0bb366305`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `1b2bb677-4d84-43bf-8257-8f001d27fe82`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `20de37fa-9413-4de2-a2e0-19bd035031ec`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `2178663c-b4ab-4c2e-8a55-b489187076e3`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `2aab2f77-d44b-41a4-8a0d-5713be741a8f`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `2b25139b-5ef3-4440-9b11-51759ace831e`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `2d026658-12cd-473b-b56f-b2b3e2ae75ae`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `3517007a-e9b0-45cb-92a0-ac92c94ab1e5`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `39090dc5-adab-4f07-a9e2-242bd3861fa6`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `3c051229-b339-4d29-805c-3ae69f2ac888`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `401142cf-47b1-44d1-817c-fd381701242b`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `4135204b-d92d-487c-abb1-5a234cd9c9c4`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `45072474-464d-46da-898a-4c52b84a5c64`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `85ce9965-4b5b-43fb-acda-b09ca6b5e731`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `a1086ebb-1213-44e6-8b2d-ce2e2a135794`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `ac81e30d-6dc6-4431-b631-2779f89d8eb2`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `b5dca3d4-5158-4ee3-b798-80341a34c538`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `b62ccf43-7536-4990-a902-05c61cc21f8f`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `bb59bc51-39a7-43da-b7e8-0e2ee4f9f51a`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `c44360aa-9c91-42b3-b0de-ee50bcbf4011`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `dd1b6dbb-fe15-4245-8df3-9f858d858e8f`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `f460c57d-1bca-47e8-ac26-38b5bdf90249`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `f66b89cf-3256-4180-8b2b-77cdb31f5c47`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `POST`
  * Parameter: `session_id`
  * Attack: ``
  * Evidence: `29dc2b53-5319-4363-a1b2-5bf2f2736af8`
  * Other Info: `
cookie:session_id`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `62c42980-6877-4835-88eb-1c6d842de8e8`
  * Other Info: `
cookie:csrf_token`
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `csrf_token`
  * Attack: ``
  * Evidence: `e75cda89-53e8-402d-b765-8914f1f3932a`
  * Other Info: `
cookie:csrf_token`

Instances: 49

### Solution

This is an informational alert rather than a vulnerability and so there is nothing to fix.

### Reference


* [ https://www.zaproxy.org/docs/desktop/addons/authentication-helper/session-mgmt-id ](https://www.zaproxy.org/docs/desktop/addons/authentication-helper/session-mgmt-id)



#### Source ID: 3

### [ User Agent Fuzzer ](https://www.zaproxy.org/docs/alerts/10104/)



##### Informational (Medium)

### Description

Check for differences in response based on fuzzed User Agent (eg. mobile sites, access as a Search Engine Crawler). Compares the response statuscode and the hashcode of the response body with the original response.

* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Trident/7.0; rv:11.0) like Gecko`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3739.0 Safari/537.36 Edg/75.0.109.0`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:93.0) Gecko/20100101 Firefox/91.0`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (compatible; Yahoo! Slurp; http://help.yahoo.com/help/us/ysearch/slurp)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (iPhone; CPU iPhone OS 8_0_2 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12A366 Safari/600.1.4`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (iPhone; U; CPU iPhone OS 3_0 like Mac OS X; en-us) AppleWebKit/528.18 (KHTML, like Gecko) Version/4.0 Mobile/7A341 Safari/528.16`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/login
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `msnbot/1.1 (+http://search.msn.com/msnbot.htm)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Trident/7.0; rv:11.0) like Gecko`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3739.0 Safari/537.36 Edg/75.0.109.0`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:93.0) Gecko/20100101 Firefox/91.0`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (compatible; Yahoo! Slurp; http://help.yahoo.com/help/us/ysearch/slurp)`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (iPhone; CPU iPhone OS 8_0_2 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12A366 Safari/600.1.4`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `Mozilla/5.0 (iPhone; U; CPU iPhone OS 3_0 like Mac OS X; en-us) AppleWebKit/528.18 (KHTML, like Gecko) Version/4.0 Mobile/7A341 Safari/528.16`
  * Evidence: ``
  * Other Info: ``
* URL: http://localhost:8000/register
  * Method: `GET`
  * Parameter: `Header User-Agent`
  * Attack: `msnbot/1.1 (+http://search.msn.com/msnbot.htm)`
  * Evidence: ``
  * Other Info: ``

Instances: 24

### Solution



### Reference


* [ https://owasp.org/wstg ](https://owasp.org/wstg)



#### Source ID: 1


