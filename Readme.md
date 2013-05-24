
# NetDNA API Docs

[NetDNA](http://www.netdna.com) is a fast &amp; reliable content delivery network ("CDN") provider.

## Index

* [Overview](#overview)
* [Support](#support)
* [Changelog](#changelog)
* [Account API](#account-api)
* [Users API](#users-api)
* [Zones API](#zones-api)
* [Reports API](#reports-by-zone-api)
* [Clients API](#reports-by-file-name-api)


## Overview

1. Sign up for a free NetDNA [developer account](http://www.netdna.com/netdna-free-trial/).

2. Create a [new application](https://cp.netdna.com/account/api/create).

3. Integrate with our RESTful API using your language wrapper:
  - Node (NPM) <https://github.com/netdna/node-netdna>
  - .NET <https://github.com/netdna/netdnarws-net>
  - Ruby <https://github.com/netdna/netdnarws-ruby>
  - Python <https://github.com/netdna/netdnarws>
  - PHP <https://github.com/netdna/netdnarws-php>
  - Perl <https://github.com/netdna/netdnarws-perl>

Follow the documentation for our API below!


## Support

Have a question? Check out our [Knowledge base](http://support.netdna.com/) to see if your question has already been answered.

Still need help?  Visit our [Contact](http://www.netdna.com/contact/) page to get in touch.

Feel free to tweet and follow us [@netdna](https://twitter.com/netdna) and [@netdnasupport](https://twitter.com/netdnasupport).


## Changelog

  - **2013-03-29**  Added "Bad Request" for Purges without file(s) parameter in body
  - **2013-03-14**  Added .ie to the TLD Validation
  - **2013-03-12**  Added single file Purge to use cURL multi
  - **2013-03-12**  Fixed SSL Update Bug
  - **2013-03-08**  cURL Multi Purge Files
  - **2013-03-07**  Fix 3-legged OAuth Restriction
  - **2013-01-16**  Fixed SSL Bug
  - **2012-12-05**  Added 2xx_hit calculation to all `statuscodebyfilename` Reports
  - **2012-02-27**  Released Alpha Version of RWS API.
---

# Key: Path Parameters

Parameter | Description |
--- | ---
{companyalias} | The alias you used when creating your account |
{zone_type} | The type of zone you are making a request on - one of push,pull, vod, or live |
{report_type} | The format you want the reports summarized by - one of hourly,daily, or monthly. This value can be left blank to receive thetotals ungrouped. |

---

# Account API

## Get Account

Gets account information

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/account.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Account ID |
`name` | The name of your account |
`address_id` | Address ID |
`alias` | Company Alias |
`ssl_credits` | SSL Credits |
`flex_credits` | Flex Location Credits |
`date_created` | Date Created |
`date_updated` | Date Updated |


## Update Account

Updates account information

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/account.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`name` | - | <span class="label important">required</span><br />length: 1-30 chars | The name of your account |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Account ID |
`name` | The name of your account |
`address_id` | Address ID |
`alias` | Company Alias |
`ssl_credits` | SSL Credits |
`flex_credits` | Flex Location Credits |
`date_created` | Date Created |
`date_updated` | Date Updated |


## Get Account Address

Gets account address information

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/account.json/address</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Address ID |
`street1` | Street Address Line 1 |
`street2` | Street Address Line 2 |
`city` | City |
`state` | State |
`zip` | ZIP |
`country` | Country Code |
`date_created` | Date Created |
`date_updated` | Date Updated |


## Update Account Address

Updates account address information

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/account.json/address</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`street1` | - | length: 1-200 chars | Street Address Line 1 |
`street2` | - | length: 1-200 chars | Street Address Line 2 |
`city` | - | length: 1-50 chars | City |
`state` | - | length: 1-50 chars | State |
`zip` | - | length: 3-5 chars; only digits accepted | ZIP |
`country` | - | length: 2 chars | Country Code |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Address ID |
`street1` | Street Address Line 1 |
`street2` | Street Address Line 2 |
`city` | City |
`state` | State |
`zip` | ZIP |
`country` | Country Code |
`date_created` | Date Created |
`date_updated` | Date Updated |




---

# Users API

## List Users

Returns a list of all users on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/users.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | User ID |
`email` | Email Address |
`firstname` | First Name |
`lastname` | Last Name |
`phone` | Phone Number |
`timezone` | User's Timezone |
`date_last_login` | The date and time the user last logged into the system |
`ip_last_login` | The IP for the user at the last login |
`date_created` | Date Created |
`date_updated` | Date Updated |
`roles` | An array of roles for the given user |


## Create User

Creates a new user on the specified account

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/users.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`email` | - | <span class="label important">required</span><br />length: 6-200 chars; valid email address | Email Address |
`password` | - | <span class="label important">required</span><br />length: 5-30 chars | Password |
`firstname` | - | <span class="label important">required</span><br />length: 1-32 chars | First Name |
`lastname` | - | <span class="label important">required</span><br />length: 1-32 chars | Last Name |
`phone` | - | length: 7, 10, 11, or 14 chars; only digits considered | Phone Number |
`timezone` | - | valid::timezone | Valid timezone (see [List ofSupported Timezones](http://php.net/manual/en/timezones.php)) |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | User ID |
`email` | Email Address |
`firstname` | First Name |
`lastname` | Last Name |
`phone` | Phone Number |
`timezone` | User's Timezone |
`date_last_login` | The date and time the user last logged into the system |
`ip_last_login` | The IP for the user at the last login |
`date_created` | Date Created |
`date_updated` | Date Updated |
`roles` | An array of roles for the given user |


## Get User

Gets a user specified by the {user_id} parameter

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/users.json/{user_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | User ID |
`email` | Email Address |
`firstname` | First Name |
`lastname` | Last Name |
`phone` | Phone Number |
`timezone` | User's Timezone |


## Update User

Updates a user specified by the {user_id} parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/users.json/{user_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`email` | - | length: 6-200 chars; valid email address | Email Address |
`firstname` | - | length: 1-32 chars | First Name |
`lastname` | - | length: 1-32 chars | Last Name |
`phone` | - | length: 7, 10, 11, or 14 chars; only digits considered | Phone Number |
`timezone` | - | valid::timezone | Valid timezone (see [List ofSupported Timezones](http://php.net/manual/en/timezones.php)) |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | User ID |
`email` | Email Address |
`firstname` | First Name |
`lastname` | Last Name |
`phone` | Phone Number |
`timezone` | User's Timezone |


## Delete User

Deletes a user specified by the {user_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/users.json/{user_id}</span></div>
</div>



---

# Zones API

## List Zones

Returns a list of all zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones.json</span></div>
</div>

## Get Zone Summary

Gets a summarized count of all zone types on the specified
account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones.json/summary</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`pull` | The number of pull zones for your account |
`push` | The number of push zones for your account |
`vod` | The number of vod zones for your account |
`live` | The number of live zones for your account |


## Get Zone Count

Counts all zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones.json/count</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`count` | The total number of content zones for your account |




---

# Pull Zone API

## List Pull Zones

Returns a list of all pull zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Pull Zone ID |
`name` | Pull Zone name |
`url` | Origin URL |
`port` | Port |
`ip` | IP address of the Origin URL |
`compress` | On the fly compression of your files served from our edges.GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`backend_compress` | Allow us to cache compressed versions of your files from theorigin. GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`queries` | Treat Query Strings as a separate cacheable item |
`set_host_header` | The URL sent as the Host in all HTTP Response Headers |
`cache_valid` | Ignore the origin Cache-Control Header and set every request tohave a Max-Age of 1d, 7d, 1M or 12M |
`ignore_setcookie_header` | Ignore any cookies set by the origin in order to make thecontent consistently cacheable |
`ignore_cache_control` | Ignore any max age values set by the origin and use the CDN setvalue instead |
`use_stale` | Serve expired content while fetching new content. This willalso cause the CDN to serve expired content in cases where theorigin is down or the file is not found |
`proxy_cache_lock` | When multiple requests for an uncached file are received, theywill wait until the first response is received rather than sendingeach request back to the origin |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`expires` | Set any request with a no "Cache-Control header" from theorigin to stay on the server. Possible values are 1d, 7d, 1M,12M |
`disallow_robots` | Enable robots.txt |
`disallow_robots_txt` | Use custom robots.txt |
`canonical_link_headers` | Pass the canonical URL in the Link HTTP Header |
`content_disposition` | Force files to download |
`pseudo_streaming` | Enable the zone for pseudo streaming content |
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Create Pull Zone

Creates a new pull zone

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`name` | - | <span class="label important">required</span><br />length: 3-32 chars; only letters, digits, and dash (-)accepted | Pull Zone Name |
`url` | - | <span class="label important">required</span><br />length: 4-100 chars; only valid URLs accepted | Origin URL |
`port` | 80 | length: 1-5 chars; only digits accepted | Port |
`ip` | - | length: 1-10 chars, only digits accepted | Valid IP address of the Origin URL. If omitted, the servicewill try to lookup the IP automatically. |
`compress` | 0 | only 0 or 1 accepted | On the fly compression of your files served from our edges.Enable GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`backend_compress` | 0 | only 0 or 1 accepted | Allow us to cache compressed versions of your files from theorigin. Enable GZip compression for the following file types:text/plain, text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`queries` | 0 | only 0 or 1 accepted | Treat Query Strings as a separate cacheable item |
`set_host_header` | - | length: 4-100 chars; only valid URLs accepted | The URL to send as the Host in all HTTP Response Headers |
`cache_valid` | 1d | length: 1-30 chars; must be a number followed by one of s, m,h, d, M, or Y | Ignore the origin Cache-Control Header and set every request tohave a Max-Age of 1d, 7d, 1M or 12M |
`ignore_setcookie_header` | 0 | only 0 or 1 accepted | Ignore any cookies set by the origin in order to make thecontent consistently cacheable |
`ignore_cache_control` | 0 | only 0 or 1 accepted | Ignore any max age values set by the origin and use the CDN setvalue instead |
`use_stale` | 0 | only 0 or 1 accepted | Serve expired content while fetching new content. This willalso cause the CDN to serve expired content in cases where theorigin is down or the file is not found |
`proxy_cache_lock` | 0 | only 0 or 1 accepted | When multiple requests for an uncached file are received, theywill wait until the first response is received rather than sendingeach request back to the origin |
`label` | - | length: 1-255 chars | Something that describes your zone |
`valid_referers` | - | length: 1-100 chars | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`expires` | 1d | length: 1-32 chars | Set any request with a no "Cache-Control header" from theorigin to stay on the server. Possible values are 1d, 7d, 1M,12M |
`disallow_robots` | 0 | only 0 or 1 accepted | Enable robots.txt |
`disallow_robots_txt` | - | length 1-255 chars | Use custom robots.txt |
`canonical_link_headers` | 1 | only 0 or 1 accepted | Pass the canonical URL in the Link HTTP Header |
`content_disposition` | 0 | only 0 or 1 accepted | Force files to download |
`pseudo_streaming` | 0 | only 0 or 1 accepted | Enable the zone for pseudo streaming content |
`secret` | - | length: 1 - 32 chars | Use a secret to protect your files from unwanted visitors |
`sslshared` | 0 | only 0 or 1 accepted | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Pull Zone ID |
`name` | Pull Zone name |
`url` | Origin URL |
`port` | Port |
`ip` | IP address of the Origin URL |
`compress` | On the fly compression of your files served from our edges.GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`backend_compress` | Allow us to cache compressed versions of your files from theorigin. GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`queries` | Treat Query Strings as a separate cacheable item |
`set_host_header` | The URL sent as the Host in all HTTP Response Headers |
`cache_valid` | Ignore the origin Cache-Control Header and set every request tohave a Max-Age of 1d, 7d, 1M or 12M |
`ignore_setcookie_header` | Ignore any cookies set by the origin in order to make thecontent consistently cacheable |
`ignore_cache_control` | Ignore any max age values set by the origin and use the CDN setvalue instead |
`use_stale` | Serve expired content while fetching new content. This willalso cause the CDN to serve expired content in cases where theorigin is down or the file is not found |
`proxy_cache_lock` | When multiple requests for an uncached file are received, theywill wait until the first response is received rather than sendingeach request back to the origin |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`expires` | Set any request with a no "Cache-Control header" from theorigin to stay on the server. Possible values are 1d, 7d, 1M,12M |
`disallow_robots` | Enable robots.txt |
`disallow_robots_txt` | Use custom robots.txt |
`canonical_link_headers` | Pass the canonical URL in the Link HTTP Header |
`content_disposition` | Force files to download |
`pseudo_streaming` | Enable the zone for pseudo streaming content |
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Get Pull Zones Count

Counts all pull zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/count</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`count` | The number of pull zones on the specified account |


## Get Pull Zone

Gets a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The Pull Zone ID |
`name` | Pull Zone name |
`url` | Origin URL |
`port` | Port |
`ip` | Valid IP address of the Origin URL. If omitted, the servicewill try to lookup the IP automatically. |
`compress` | On the fly compression of your files served from our edges.GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`backend_compress` | Allow us to cache compressed versions of your files from theorigin. GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`queries` | Treat Query Strings as a separate cacheable item |
`set_host_header` | The URL sent as the Host in all HTTP Response Headers |
`cache_valid` | Ignore the origin Cache-Control Header and set every request tohave a Max-Age of 1d, 7d, 1M or 12M |
`ignore_setcookie_header` | Ignore any cookies set by the origin in order to make thecontent consistently cacheable |
`ignore_cache_control` | Ignore any max age values set by the origin and use the CDN setvalue instead |
`use_stale` | Serve expired content while fetching new content. This willalso cause the CDN to serve expired content in cases where theorigin is down or the file is not found |
`proxy_cache_lock` | When multiple requests for an uncached file are received, theywill wait until the first response is received rather than sendingeach request back to the origin |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`expires` | Set any request with a no "Cache-Control header" from theorigin to stay on the server. Possible values are 1d, 7d, 1M,12M |
`disallow_robots` | Enable robots.txt |
`disallow_robots_txt` | Use custom robots.txt |
`canonical_link_headers` | Pass the canonical URL in the Link HTTP Header |
`content_disposition` | Force files to download |
`pseudo_streaming` | Enable the zone for pseudo streaming content |
`sslshared` | Enable Shared SSL. This feature allows you use your zone in HTTPS mode. You don't need your own SSL certificate, our server netdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Update Pull Zone

Updates a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`url` | - | length: 4-100 chars; only valid URLs accepted | Origin URL |
`port` | 80 | length: 1-5 chars; only digits accepted | Port |
`compress` | 0 | only 0 or 1 accepted | On the fly compression of your files served from our edges.Enable GZip compression for the following file types: `text/plain`, `text/html`, `text/javascript`, `text/css`, `text/xml`, `application/javascript`, `application/x-javascript`, `application/xml`, `text/x-component`, `application/json`, `application/xhtml+xml`, `application/rss+xml`, `application/atom+xml`, `app/vnd.ms-fontobject`, `image/svg+xml`, `application/x-font-ttf`, `font/opentype` |
`backend_compress` | 0 | only 0 or 1 accepted | Allow us to cache compressed versions of your files from the origin. Enable GZip compression for the following file types: `text/plain`, `text/html`, `text/javascript`, `text/css`, `text/xml`, `application/javascript`, `application/x-javascript`, `application/xml`, `text/x-component`, `application/json`, `application/xhtml+xml`, `application/rss+xml`, `application/atom+xml`, `app/vnd.ms-fontobject`, `image/svg+xml`, `application/x-font-ttf`, `font/opentype` |
`queries` | 0 | only 0 or 1 accepted | Treat Query Strings as a separate cacheable item |
`set_host_header` | - | length: 4-100 chars; only valid URLs accepted | The URL to send as the Host in all HTTP Response Headers |
`cache_valid` | - | length: 1-30 chars; must be a number followed by one of `s`, `m`, `h`, `d`, `M`, or `Y` | Ignore the origin Cache-Control Header and set every request to have a Max-Age of `1d`, `7d`, `1M` or `12M` |
`ignore_setcookie_header` | 0 | only 0 or 1 accepted | Ignore any cookies set by the origin in order to make the content consistently cacheable |
`ignore_cache_control` | 0 | only 0 or 1 accepted | Ignore any max age values set by the origin and use the CDN set value instead |
`use_stale` | 0 | only 0 or 1 accepted | Serve expired content while fetching new content. This will also cause the CDN to serve expired content in cases where the origin is down or the file is not found |
`proxy_cache_lock` | 0 | only 0 or 1 accepted | When multiple requests for an uncached file are received, they will wait until the first response is received rather than sending each request back to the origin |
`label` | - | length: 1-255 chars | Something that describes your zone |
`valid_referers` | - | length: 1-100 chars | List of domains for http referrer protection (separated by space). Only the domains in the list will be treated as valid referrers |
`expires` | 1d | length: 1-32 chars | Set any request with a no "Cache-Control header" from the origin to stay on the server. Possible values are 1d, 7d, 1M,12M |
`disallow_robots` | 0 | only 0 or 1 accepted | Enable robots.txt |
`disallow_robots_txt` | - | length: 1-255 chars | Use custom robots.txt |
`canonical_link_headers` | 1 | only 0 or 1 accepted | Pass the canonical URL in the Link HTTP Header |
`content_disposition` | 0 | only 0 or 1 accepted | Force files to download |
`pseudo_streaming` | 0 | only 0 or 1 accepted | Enable the zone for pseudo streaming content |
`secret` | - | length: 1 - 32 chars | Use a secret to protect your files from unwanted visitors |
`sslshared` | 0 | only 0 or 1 accepted | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Pull Zone ID |
`name` | Pull Zone name |
`url` | Origin URL |
`port` | Port |
`ip` | Valid IP address of the Origin URL. If omitted, the servicewill try to lookup the IP automatically. |
`compress` | On the fly compression of your files served from our edges.GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`backend_compress` | Allow us to cache compressed versions of your files from theorigin. GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`queries` | Treat Query Strings as a separate cacheable item |
`set_host_header` | The URL sent as the Host in all HTTP Response Headers |
`cache_valid` | Ignore the origin Cache-Control Header and set every request tohave a Max-Age of 1d, 7d, 1M or 12M |
`ignore_setcookie_header` | Ignore any cookies set by the origin in order to make thecontent consistently cacheable |
`ignore_cache_control` | Ignore any max age values set by the origin and use the CDN setvalue instead |
`use_stale` | Serve expired content while fetching new content. This willalso cause the CDN to serve expired content in cases where theorigin is down or the file is not found |
`proxy_cache_lock` | When multiple requests for an uncached file are received, theywill wait until the first response is received rather than sendingeach request back to the origin |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`expires` | Set any request with a no "Cache-Control header" from theorigin to stay on the server. Possible values are 1d, 7d, 1M,12M |
`disallow_robots` | Enable robots.txt |
`disallow_robots_txt` | Use custom robots.txt |
`canonical_link_headers` | Pass the canonical URL in the Link HTTP Header |
`content_disposition` | Force files to download |
`pseudo_streaming` | Enable the zone for pseudo streaming content |
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Delete Pull Zone

Deletes a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>

## Enable Pull Zone

Enables a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>

## Disable Pull Zone

Disables a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>

## Purge Cache

Purges pull zone cache

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}/cache</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`files` | - | An array containing relative paths of the files to purge (i.e./favicon.ico) |

### Code Samples

<ul class="nav nav-tabs" id="myTab">
  <li class="active"><a href="#ruby" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python" data-toggle='tab'>Python</a></li>
  <li><a href="#php" data-toggle='tab'>PHP</a></li>
  <li><a href="#node" data-toggle='tab'>Node</a></li>
  <li><a href="#response" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby">
  <pre>
require 'netdnarws'
api = NetDNARWS::NetDNA.new("myalias", "consumer_key", "consumer_secret")
api.purge(zone_id)
api.purge(zone_id, '/some_file')
api.purge(zone_id, ['/some_file', '/another_file'])</pre>
  </div>
  <div class="tab-pane" id="python">
  <pre>
from netdnarws import NetDNA
api = NetDNA("myalias", "consumer_key", "consumer_secret")
api.delete("/zones/pull.json/zone_id/cache")
api.delete("/zones/pull.json/zone_id/cache", data={'file': '/my-file.png'})</pre>
  </div>
  <div class="tab-pane" id="php">
    <pre>
<?php
require_once('NetDNA.php');
$api = new NetDNA("my_alias","consumer_key","consumer_secret");
$params = array('file' => '/robots.txt');
echo $api->delete('/zones/pull.json/6055/cache', $params);
?></pre>
  </div>
  <div class="tab-pane" id="node">
  <pre>
var netdna = require('netdna')({
  companyAlias: 'alias'
  , consumerKey: 'key'
  , consumerSecret: 'secret'
})
netdna.del('/zones/pull.json/zone_id', callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response">
  <pre>
{ code: 200 }</pre>
  </div>
</div>

---

# Pull Zone Custom Domains API

## List Custom Domains

Returns a list of all custom domains on the zone specified by
{zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull/{zone_id}/customdomains.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | A valid custom domain |


## Create Custom Domain

Adds a new custom domain to {zone_id}

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull/{zone_id}/customdomains.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`custom_domain` | - | <span class="label important">required</span><br />length: 1-255 chars, valid::custom_domain, !valid::full_domain | A valid custom domain |
`type` | - | Applies only to Vod Zones and must be either 'vod-rtmp','vod-pseudo', 'vod-direct', or 'vod-ftp' | The type of custom domain being created |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The valid custom domain |


## Get Custom Domain

Gets a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The valid custom domain |


## Update Custom Domain

Updates a custom domain specified by the id parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`custom_domain` | - | <span class="label important">required</span><br />length: 1-255 chars, valid::custom_domain, !valid::full_domain | A new valid custom domain |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The new valid custom domain |


## Delete Custom Domain

Deletes a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>



---

# Push Zone API

## List Push Zones

Returns a list of all push zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Push Zone ID |
`name` | Push Zone name |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`content_disposition` | Force files to download |
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Create Push Zone

Creates a new push zone

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`name` | - | <span class="label important">required</span><br />length: 3-30 chars; only letters, digits, and dash (-)accepted | Push Zone name |
`password` | - | <span class="label important">required</span><br />length: 5-30 chars; | Push Zone FTP password |
`label` | - | length: 1-255 chars | Something that describes your zone |
`valid_referers` | - | length: 1-200 chars | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`content_disposition` | 0 | only 0 or 1 accepted | Force files to download |
`sslshared` | 0 | only 0 or 1 accepted | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Push Zone ID |
`name` | Push Zone name |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`content_disposition` | Force files to download |
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Get Push Zones Count

Counts all push zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/count</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`count` | The number of push zones on the specified account |


## Get Push Zone

Gets a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Push Zone ID |
`name` | Push Zone name |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`content_disposition` | Force files to download |
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Update Push Zone

Updates a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`label` | - | length: 1-255 chars | Something that describes your zone |
`valid_referers` | - | length: 1-100 chars | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`content_disposition` | 0 | only 0 or 1 accepted | Force files to download |
`sslshared` | 0 | only 0 or 1 accepted | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Push Zone ID |
`name` | Push Zone name |
`label` | Something that describes your zone |
`valid_referers` | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`content_disposition` | Force files to download |
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Delete Push Zone

Deletes a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>

## Enable Push Zone

Enables a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>

## Disable Push Zone

Disables a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>



---

# Push Zone Custom Domains API

## List Custom Domains

Returns a list of all custom domains on the zone specified by
{zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push/{zone_id}/customdomains.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | A valid custom domain |


## Create Custom Domain

Adds a new custom domain to {zone_id}

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push/{zone_id}/customdomains.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`custom_domain` | - | <span class="label important">required</span><br />length: 1-255 chars, valid::custom_domain, !valid::full_domain | A valid custom domain |
`type` | - | Applies only to Vod Zones and must be either 'vod-rtmp','vod-pseudo', 'vod-direct', or 'vod-ftp' | The type of custom domain being created |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The valid custom domain |


## Get Custom Domain

Gets a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The valid custom domain |


## Update Custom Domain

Updates a custom domain specified by the id parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`custom_domain` | - | <span class="label important">required</span><br />length: 1-255 chars, valid::custom_domain, !valid::full_domain | A new valid custom domain |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The new valid custom domain |


## Delete Custom Domain

Deletes a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>



---

# VOD Zone API

## List VOD Zones

Returns a list of all VOD zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | VOD Zone ID |
`name` | VOD Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Create VOD Zone

Creates a new VOD zone

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`name` | - | <span class="label important">required</span><br />length: 3-30 chars; only letters, digits, and dash (-)accepted | VOD Zone user name |
`password` | - | <span class="label important">required</span><br />length: 5-30 chars | Your desired password |
`token` | - | length: 1-64 chars | The token value (shared secret) for secure streaming |
`label` | - | length: 1-255 chars | Something that describes your zone |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | VOD Zone ID |
`name` | VOD Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Get VOD Zones Count

Counts all vod zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/count</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`count` | The number of vod zones on the specified account |


## Get VOD Zone

Gets a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | VOD Zone ID |
`name` | VOD Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Update VOD Zone

Updates a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`password` | - | length: 5-30 chars | Your desired password |
`token` | - | length: 1-64 chars | The token value (shared secret) for secure streaming |
`label` | - | length: 1-255 chars | Something that describes your zone |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | VOD Zone ID |
`name` | VOD Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Delete VOD Zone

Deletes a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>

## Enable VOD Zone

Enables a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>

## Disable VOD Zone

Disables a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>



---

# VOD Zone Custom Domains API

## List Custom Domains

Returns a list of all custom domains on the zone specified by
{zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod/{zone_id}/customdomains.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | A valid custom domain |


## Create Custom Domain

Adds a new custom domain to {zone_id}

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod/{zone_id}/customdomains.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`custom_domain` | - | <span class="label important">required</span><br />length: 1-255 chars, valid::custom_domain, !valid::full_domain | A valid custom domain |
`type` | - | Applies only to Vod Zones and must be either 'vod-rtmp','vod-pseudo', 'vod-direct', or 'vod-ftp' | The type of custom domain being created |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The valid custom domain |


## Get Custom Domain

Gets a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The valid custom domain |


## Update Custom Domain

Updates a custom domain specified by the id parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`custom_domain` | - | <span class="label important">required</span><br />length: 1-255 chars, valid::custom_domain, !valid::full_domain | A new valid custom domain |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The id of the custom domain |
`bucket_id` | The id of the zone the custom domain belongs to |
`custom_domain` | The new valid custom domain |


## Delete Custom Domain

Deletes a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>



---

# Live Zone API

## List Live Zones

Returns a list of all live zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Live Zone ID |
`name` | Live Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Create Live Zone

Creates a new live zone

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`name` | - | <span class="label important">required</span><br />length: 3-30 chars; only letters, digits, and dash (-)accepted | Your desired zone name |
`password` | - | length: 5-30 chars | Your desired password |
`label` | - | length: 1-255 chars | Something that describes your zone |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Live Zone ID |
`name` | Live Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Get Live Zones Count

Counts all live zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/count</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`count` | The number of live zones on the specified account |


## Get Live Zone

Gets a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Live Zone ID |
`name` | Live Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Update Live Zone

Updates a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`password` | - | length: 5-30 chars | Your desired password |
`token` | - | length: 1-64 chars | The token value (shared secret) for secure streaming |
`label` | - | length: 1-255 chars | Something that describes your zone |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Live Zone ID |
`name` | Live Zone name |
`label` | The zone's description |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |


## Delete Live Zone

Deletes a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>

## Enable Live Zone

Enables a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>

## Disable Live Zone

Disables a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>



---

# Zones SSL API

## Get Zone's SSL Information

Get the SSL certificate for the specified {zone_type} and
{zone_id}.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/ssl.json</span></div>
</div>

## Install SSL on Zone

Upload an SSL certificate for the specified {zone_type} and
{zone_id}.

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/ssl.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`ssl_crt` | - | <span class="label important">required</span><br /> | The SSL certificate you are installing. |
`ssl_key` | - | <span class="label important">required</span><br /> | The key for the SSL certificate you are installing. |
`ssl_cabundle` | - | The CA Bundle for the SSL Certificate you are installing. |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The SSL Certificate ID. |
`ssl_crt` | The SSL certificate. |
`ssl_key` | The SSL Private Key. |
`ssl_cabundle` | The CA Bundle for the cert. |
`domain` | The domain applicable to this certificate. |
`date_expiration` | The date of expiration for the certificate. |
`wildcard` | Flag to signify whether this is a wildcard certificate. |


## Update Zone's SSL Information

Update the SSL certificate for the specified {zone_type} and
{zone_id}.

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/ssl.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`ssl_crt` | - | <span class="label important">required</span><br /> | The SSL certificate you are installing. |
`ssl_key` | - | <span class="label important">required</span><br /> | The key for the SSL certificate you are installing. |
`ssl_cabundle` | - | The CABundle for the SSL Certificate you are installing. |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The SSL Certificate ID. |
`ssl_crt` | The SSL certificate. |
`ssl_key` | The SSL Private Key. |
`ssl_cabundle` | The CA Bundle for the cert. |
`domain` | The domain applicable to this certificate. |
`date_expiration` | The date of expiration for the certificate. |
`wildcard` | Flag to signify whether this is a wildcard certificate. |


## Remove Zone's SSL Information

Remove the SSL certificate for the specified {zone_type} and
{zone_id}.

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/ssl.json</span></div>
</div>



---

# Zones Upstream API

## Get Upstream information for the current zone

Get the upstream information for the specified {zone_id}.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/upstream.json</span></div>
</div>

## Enable Upstream on Zone

Create and enable Upstream for a specific {zone_id}.

<div class="heading">
<div class="url POST"><span class="http_method">POST</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/upstream.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`server_url` | - | <span class="label important">required</span><br /> | The server url or ip to provide the streaming resources | 1.0.1 |
`port` | - | <span class="label important">required</span><br /> | The port where server is to be called | 1.0.1 |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The Upstream ID. | 1.0.1 |
`bucket_id` | The bucket_id it belongs to | 1.0.1 |
`server_url` | The server url or ip | 1.0.1 |
`port` | The port it uses to call the server | 1.0.1 |


## Update Zone's Upstream Information

Update the Upstream information for the specified {zone_id}.

<div class="heading">
<div class="url PUT"><span class="http_method">PUT</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/upstream.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`upstream_id` | - | <span class="label important">required</span><br /> | The Upstream Information you're modifying. | 1.0.1 |
`server_url` | - | <span class="label important">required</span><br /> | The server url or ip | 1.0.1 |
`port` | - | <span class="label important">required</span><br /> | The port it uses to call the server | 1.0.1 |


### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | The Upstream ID. | 1.0.1 |
`bucket_id` | The bucket_id it belongs to | 1.0.1 |
`server_url` | The server url or ip | 1.0.1 |
`port` | The port it uses to call the server | 1.0.1 |


## Remove Zone's Upstream Information

Remove the Upstream Information for the specified {zone_id}.

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/upstream.json</span></div>
</div>



---

# Reports by Zone API

## List Zone Stats

Gets all zone usage statistics optionally broken up by
{report_type}. If no {report_type} is given the request will return
the total usage for the zones.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/stats.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`size` | The amount of bytes transferred |
`hit` | The number of times files were requested |
`noncache_hit` | The number of times a requested file was not in cache |
`cache_hit` | The number of times a requested file was already cached |
`timestamp` | The timestamp for the corresponding {report_type}. |


## List Stats per Zone

Gets the {zone_id} usage statistics optionally broken up by
{report_type}. If no {report_type} is given the request will return
the total usage for the zones.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/stats.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`size` | The amount of bytes transferred |
`hit` | The number of times files were requested |
`noncache_hit` | The number of times a requested file was not in cache |
`cache_hit` | The number of times a requested file was already cached |
`timestamp` | The timestamp for the corresponding {report_type}. |




---

# Reports by Location API

## List Nodes

Gets a list of all active nodes (locations)

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/nodes.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Node Id |
`name` | Node 3 letter code |
`description` | Full node name |


## List Nodes by Zone

Gets a list of all active nodes (locations) specified by the
{zone_id} parameter

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/nodes.json</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Node Id |
`name` | Node 3 letter code |
`description` | Full node name |


## List Zone Node Stats by Report Type

Get usage statistics broken up by nodes and optionally
{report_type}. If no {report_type} is given the request will return
the total usage broken up by node.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/nodes.json/stats/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-31) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-31) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`pop_id` | Node Id |
`pop_name` | Node 3 letter code. Only returned when {report_type} is notempty. |
`pop_description` | Full node name. Only returned when {report_type} is notempty. |
`size` | The amount of bytes transferred |
`hit` | The number of times files were requested |
`noncache_hit` | The number of times a requested file was not in cache |
`cache_hit` | The number of times a requested file was already cached |
`timestamp` | A timestamp corresponding to {report_type}. Only returned when{report_type} is not empty. |


## List Node Stats by Zone and Report Type

Get usage statistics for a particular {zone_id} broken up by
nodes and optionally {report_type}. If no {report_type} is given
the request will return the total usage broken up by node.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/nodes.json/stats/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`pop_id` | Node Id |
`pop_name` | Node 3 letter code. Only returned when {report_type} is notempty. |
`pop_description` | Full node name. Only returned when {report_type} is notempty. |
`size` | The amount of bytes transferred |
`hit` | The number of times files were requested |
`noncache_hit` | The number of times a requested file was not in cache |
`cache_hit` | The number of times a requested file was already cached |
`timestamp` | A timestamp corresponding to {report_type}. Only returned when{report_type} is not empty. |


## Get Zone Node

Gets the node information for the specified {node_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/nodes.json/{node_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Node Id |
`name` | Node 3 letter code |
`description` | Full node name |


## Get Node by Zone

Gets the node information for the specified {node_id} and
{zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/nodes.json/{node_id}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`id` | Node Id |
`name` | Node 3 letter code |
`description` | Full node name |


## Get Zone Node Stats by Report Type

Get usage statistics for a particular {node_id} optionally
broken up by {report_type}. If no {report_type} is given the
request will return the total usage for the node.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/nodes.json/{node_id}/stats/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date. |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date. |


### Response Parameters

Parameter | Description |
--- | --- | ---
`size` | The amount of bytes transferred |
`hit` | The number of times files were requested |
`noncache_hit` | The number of times a requested file was not in cache |
`cache_hit` | The number of times a requested file was already cached |
`timestamp` | A timestamp corresponding to {report_type}. Only returned when{report_type} is not empty. |


## Get Node Stats by Zone and Report Type

Get usage statistics for a particular {node_id} and {zone_id},
optionally broken up by {report_type}. If no {report_type} is given
the request will return the total usage for the node.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/nodes.json/{node_id}/stats/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`size` | The amount of bytes transferred |
`hit` | The number of times files were requested |
`noncache_hit` | The number of times a requested file was not in cache |
`cache_hit` | The number of times a requested file was already cached |
`timestamp` | A timestamp corresponding to {report_type}. Only returned when{report_type} is not empty. |




---

# Reports by Popular Files API

## List Popular Files

Gets the most popularly requested files for your account,
grouped into daily statistics

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/popularfiles.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01). | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01). | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the popular file |
`uri` | The URI for the requested popular file |
`hit` | The number of times the file was requested |
`size` | The amount of bytes transferred for the given file |
`vhost` | The CDN URL for the corresponding zone |
`timestamp` | The amount of bytes transferred |


## List Popular Files

Gets the most popularly requested files for your account,
filtered by {zone_type} and grouped into daily statistics

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_type}/popularfiles.json</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the popular file |
`uri` | The URI for the requested popular file |
`hit` | The number of times the file was requested |
`size` | The amount of bytes transferred for the given file |
`vhost` | The CDN URL for the corresponding zone |
`timestamp` | The amount of bytes transferred |




---

# Reports by Status Codes API

## List Status Code Responses

Gets HTTP status code response statistics for your account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/statuscodes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`status_code` | The HTTP status code for the response |
`hit` | The number of responses with this status code |
`definition` | The definition for the status code |


## List Status Code Responses by Zone Id

Gets HTTP status code response statistics for a specific
{zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/statuscodes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`status_code` | The HTTP status code for the response |
`hit` | The number of responses with this status code |
`definition` | The definition for the status code |


## List Status Codes by Zone Type

Gets HTTP status code response statistics for a specific
{zone_type}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_type}/statuscodes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`status_code` | The HTTP status code for the response |
`hit` | The number of responses with this status code |
`definition` | The definition for the status code |


## List Status Codes by Zone Id

Gets HTTP status code response statistics for a specific
{zone_type} and {zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_type}/{zone_id}/statuscodes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`status_code` | The HTTP status code for the response |
`hit` | The number of responses with this status code |
`definition` | The definition for the status code |




---

# Reports by File Types API

## List File Types

Gets file type statistics for your account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/filetypes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`file_type` | The file type requested |
`hit` | The number of times a file of this type has been requested |


## List File Types by Zone Id

Gets file type statistics for a specific {zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/filetypes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d e.g. 2012-01-01 | Start date |
`date_to` | now() | Y-m-d e.g. 2012-01-01 | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`file_type` | The file type requested |
`hit` | The number of times a file of this type has been requested |


## List File Types by Zone Type

Gets file type statistics for a specific {zone_type}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_type}/filetypes.json/{report_type}</span></div>
</div>

### Response Parameters

Parameter | Description |
--- | --- | ---
`file_type` | The file type requested |
`hit` | The number of times a file of this type has been requested |


## List File Types by Zone Id

Gets file type statistics for a specific {zone_type} and
{zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_type}/{zone_id}/filetypes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`file_type` | The file type requested |
`hit` | The number of times a file of this type has been requested |




---

# Reports by File Size Ranges API

## List File Sizes

Gets request statistics for your account based on file size
ranges

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/filesizes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`le_10k_hits` | The number of requests for files &lt;= 10KB |
`le_50k_hits` | The number of requests for files &lt;= 50KB |
`le_100k_hits` | The number of requests for files &lt;= 100KB |
`le_500k_hits` | The number of requests for files &lt;= 500KB |
`le_1m_hits` | The number of requests for files &lt;= 1MB |
`le_10m_hits` | The number of requests for files &lt;= 10MB |
`le_100m_hits` | The number of requests for files &lt;= 100MB |
`gt_100m_hits` | The number of requests for files &gt; 100MB |


## List File Sizes by Zone Id

Gets request statistics for the specified {zone_id} based on
file size ranges

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/filesizes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d e.g. 2012-01-01 | Start date |
`date_to` | now() | Y-m-d e.g. 2012-01-01 | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`le_10k_hits` | The number of requests for files &lt;= 10KB |
`le_50k_hits` | The number of requests for files &lt;= 50KB |
`le_100k_hits` | The number of requests for files &lt;= 100KB |
`le_500k_hits` | The number of requests for files &lt;= 500KB |
`le_1m_hits` | The number of requests for files &lt;= 1MB |
`le_10m_hits` | The number of requests for files &lt;= 10MB |
`le_100m_hits` | The number of requests for files &lt;= 100MB |
`gt_100m_hits` | The number of requests for files &gt; 100MB |


## List File Sizes by Zone Type

Gets request statistics for the specified {zone_type} based on
file size ranges

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_type}/filesizes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d e.g. 2012-01-01 | Start date |
`date_to` | now() | Y-m-d e.g. 2012-01-01 | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`le_10k_hits` | The number of requests for files &lt;= 10KB |
`le_50k_hits` | The number of requests for files &lt;= 50KB |
`le_100k_hits` | The number of requests for files &lt;= 100KB |
`le_500k_hits` | The number of requests for files &lt;= 500KB |
`le_1m_hits` | The number of requests for files &lt;= 1MB |
`le_10m_hits` | The number of requests for files &lt;= 10MB |
`le_100m_hits` | The number of requests for files &lt;= 100MB |
`gt_100m_hits` | The number of requests for files &gt; 100MB |


## List File Sizes by Zone Id

Gets request statistics for the specified {zone_type} and
{zone_id} based on file size ranges

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_type}/{zone_id}/filesizes.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`le_10k_hits` | The number of requests for files &lt;= 10KB |
`le_50k_hits` | The number of requests for files &lt;= 50KB |
`le_100k_hits` | The number of requests for files &lt;= 100KB |
`le_500k_hits` | The number of requests for files &lt;= 500KB |
`le_1m_hits` | The number of requests for files &lt;= 1MB |
`le_10m_hits` | The number of requests for files &lt;= 10MB |
`le_100m_hits` | The number of requests for files &lt;= 100MB |
`gt_100m_hits` | The number of requests for files &gt; 100MB |




---

# Reports By Directory API

## List Stats By Directory

Gets usage statistics by directory for your account. (This
report has to be enabled by Sales).

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/statsbydir.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the top level directory |
`dir` | The name of the directory |
`hit` | The number of requests made to files within this directory |
`size` | The amount of bytes transferred from within this directory |


## List Stats By Directory and Zone Id

Gets usage statistics by directory for the specified {zone_id}.
(This report has to be enabled by Sales).

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/{zone_id}/statsbydir.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the top level directory |
`dir` | The name of the directory |
`hit` | The number of requests made to files within this directory |
`size` | The amount of bytes transferred from within this directory |




---

# Reports By File Name API

## List Stats By File Name

Gets usage statistics by file name for your account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/clients/{client_id}/reports/statsbyfilename.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |
`file_names` | A JSON Encoded file names list |
`filter` | Matching expression for file names |
`sort_by` | Field to sort by |
`sort_dir` | Directory to sort files by |
`page_size` | - | The number of records returned in the result set |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the top level directory |
`hit` | The number of requests made to files within this directory |
`size` | The amount of bytes transferred from within this directory |
`200` | The amount of 200 hits |
`206` | The amount of 206 hits |
`2xx` | The amount of 2xx hits |
`3xx` | The amount of 3xx hits |
`404` | The amount of 404 hits |
`4xx` | The amount of 4xx hits |
`5xx` | The amount of 206 hits |
`5xx` | The amount of 206 hits |
`timestampf` | Timestamp |


## List Stats By File Name and Zone Id

Gets usage statistics by file name for the specified
{zone_id}

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/clients/{client_id}/reports/{zone_id}/statsbyfilename.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |
`file_names` | A JSON Encoded file names list |
`filter` | Matching expression for file names |
`sort_by` | Field to sort by |
`sort_dir` | Directory to sort files by |
`page_size` | - | The number of records returned in the result set |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the top level directory |
`hit` | The number of requests made to files within this directory |
`size` | The amount of bytes transferred from within this directory |
`200` | The amount of 200 hits |
`206` | The amount of 206 hits |
`2xx` | The amount of 2xx hits |
`3xx` | The amount of 3xx hits |
`404` | The amount of 404 hits |
`4xx` | The amount of 4xx hits |
`5xx` | The amount of 206 hits |
`5xx` | The amount of 206 hits |
`timestampf` | Timestamp |




---

# Reports By Custom Domain API

## List Stats By Directory

Gets usage statistics by custom domain for your account. (This
report has to be enabled by Sales).

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/clients/{client_id}/reports/statsbycustomdomain.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the custom domain |
`custom_domain_id` | The ID of your custom domain |
`hit` | The number of requests made to this custom domain |
`size` | The amount of bytes transferred to/from this custom domain |


## List Stats By Custom Domain and Zone Id

Gets usage statistics by custom domain for the specified
{zone_id}. (This report has to be enabled by Sales).

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/clients/{client_id}/reports/{zone_id}/statsbycustomdomain.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | now() - 1 month | Y-m-d (e.g. 2012-01-01) | Start date |
`date_to` | now() | Y-m-d (e.g. 2012-01-01) | End date |


### Response Parameters

Parameter | Description |
--- | --- | ---
`bucket_id` | The Zone ID for the top level directory |
`custom_domain_id` | The ID of the Custom Domain |
`hit` | The number of requests made to this custom domain |
`size` | The amount of bytes transferred to/from this custom domain |




---

# Reports for Live Zones API

## List Connection Stats

Gets zone stats in hourly, daily, or monthly summaries

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/reports/live/connectionstats.json/{report_type}</span></div>
</div>

### Accepted Request Parameters

Parameter | Default Value | Validation | Description |
--- | --- | --- | --- | ---
`date_from` | - | Y-m-d e.g. 2012-01-01 | Start date |
`date_to` | - | Y-m-d e.g. 2012-01-01 | End date |


---

[@niftylettuce](https://github.com/niftylettuce) was here.
