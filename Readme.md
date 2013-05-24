
# NetDNA API Docs

[NetDNA](http://www.netdna.com) is a content delivery network ("CDN") provider.

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
  - Node (NPM) <https://github.com/niftylettuce/node-netdna>
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

Reference to [History.md](https://github.com/netdna/netdna-apidocs/blob/master/History.md#changelog) for a complete log of API changes and improvements.

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

### Code Samples

<ul class="nav nav-tabs" id="myTab1">
  <li class="active"><a href="#ruby1" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python1" data-toggle='tab'>Python</a></li>
  <li><a href="#php1" data-toggle='tab'>PHP</a></li>
  <li><a href="#node1" data-toggle='tab'>Node</a></li>
  <li><a href="#response1" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby1">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python1">
		<pre>
api.get("/account.json")</pre>
	</div>
  <div class="tab-pane" id="php1">
  	<pre>
$api->get('/account.json');</pre>
  </div>
  <div class="tab-pane" id="node1">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
netdna.get('/account.json', callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response1">
		<pre>
{
    "code": 200,
    "data": {
        "account": {
            "alias": "aliasname",
            "date_created": "2013-05-15 17:32:30",
            "date_updated": "2013-05-15 19:43:36",
            "edgerules_credits": "0",
            "flex_credits": "-1",
            "id": "#####",
            "name": "NetDNA sampleCode",
            "secure_token_pull_credits": "0",
            "server_id": "18",
            "ssl_credits": "-1",
            "status": "2",
            "storage_quota": "107374182400",
            "storage_server_id": "11",
            "zone_credits": "-1"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab1 a:last').tab('show');
  })
</script>

---

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


### Code Samples

<ul class="nav nav-tabs" id="myTab2">
  <li class="active"><a href="#ruby2" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python2" data-toggle='tab'>Python</a></li>
  <li><a href="#php2" data-toggle='tab'>PHP</a></li>
  <li><a href="#node2" data-toggle='tab'>Node</a></li>
  <li><a href="#response2" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby2">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python2">
		<pre>
params={"name": "Monty"}
	api.put('/account.json',params=params)</pre>
	</div>
  <div class="tab-pane" id="php2">
  	<pre>
$api->put('/account.json',array("name"=>"newName"));</pre>
  </div>
  <div class="tab-pane" id="node2">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
netdna.put('/account.json', { name: 'newName' }, callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response2">
		<pre>
{
    "code": 200,
    "data": {
        "account": {
            "alias": "aliasname",
            "date_created": "2013-05-15 17:32:30",
            "date_updated": "2013-05-23 17:58:27",
            "edgerules_credits": "0",
            "flex_credits": "-1",
            "id": "#####",
            "name": "newName",
            "secure_token_pull_credits": "0",
            "server_id": "18",
            "ssl_credits": "-1",
            "status": "2",
            "storage_quota": "107374182400",
            "storage_server_id": "11",
            "zone_credits": "-1"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab2 a:last').tab('show');
  })
</script>

---

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


### Code Samples

<ul class="nav nav-tabs" id="myTab3">
  <li class="active"><a href="#ruby3" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python3" data-toggle='tab'>Python</a></li>
  <li><a href="#php3" data-toggle='tab'>PHP</a></li>
  <li><a href="#node3" data-toggle='tab'>Node</a></li>
  <li><a href="#response3" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby3">
		<pre>
		</pre>
  </div>
  <div class="tab-pane" id="python3">
		<pre>
api.get('/account.json/address')</pre>
	</div>
  <div class="tab-pane" id="php3">
  	<pre>
$api->get('/account.json/address')</pre>
  </div>
  <div class="tab-pane" id="node3">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
netdna.get('/account.json/address', callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response3">
		<pre>
{
    "code": 200,
    "data": {
        "address": {
            "city": "los angeles",
            "country": "US",
            "date_created": "0000-00-00 00:00:00",
            "date_updated": "2013-05-15 19:54:40",
            "id": "#####",
            "state": "CA",
            "street1": "123 Main Street",
            "street2": "apt 42",
            "zip": "90068"
        }
    }
}
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab3 a:last').tab('show');
  })
</script>

---

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


### Code Samples

<ul class="nav nav-tabs" id="myTab4">
  <li class="active"><a href="#ruby4" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python4" data-toggle='tab'>Python</a></li>
  <li><a href="#php4" data-toggle='tab'>PHP</a></li>
  <li><a href="#node4" data-toggle='tab'>Node</a></li>
  <li><a href="#response4" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby4">
		<pre>
		</pre>
  </div>
  <div class="tab-pane" id="python4">
		<pre>
params = {"street1": "1234 Main Street", "street2": "apt 42", "state": "CA"}
api.put('/account.json/address',params=params)</pre>
	</div>
  <div class="tab-pane" id="php4">
  	<pre>
$params = array("street1"=>"123 Main Street", "street2"=>"apt 42", "state"=>"CA");
$api->put('/account.json/address',$params);</pre>
  </div>
  <div class="tab-pane" id="node4">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
netdna.put('/account.json/address', { street1: '123 Main Street', street2: 'apt 42', state: 'CA' }, callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response4">
		<pre>
{
    "code": 200,
    "data": {
        "address": {
            "city": "los angeles",
            "country": "US",
            "date_created": "0000-00-00 00:00:00",
            "date_updated": "2013-05-23 18:01:29",
            "id": "#####",
            "state": "CA",
            "street1": "1234 Main Street",
            "street2": "apt 42",
            "zip": "90068"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab4 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab5">
  <li class="active"><a href="#ruby5" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python5" data-toggle='tab'>Python</a></li>
  <li><a href="#php5" data-toggle='tab'>PHP</a></li>
  <li><a href="#node5" data-toggle='tab'>Node</a></li>
  <li><a href="#response5" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby5">
		<pre>
		</pre>
  </div>
  <div class="tab-pane" id="python5">
		<pre>
api.get('/users.json')</pre>
	</div>
  <div class="tab-pane" id="php5">
  	<pre>
$api->get('/users.json');</pre>
  </div>
  <div class="tab-pane" id="node5">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
netdna.get('/users.json', callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response5">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 4,
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "total": 4,
        "users": [
            {
                "brand_id": "1",
                "date_created": "2013-05-15 17:32:30",
                "date_last_login": "2013-05-23 17:54:18",
                "date_updated": "2013-05-15 17:33:09",
                "default_company_id": "#####",
                "email": "name@domain.com",
                "firstname": "Given",
                "id": "33706",
                "ip_last_login": "12.13.90.183",
                "isadmin": "0",
                "isdisabled": "0",
                "lastname": "Family",
                "phone": "3235551400",
                "roles": [
                    "User",
                    "Account Owner"
                ],
                "timezone": "Europe/London"
            },
            {
                "brand_id": "1",
                "date_created": "2013-05-15 20:16:34",
                "date_last_login": null,
                "date_updated": "0000-00-00 00:00:00",
                "default_company_id": "19538",
                "email": "caphammer1@hamcave.com",
                "firstname": "Captain",
                "id": "33714",
                "ip_last_login": null,
                "isadmin": "0",
                "isdisabled": "0",
                "lastname": "Hammer",
                "phone": null,
                "roles": [
                    "User"
                ],
                "timezone": "Europe/London"
            },
            {
                "brand_id": "1",
                "date_created": "2013-05-15 20:20:03",
                "date_last_login": null,
                "date_updated": "2013-05-15 20:31:05",
                "default_company_id": "19538",
                "email": "drhorrible3@ele.net",
                "firstname": "Billy",
                "id": "33716",
                "ip_last_login": null,
                "isadmin": "0",
                "isdisabled": "0",
                "lastname": "Horrible",
                "phone": null,
                "roles": [
                    "User"
                ],
                "timezone": "Europe/London"
            }
        ]
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab5 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab6">
  <li class="active"><a href="#ruby6" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python6" data-toggle='tab'>Python</a></li>
  <li><a href="#php6" data-toggle='tab'>PHP</a></li>
  <li><a href="#node6" data-toggle='tab'>Node</a></li>
  <li><a href="#response6" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby6">
		<pre>
		</pre>
  </div>
  <div class="tab-pane" id="python6">
		<pre>
params={'email':'name43@domain.com','password':'password','firstname':'Given','lastname':'Family'}
api.post('/users.json',data=params )</pre>
	</div>
  <div class="tab-pane" id="php6">
  	<pre>
$params = array("email"=>"name@domain.com","password"=>"password","firstname"=>"Given","lastname"=>"Family");
$api->post('/users.json',$params );</pre>
  </div>
  <div class="tab-pane" id="node6">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
netdna.post('/users.json', { email: 'name@domain.com', password: 'password', firstname: 'Given', lastname: 'Family' }, callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response6">
		<pre>
{
    "code": 201,
    "data": {
        "user": {
            "brand_id": null,
            "date_created": "2013-05-23 18:22:11",
            "date_last_login": null,
            "date_updated": null,
            "default_company_id": "19538",
            "email": "name@domain.com",
            "firstname": "Given",
            "id": 33941,
            "ip_last_login": null,
            "isadmin": 0,
            "isdisabled": 0,
            "lastname": "Family",
            "phone": null,
            "roles": [
                "User"
            ],
            "timezone": "America/Los_Angeles"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab6 a:last').tab('show');
  })
</script>

---

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


### Code Samples

<ul class="nav nav-tabs" id="myTab7">
  <li class="active"><a href="#ruby7" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python7" data-toggle='tab'>Python</a></li>
  <li><a href="#php7" data-toggle='tab'>PHP</a></li>
  <li><a href="#node7" data-toggle='tab'>Node</a></li>
  <li><a href="#response7" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby7">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python7">
		<pre>
id = '33706'
api.get('/users.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php7">
  	<pre>
$id = '33941';
$api->get('/users.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node7">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
var id = '33941'
netdna.get('/users.json/' + id, callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response7">
		<pre>
{
    "code": 200,
    "data": {
        "user": {
            "brand_id": "1",
            "date_created": "2013-05-23 18:22:11",
            "date_last_login": null,
            "date_updated": "0000-00-00 00:00:00",
            "default_company_id": "19538",
            "email": "name@domain.com",
            "firstname": "Given",
            "id": "33941",
            "ip_last_login": null,
            "isadmin": "0",
            "isdisabled": "0",
            "lastname": "Family",
            "phone": null,
            "roles": [
                "User"
            ],
            "timezone": "Europe/London"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab7 a:last').tab('show');
  })
</script>

---

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

### Code Samples

<ul class="nav nav-tabs" id="myTab8">
  <li class="active"><a href="#ruby8" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python8" data-toggle='tab'>Python</a></li>
  <li><a href="#php8" data-toggle='tab'>PHP</a></li>
  <li><a href="#node8" data-toggle='tab'>Node</a></li>
  <li><a href="#response8" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby8">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python8">
		<pre>
api.put('/users.json/'+id,params={'firstname': 'Verran'})</pre>
	</div>
  <div class="tab-pane" id="php8">
  	<pre>
$id = '33941';
$params =  array("firstname"=>"Billy");
$api->put('/users.json/'.$id,$params);</pre>
</div>
  <div class="tab-pane" id="node8">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
var id = '33941'
netdna.put('/users.json/' + id, { firstname: 'Billy' }, callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response8">
		<pre>
{
    "code": 200,
    "data": {
        "user": {
            "brand_id": "1",
            "date_created": "2013-05-23 18:22:11",
            "date_last_login": null,
            "date_updated": "2013-05-23 19:10:09",
            "default_company_id": "19538",
            "email": "name@domain.com",
            "firstname": "Billy",
            "id": "33941",
            "ip_last_login": null,
            "isadmin": "0",
            "isdisabled": "0",
            "lastname": "Family",
            "phone": null,
            "roles": [
                "User"
            ],
            "timezone": "Europe/London"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab8 a:last').tab('show');
  })
</script>

---


## Delete User

Deletes a user specified by the {user_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/users.json/{user_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab9">
  <li class="active"><a href="#ruby9" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python9" data-toggle='tab'>Python</a></li>
  <li><a href="#php9" data-toggle='tab'>PHP</a></li>
  <li><a href="#node9" data-toggle='tab'>Node</a></li>
  <li><a href="#response9" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby9">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python9">
		<pre>
id = '33706'
api.delete('/users.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php9">
  	<pre>
$id = '33715';
$api->delete('/users.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node9">
	<pre>
var netdna = require('netdna')({
	companyAlias: 'alias'
	, consumerKey: 'key'
	, consumerSecret: 'secret'
})
var id = '33715'
netdna.del('/users.json/' + id, callback)
function callback(err, response) {
  if (err) return console.log(err)
  console.log(response)
}</pre>
  </div>
  <div class="tab-pane" id="response9">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab9 a:last').tab('show');
  })
</script>

---
---

# Zones API

## List Zones

Returns a list of all zones on the specified account

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones.json</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab10">
  <li class="active"><a href="#ruby10" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python10" data-toggle='tab'>Python</a></li>
  <li><a href="#php10" data-toggle='tab'>PHP</a></li>
  <li><a href="#node10" data-toggle='tab'>Node</a></li>
  <li><a href="#response10" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby10">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python10">
		<pre>
api.get('/zones.json')</pre>
	</div>
  <div class="tab-pane" id="php10">
  	<pre>
$api->get('/zones.json');</pre>
  </div>
  <div class="tab-pane" id="node10">
	<pre>
netdna.get('/zones.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response10">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 2,
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "total": 2,
        "zones": [
            {
                "cdn_url": "cdn.somedomain.com",
                "creation_date": "2013-05-15 20:45:44",
                "id": "#####",
                "inactive": "0",
                "label": "personal",
                "locked": "0",
                "name": "zoneName",
                "suspend": "0",
                "tmp_url": "zone.alias.netdna-cdn.com",
                "type": "2"
            },
            {
                "cdn_url": "newlivezone.somedomain.netdna-cdn.com",
                "creation_date": "2013-05-16 16:23:49",
                "id": "#####",
                "inactive": "0",
                "label": null,
                "locked": "0",
                "name": "newlivezone",
                "suspend": "0",
                "tmp_url": "newlivezone.alias.netdna-cdn.com",
                "type": "5"
            }
        ]
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab10 a:last').tab('show');
  })
</script>

---

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


### Code Samples

<ul class="nav nav-tabs" id="myTab11">
  <li class="active"><a href="#ruby11" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python11" data-toggle='tab'>Python</a></li>
  <li><a href="#php11" data-toggle='tab'>PHP</a></li>
  <li><a href="#node11" data-toggle='tab'>Node</a></li>
  <li><a href="#response11" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby11">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python11">
		<pre>
api.get('/zones.json/summary')</pre>
	</div>
  <div class="tab-pane" id="php11">
  	<pre>
$api->get('/zones.json/summary');</pre>
  </div>
  <div class="tab-pane" id="node11">
	<pre>
netdna.get('/zones.json/summary', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response11">
		<pre>
{
    "code": 200,
    "data": {
        "summary": {
            "live": 1,
            "pull": 1,
            "push": 1,
            "vod": 1
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab11 a:last').tab('show');
  })
</script>

---

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



### Code Samples

<ul class="nav nav-tabs" id="myTab12">
  <li class="active"><a href="#ruby12" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python12" data-toggle='tab'>Python</a></li>
  <li><a href="#php12" data-toggle='tab'>PHP</a></li>
  <li><a href="#node12" data-toggle='tab'>Node</a></li>
  <li><a href="#response12" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby12">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python12">
		<pre>
api.get('/zones.json/count')</pre>
	</div>
  <div class="tab-pane" id="php12">
  	<pre>
$api->get('/zones.json/count');</pre>
  </div>
  <div class="tab-pane" id="node12">
	<pre>
netdna.get('/zones.json/count', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response12">
		<pre>
{"code":200,"data":
	{
		"count":"4"
	}
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab12 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab13">
  <li class="active"><a href="#ruby13" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python13" data-toggle='tab'>Python</a></li>
  <li><a href="#php13" data-toggle='tab'>PHP</a></li>
  <li><a href="#node13" data-toggle='tab'>Node</a></li>
  <li><a href="#response13" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby13">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python13">
		<pre>
api.get('/zones/pull.json')</pre>
	</div>
  <div class="tab-pane" id="php13">
  	<pre>
$api->get('/zones/pull.json');</pre>
  </div>
  <div class="tab-pane" id="node13">
	<pre>
netdna.get('/zones/pull.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response13">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 3,
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "pullzones": [
            {
                "backend_compress": "0",
                "cache_valid": "1d",
                "canonical_link_headers": "0",
                "cdn_url": "cdn.somedomain.com",
                "compress": "1",
                "content_disposition": "0",
                "creation_date": "2013-05-15 20:45:44",
                "disallow_robots": "0",
                "disallow_robots_txt": null,
                "dns_check": "1",
                "expires": null,
                "hide_setcookie_header": "0",
                "id": "96061",
                "ignore_cache_control": "0",
                "ignore_setcookie_header": "0",
                "inactive": "0",
                "ip": "205.134.255.49",
                "label": "personal",
                "locked": "0",
                "name": "somedomain",
                "port": "80",
                "proxy_cache_lock": "0",
                "pseudo_streaming": "0",
                "queries": "1",
                "server_id": "18",
                "set_host_header": null,
                "sslshared": "0",
                "suspend": "0",
                "tmp_url": "somedomain.alias.netdna-cdn.com",
                "type": "2",
                "upstream_enabled": "0",
                "url": "http://somedomain.net",
                "use_stale": "0",
                "valid_referers": null
            },
            <...>,
            {
                "backend_compress": "0",
                "cache_valid": "1d",
                "canonical_link_headers": "0",
                "cdn_url": "newpullzone3.alias.netdna-cdn.com",
                "compress": "0",
                "content_disposition": "0",
                "creation_date": "2013-05-24 16:18:19",
                "disallow_robots": "0",
                "disallow_robots_txt": null,
                "dns_check": "1",
                "expires": null,
                "hide_setcookie_header": "0",
                "id": "97312",
                "ignore_cache_control": "0",
                "ignore_setcookie_header": "0",
                "inactive": "0",
                "ip": "205.134.255.49",
                "label": null,
                "locked": "0",
                "name": "newpullzone3",
                "port": "80",
                "proxy_cache_lock": "0",
                "pseudo_streaming": "0",
                "queries": "1",
                "server_id": "18",
                "set_host_header": null,
                "sslshared": "0",
                "suspend": "0",
                "tmp_url": "newpullzone3.alias.netdna-cdn.com",
                "type": "2",
                "upstream_enabled": "0",
                "url": "http://somedomain.net",
                "use_stale": "0",
                "valid_referers": null
            }
        ],
        "total": 3
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab13 a:last').tab('show');
  })
</script>

---

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

### Code Samples

<ul class="nav nav-tabs" id="myTab14">
  <li class="active"><a href="#ruby14" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python14" data-toggle='tab'>Python</a></li>
  <li><a href="#php14" data-toggle='tab'>PHP</a></li>
  <li><a href="#node14" data-toggle='tab'>Node</a></li>
  <li><a href="#response14" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby14">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python14">
		<pre>
params = {"name":"newPullZone5","url":"http://somedomain.net"}
api.post('/zones/pull.json',data=params)</pre>
	</div>
  <div class="tab-pane" id="php14">
  	<pre>
$params =  array("name"=>"newPullZone2","url"=>"http://somedomain.net");
$api->post('/zones/pull.json',$params);</pre>
  </div>
  <div class="tab-pane" id="node14">
	<pre>
netdna.post('/zones/pull.json', { name: 'newPullZone2', url: 'http://somedomain.net' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response14">
		<pre>
{
    "code": 201,
    "data": {
        "pullzone": {
            "backend_compress": 0,
            "cache_valid": "1d",
            "canonical_link_headers": 1,
            "cdn_url": "newpullzone3.alias.netdna-cdn.com",
            "compress": 0,
            "content_disposition": 0,
            "creation_date": "2013-05-24 16:18:19",
            "disallow_robots": 0,
            "disallow_robots_txt": null,
            "dns_check": 0,
            "expires": null,
            "hide_setcookie_header": 0,
            "id": 97312,
            "ignore_cache_control": 0,
            "ignore_setcookie_header": 0,
            "inactive": 0,
            "ip": "205.134.255.49",
            "label": null,
            "locked": 0,
            "name": "newpullzone3",
            "port": 80,
            "proxy_cache_lock": 0,
            "pseudo_streaming": 0,
            "queries": "1",
            "server_id": "18",
            "set_host_header": 1,
            "sslshared": null,
            "suspend": 0,
            "tmp_url": "newpullzone3.alias.netdna-cdn.com",
            "type": 2,
            "upstream_enabled": 0,
            "url": "http://somedomain.net",
            "use_stale": 0,
            "valid_referers": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab14 a:last').tab('show');
  })
</script>

---

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

### Code Samples

<ul class="nav nav-tabs" id="myTab15">
  <li class="active"><a href="#ruby15" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python15" data-toggle='tab'>Python</a></li>
  <li><a href="#php15" data-toggle='tab'>PHP</a></li>
  <li><a href="#node15" data-toggle='tab'>Node</a></li>
  <li><a href="#response15" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby15">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python15">
		<pre>
api.get('/zones/pull.json/count')</pre>
	</div>
  <div class="tab-pane" id="php15">
  	<pre>
$api->get('/zones/pull.json/count');</pre>
  </div>
  <div class="tab-pane" id="node15">
	<pre>
netdna.get('/zones/pull.json/count', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response15">
		<pre>
{"code":200,"data":
	{
    "count": "3"
	}
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab15 a:last').tab('show');
  })
</script>

---

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
`sslshared` | Enable Shared SSL. This feature allows you use your zone inHTTPS mode. You don't need your own SSL certificate, our servernetdna-ssl.com will be used. |
`suspend` | Flag denoting if the zone has been suspended |
`locked` | Flag denoting if the zone has been locked |
`inactive` | Flag denoting if the zone has been deleted |
`creation_date` | Date Created |

### Code Samples

<ul class="nav nav-tabs" id="myTab16">
  <li class="active"><a href="#ruby16" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python16" data-toggle='tab'>Python</a></li>
  <li><a href="#php16" data-toggle='tab'>PHP</a></li>
  <li><a href="#node16" data-toggle='tab'>Node</a></li>
  <li><a href="#response16" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby16">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python16">
		<pre>
api.get('/zones/pull.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php16">
  	<pre>
$id = '96076';
$api->get('/zones/pull.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node16">
	<pre>
var id = '96076'
netdna.get('/zones/pull.json' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response16">
		<pre>
{
    "code": 200,
    "data": {
        "pullzone": {
            "backend_compress": "0",
            "cache_valid": "1d",
            "canonical_link_headers": "0",
            "cdn_url": "cdn.somenewdomain.com",
            "compress": "0",
            "content_disposition": "0",
            "creation_date": "2013-05-23 19:38:30",
            "disallow_robots": "0",
            "disallow_robots_txt": null,
            "dns_check": "1",
            "expires": null,
            "hide_setcookie_header": "0",
            "id": "97167",
            "ignore_cache_control": "0",
            "ignore_setcookie_header": "0",
            "inactive": "0",
            "ip": "205.134.255.49",
            "label": "Some other description",
            "locked": "0",
            "name": "newpullzone2",
            "port": "80",
            "proxy_cache_lock": "0",
            "pseudo_streaming": "0",
            "queries": "1",
            "server_id": "18",
            "set_host_header": null,
            "sslshared": "0",
            "suspend": "0",
            "tmp_url": "newpullzone2.alias.netdna-cdn.com",
            "type": "2",
            "upstream_enabled": "0",
            "url": "http://somedomain.net",
            "use_stale": "0",
            "valid_referers": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab16 a:last').tab('show');
  })
</script>

---

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
`compress` | 0 | only 0 or 1 accepted | On the fly compression of your files served from our edges.Enable GZip compression for the following file types: text/plain,text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`backend_compress` | 0 | only 0 or 1 accepted | Allow us to cache compressed versions of your files from theorigin. Enable GZip compression for the following file types:text/plain, text/html, text/javascript, text/css, text/xml,application/javascript, application/x-javascript, application/xml,text/x-component, application/json, application/xhtml+xml,application/rss+xml, application/atom+xml, app/vnd.ms-fontobject,image/svg+xml, application/x-font-ttf, font/opentype |
`queries` | 0 | only 0 or 1 accepted | Treat Query Strings as a separate cacheable item |
`set_host_header` | - | length: 4-100 chars; only valid URLs accepted | The URL to send as the Host in all HTTP Response Headers |
`cache_valid` | - | length: 1-30 chars; must be a number followed by one of s, m,h, d, M, or Y | Ignore the origin Cache-Control Header and set every request tohave a Max-Age of 1d, 7d, 1M or 12M |
`ignore_setcookie_header` | 0 | only 0 or 1 accepted | Ignore any cookies set by the origin in order to make thecontent consistently cacheable |
`ignore_cache_control` | 0 | only 0 or 1 accepted | Ignore any max age values set by the origin and use the CDN setvalue instead |
`use_stale` | 0 | only 0 or 1 accepted | Serve expired content while fetching new content. This willalso cause the CDN to serve expired content in cases where theorigin is down or the file is not found |
`proxy_cache_lock` | 0 | only 0 or 1 accepted | When multiple requests for an uncached file are received, theywill wait until the first response is received rather than sendingeach request back to the origin |
`label` | - | length: 1-255 chars | Something that describes your zone |
`valid_referers` | - | length: 1-100 chars | List of domains for http referrer protection (separated byspace). Only the domains in the list will be treated as validreferrers |
`expires` | 1d | length: 1-32 chars | Set any request with a no "Cache-Control header" from theorigin to stay on the server. Possible values are 1d, 7d, 1M,12M |
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


### Code Samples

<ul class="nav nav-tabs" id="myTab17">
  <li class="active"><a href="#ruby17" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python17" data-toggle='tab'>Python</a></li>
  <li><a href="#php17" data-toggle='tab'>PHP</a></li>
  <li><a href="#node17" data-toggle='tab'>Node</a></li>
  <li><a href="#response17" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby17">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python17">
		<pre>
id = '97167'
params = {"label":"Some other description"}
api.put('/zones/pull.json/'+id,params=params)</pre>
	</div>
  <div class="tab-pane" id="php17">
  	<pre>
$id = '96167';
$params = array("label"=>"Some other description");
$api->put('/zones/pull.json/'.$id, $params);</pre>
  </div>
  <div class="tab-pane" id="node17">
	<pre>
var id = '96167'
netdna.put('/zones/pull.json' + id, { label: 'Some other description' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response17">
		<pre>
{
    "code": 200,
    "data": {
        "pullzone": {
            "backend_compress": "0",
            "cache_valid": "1d",
            "canonical_link_headers": "0",
            "cdn_url": "cdn.somenewdomain.com",
            "compress": "0",
            "content_disposition": "0",
            "creation_date": "2013-05-23 19:38:30",
            "disallow_robots": "0",
            "disallow_robots_txt": null,
            "dns_check": "1",
            "expires": null,
            "hide_setcookie_header": "0",
            "id": "97167",
            "ignore_cache_control": "0",
            "ignore_setcookie_header": "0",
            "inactive": "0",
            "ip": "205.134.255.49",
            "label": "Some other description",
            "locked": "0",
            "name": "newpullzone2",
            "port": "80",
            "proxy_cache_lock": "0",
            "pseudo_streaming": "0",
            "queries": "1",
            "server_id": "18",
            "set_host_header": null,
            "sslshared": "0",
            "suspend": "0",
            "tmp_url": "newpullzone2.alias.netdna-cdn.com",
            "type": "2",
            "upstream_enabled": "0",
            "url": "http://somedomain.net",
            "use_stale": "0",
            "valid_referers": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab17 a:last').tab('show');
  })
</script>

---


## Delete Pull Zone

Deletes a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab18">
  <li class="active"><a href="#ruby18" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python18" data-toggle='tab'>Python</a></li>
  <li><a href="#php18" data-toggle='tab'>PHP</a></li>
  <li><a href="#node18" data-toggle='tab'>Node</a></li>
  <li><a href="#response18" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby18">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python18">
		<pre>
id = '97167'
api.delete('/zones/pull.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php18">
  	<pre>
$id = '97167';
$api->delete('/zones/pull.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node18">
	<pre>
var id = '97167'
netdna.del('/zones/pull.json' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response18">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab18 a:last').tab('show');
  })
</script>

---


## Enable Pull Zone

Enables a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab19">
  <li class="active"><a href="#ruby19" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python19" data-toggle='tab'>Python</a></li>
  <li><a href="#php19" data-toggle='tab'>PHP</a></li>
  <li><a href="#node19" data-toggle='tab'>Node</a></li>
  <li><a href="#response19" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby19">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python19">
		<pre>
id = '97167'
api.enable('/zones/pull.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php19">
  	<pre>
$id = '97167';
$api->enable('/zones/pull.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node19">
	<pre>
var id = '97167'
netdna.enable('/zones/pull.json' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response19">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab19 a:last').tab('show');
  })
</script>

---


## Disable Pull Zone

Disables a pull zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull.json/{zone_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab20">
  <li class="active"><a href="#ruby20" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python20" data-toggle='tab'>Python</a></li>
  <li><a href="#php20" data-toggle='tab'>PHP</a></li>
  <li><a href="#node20" data-toggle='tab'>Node</a></li>
  <li><a href="#response20" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby20">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python20">
		<pre>
id = '97167'
api.disable('/zones/pull.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php20">
  	<pre>
$id = '97167';
$api->disable('/zones/pull.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node20">
	<pre>
var id = '97167'
netdna.disable('/zones/pull.json' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response20">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab20 a:last').tab('show');
  })
</script>

---


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

<ul class="nav nav-tabs" id="myTab21">
  <li class="active"><a href="#ruby21" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python21" data-toggle='tab'>Python</a></li>
  <li><a href="#php21" data-toggle='tab'>PHP</a></li>
  <li><a href="#node21" data-toggle='tab'>Node</a></li>
  <li><a href="#response21" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby21">
	<pre>
api.purge(zone_id)
api.purge(zone_id, '/some_file')
api.purge(zone_id, ['/some_file', '/another_file'])</pre>
  </div>
  <div class="tab-pane" id="python21">
	<pre>
id = '97167'
params = {"file":"/robots.txt"}
api.delete('/zones/pull.json/'+id+'/cache',data=params)</pre>
	</div>
  <div class="tab-pane" id="php21">
  	<pre>
$id = '97167';
$params = array('file' => '/robots.txt');
$api->delete('/zones/pull.json/'.$id.'/cache', $params);</pre>
  </div>
  <div class="tab-pane" id="node21">
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
  <div class="tab-pane" id="response21">
	<pre>
{
    "code": 200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab21 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab22">
  <li class="active"><a href="#ruby22" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python22" data-toggle='tab'>Python</a></li>
  <li><a href="#php22" data-toggle='tab'>PHP</a></li>
  <li><a href="#node22" data-toggle='tab'>Node</a></li>
  <li><a href="#response22" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby22">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python22">
		<pre>
id = '97167'
api.get('/zones/pull/'+id+'/customdomains.json')</pre>
	</div>
  <div class="tab-pane" id="php22">
  	<pre>
$id = '96061';
$api->get('/zones/pull/'.$id.'/customdomains.json');</pre>
  </div>
  <div class="tab-pane" id="node22">
	<pre>
var id = '96061'
netdna.get('/zones/pull/' + id + '/customdomains.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response22">
		<pre>
{
    "code": 200,
    "data": {
        "customdomains": [
            {
                "bucket_id": "97167",
                "custom_domain": "cdn.somenewdomain.com",
                "id": "79182",
                "type": null
            }
        ],
        "total": 1
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab22 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab23">
  <li class="active"><a href="#ruby23" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python23" data-toggle='tab'>Python</a></li>
  <li><a href="#php23" data-toggle='tab'>PHP</a></li>
  <li><a href="#node23" data-toggle='tab'>Node</a></li>
  <li><a href="#response23" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby23">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python23">
		<pre>
id = '97167'
params = {"custom_domain":"cdn.somedomain13.com"}
api.post('/zones/pull/'+id+'/customdomains.json', params)</pre>
	</div>
  <div class="tab-pane" id="php23">
  	<pre>
$id = '97167';
$params = array("custom_domain"=>"cdn.somedomain3.com");
$api->post('/zones/pull/'.$id.'/customdomains.json', $params);</pre>
  </div>
  <div class="tab-pane" id="node23">
	<pre>
var id = '96167'
netdna.post('/zones/pull/' + id + '/customdomains.json', { custom_domain: 'cdn.somedomain3.com' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response23">
		<pre>
{
    "code": 201,
    "data": {
        "customdomain": {
            "bucket_id": "97167",
            "custom_domain": "cdn.somedomain3.com",
            "id": 79282,
            "type": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab23 a:last').tab('show');
  })
</script>

---

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

### Code Samples

<ul class="nav nav-tabs" id="myTab24">
  <li class="active"><a href="#ruby24" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python24" data-toggle='tab'>Python</a></li>
  <li><a href="#php24" data-toggle='tab'>PHP</a></li>
  <li><a href="#node24" data-toggle='tab'>Node</a></li>
  <li><a href="#response24" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby24">
		<pre>
		</pre>
  </div>
  <div class="tab-pane" id="python24">
		<pre>
zoneId = '97167'
domainId = '79182'
api.get('/zones/pull/'+zoneId+'/customdomains.json/'+domainId)</pre>
	</div>
  <div class="tab-pane" id="php24">
  	<pre>
$zoneId = '97167';
$domainId = '79182';
$api->get('/zones/pull/'.$zoneId.'/customdomains.json/'.$domainId);</pre>
  </div>
  <div class="tab-pane" id="node24">
	<pre>
var id = '97167'
var domainId = '79182'
netdna.get('/zones/pull/' + id + '/customdomains.json/' + domainId, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response24">
		<pre>
{
    "code": 200,
    "data": {
        "customdomain": {
            "bucket_id": "97167",
            "custom_domain": "cdn.somenewdomain.com",
            "id": "79182",
            "type": null
        }
    }
}
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab24 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab25">
  <li class="active"><a href="#ruby25" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python25" data-toggle='tab'>Python</a></li>
  <li><a href="#php25" data-toggle='tab'>PHP</a></li>
  <li><a href="#node25" data-toggle='tab'>Node</a></li>
  <li><a href="#response25" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby25">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python25">
		<pre>
zoneId = '97167'
domainId = '79182'
params = {"custom_domain":"cdn.somenewdomain41.com"}
api.put('/zones/pull/'+zoneId+'/customdomains.json/'+domainId,params=params)</pre>
	</div>
  <div class="tab-pane" id="php25">
  	<pre>
$zoneId = '97167';
$domainId = '79182';
$params = array("custom_domain"=>"cdn.somenewdomain.com");
$response =  $api->put('/zones/pull/'.$zoneId.'/customdomains.json/'.$domainId, $params);</pre>
  </div>
  <div class="tab-pane" id="node25">
	<pre>
var zoneId = '97167'
var domainId = '79182'
netdna.put('/zones/pull/' + zoneId + '/customdomains.json/' + domainId, { custom_domain: 'cdn.somenewdomain.com' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response25">
		<pre>
{
    "code": 200,
    "data": {
        "customdomain": {
            "bucket_id": "97167",
            "custom_domain": "cdn.somenewdomain4.com",
            "id": "79182",
            "type": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab25 a:last').tab('show');
  })
</script>

---


## Delete Custom Domain

Deletes a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/pull/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab26">
  <li class="active"><a href="#ruby26" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python26" data-toggle='tab'>Python</a></li>
  <li><a href="#php26" data-toggle='tab'>PHP</a></li>
  <li><a href="#node26" data-toggle='tab'>Node</a></li>
  <li><a href="#response26" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby26">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python26">
		<pre>
zoneId = '97167'
domainId = '79182'
api.delete('/zones/pull/'+zoneId+'/customdomains.json/'+domainId)</pre>
	</div>
  <div class="tab-pane" id="php26">
  	<pre>
$zoneId = '97167';
$domainId = '79182';
$api->delete('/zones/pull/'.$zoneId.'/customdomains.json/'.$domainId);</pre>
  </div>
  <div class="tab-pane" id="node26">
	<pre>
var zoneId = '97167'
var domainId = '79182'
netdna.del('/zones/pull/' + zoneId + '/customdomains.json/' + domainId, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response26">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab26 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab27">
  <li class="active"><a href="#ruby27" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python27" data-toggle='tab'>Python</a></li>
  <li><a href="#php27" data-toggle='tab'>PHP</a></li>
  <li><a href="#node27" data-toggle='tab'>Node</a></li>
  <li><a href="#response27" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby27">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python27">
		<pre>
api.get('/zones/push.json')</pre>
	</div>
  <div class="tab-pane" id="php27">
  	<pre>
$api->get('/zones/push.json');</pre>
  </div>
  <div class="tab-pane" id="node27">
	<pre>
netdna.get('/zones/push.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response27">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 2,
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "pushzones": [
            {
                "cdn_url": "cdn.somedomain.net",
                "compress": "0",
                "content_disposition": "0",
                "creation_date": "2013-05-16 15:25:19",
                "expires": null,
                "ftp_url": "ftp.newpushzone2.alias.netdna-cdn.com",
                "id": "96182",
                "inactive": "0",
                "label": null,
                "locked": "0",
                "name": "newpushzone2",
                "server_id": "11",
                "sslshared": "0",
                "storage_updated": "2013-05-24 06:31:52",
                "storage_used": "20480",
                "suspend": "0",
                "tmp_url": "newpushzone2.alias.netdna-cdn.com",
                "type": "3",
                "valid_referers": null
            },
            {
                "cdn_url": "cdn.somenewdomain2.com",
                "compress": "0",
                "content_disposition": "0",
                "creation_date": "2013-05-23 21:01:39",
                "expires": null,
                "ftp_url": "ftp.newpushzone3.alias.netdna-cdn.com",
                "id": "97181",
                "inactive": "0",
                "label": "Some other description",
                "locked": "0",
                "name": "newpushzone3",
                "server_id": "11",
                "sslshared": "0",
                "storage_updated": "2013-05-24 06:31:52",
                "storage_used": "20480",
                "suspend": "0",
                "tmp_url": "newpushzone3.alias.netdna-cdn.com",
                "type": "3",
                "valid_referers": null
            }
        ],
        "total": 2
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab27 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab28">
  <li class="active"><a href="#ruby28" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python28" data-toggle='tab'>Python</a></li>
  <li><a href="#php28" data-toggle='tab'>PHP</a></li>
  <li><a href="#node28" data-toggle='tab'>Node</a></li>
  <li><a href="#response28" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby28">
		<pre>
		</pre>
  </div>
  <div class="tab-pane" id="python28">
		<pre>
params = {"name":"newPushZone6","password":"password"}
api.post('/zones/push.json',data=params)</pre>
	</div>
  <div class="tab-pane" id="php28">
  	<pre>
$params = array("name"=>"newPushZone","password"=>"password");
$api->post('/zones/push.json', $params);</pre>
  </div>
  <div class="tab-pane" id="node28">
	<pre>
netdna.post('/zones/push.json', { name: 'newPushZone', password: 'password' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response28">
		<pre>
{
    "code": 201,
    "data": {
        "pushzone": {
            "cdn_url": "newpushzone4.alias.netdna-cdn.com",
            "compress": 0,
            "content_disposition": 0,
            "creation_date": "2013-05-24 16:41:53",
            "expires": null,
            "ftp_url": "ftp.newpushzone4.alias.netdna-cdn.com",
            "id": 97317,
            "inactive": 0,
            "label": null,
            "locked": 0,
            "name": "newpushzone4",
            "server_id": "11",
            "sslshared": null,
            "storage_updated": null,
            "storage_used": null,
            "suspend": 0,
            "tmp_url": "newpushzone4.alias.netdna-cdn.com",
            "type": 3,
            "valid_referers": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab28 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab29">
  <li class="active"><a href="#ruby29" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python29" data-toggle='tab'>Python</a></li>
  <li><a href="#php29" data-toggle='tab'>PHP</a></li>
  <li><a href="#node29" data-toggle='tab'>Node</a></li>
  <li><a href="#response29" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby29">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python29">
		<pre>
api.get('/zones/push.json/count')</pre>
	</div>
  <div class="tab-pane" id="php29">
  	<pre>
$api->get('/zones/push.json/count');</pre>
  </div>
  <div class="tab-pane" id="node29">
	<pre>
netdna.get('/zones/push.json/count', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response29">
		<pre>
{
    "code": 200,
    "data": {
        "count": "3"
    }
}
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab29 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab30">
  <li class="active"><a href="#ruby30" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python30" data-toggle='tab'>Python</a></li>
  <li><a href="#php30" data-toggle='tab'>PHP</a></li>
  <li><a href="#node30" data-toggle='tab'>Node</a></li>
  <li><a href="#response30" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby30">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python30">
		<pre>
id = '96182'
api.get('/zones/push.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php30">
  	<pre>
$id = '97181';
$api->get('/zones/push.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node30">
	<pre>
var id = '97182'
netdna.get('/zones/push.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response30">
		<pre>
{
    "code": 200,
    "data": {
        "pushzone": {
            "cdn_url": "cdn.somenewdomain2.com",
            "compress": "0",
            "content_disposition": "0",
            "creation_date": "2013-05-23 21:01:39",
            "expires": null,
            "ftp_url": "ftp.newpushzone3.alias.netdna-cdn.com",
            "id": "97181",
            "inactive": "0",
            "label": "Some other description",
            "locked": "0",
            "name": "newpushzone3",
            "server_id": "11",
            "sslshared": "0",
            "storage_updated": "2013-05-24 06:31:52",
            "storage_used": "20480",
            "suspend": "0",
            "tmp_url": "newpushzone3.alias.netdna-cdn.com",
            "type": "3",
            "valid_referers": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab30 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab31">
  <li class="active"><a href="#ruby31" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python31" data-toggle='tab'>Python</a></li>
  <li><a href="#php31" data-toggle='tab'>PHP</a></li>
  <li><a href="#node31" data-toggle='tab'>Node</a></li>
  <li><a href="#response31" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby31">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python31">
		<pre>
id = '96182'
params = {"label":"Some other description"}
api.put('/zones/push.json/'+id,params=params)</pre>
	</div>
  <div class="tab-pane" id="php31">
  	<pre>
$id = '97181';
$params = array("label"=>"Some other description");
$api->put('/zones/push.json/'.$id, $params);</pre>
  </div>
  <div class="tab-pane" id="node31">
	<pre>
var id = '97182'
netdna.get('/zones/push.json/' + id, { label: 'Some other description' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response31">
		<pre>
{
    "code": 200,
    "data": {
        "pushzone": {
            "cdn_url": "cdn.somenewdomain2.com",
            "compress": "0",
            "content_disposition": "0",
            "creation_date": "2013-05-23 21:01:39",
            "expires": null,
            "ftp_url": "ftp.newpushzone3.alias.netdna-cdn.com",
            "id": "97181",
            "inactive": "0",
            "label": "Some other description",
            "locked": "0",
            "name": "newpushzone3",
            "server_id": "11",
            "sslshared": "0",
            "storage_updated": "2013-05-24 06:31:52",
            "storage_used": "20480",
            "suspend": "0",
            "tmp_url": "newpushzone3.alias.netdna-cdn.com",
            "type": "3",
            "valid_referers": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab31 a:last').tab('show');
  })
</script>

---


## Delete Push Zone

Deletes a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab32">
  <li class="active"><a href="#ruby32" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python32" data-toggle='tab'>Python</a></li>
  <li><a href="#php32" data-toggle='tab'>PHP</a></li>
  <li><a href="#node32" data-toggle='tab'>Node</a></li>
  <li><a href="#response32" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby32">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python32">
		<pre>
id = '96182'
api.delete('/zones/push.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php32">
  	<pre>
$id = '97181';
$api->delete('/zones/push.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node32">
	<pre>
var id = '97181'
netdna.del('/zones/push.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response32">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab32 a:last').tab('show');
  })
</script>

---


## Enable Push Zone

Enables a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab33">
  <li class="active"><a href="#ruby33" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python33" data-toggle='tab'>Python</a></li>
  <li><a href="#php33" data-toggle='tab'>PHP</a></li>
  <li><a href="#node33" data-toggle='tab'>Node</a></li>
  <li><a href="#response33" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby33">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python33">
		<pre>
id = '96182'
api.enable('/zones/push.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php33">
  	<pre>
$id = '97181';
$api->enable('/zones/push.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node33">
	<pre>
var id = '97181'
netdna.enable('/zones/push.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response33">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab33 a:last').tab('show');
  })
</script>

---


## Disable Push Zone

Disables a push zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push.json/{zone_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab34">
  <li class="active"><a href="#ruby34" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python34" data-toggle='tab'>Python</a></li>
  <li><a href="#php34" data-toggle='tab'>PHP</a></li>
  <li><a href="#node34" data-toggle='tab'>Node</a></li>
  <li><a href="#response34" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby34">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python34">
		<pre>
id = '96182'
api.disable('/zones/push.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php34">
  	<pre>
$id = '97181';
$api->disable('/zones/push.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node34">
	<pre>
var id = '97181'
netdna.disable('/zones/push.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response34">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab34 a:last').tab('show');
  })
</script>


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

### Code Samples

<ul class="nav nav-tabs" id="myTab35">
  <li class="active"><a href="#ruby35" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python35" data-toggle='tab'>Python</a></li>
  <li><a href="#php35" data-toggle='tab'>PHP</a></li>
  <li><a href="#node35" data-toggle='tab'>Node</a></li>
  <li><a href="#response35" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby35">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python35">
		<pre>
id = '96182'
api.get('/zones/push/'+id+'/customdomains.json')</pre>
	</div>
  <div class="tab-pane" id="php35">
  	<pre>
$id = '96061';
$api->get('/zones/push/'.$id.'/customdomains.json');</pre>
  </div>
  <div class="tab-pane" id="node35">
	<pre>
var id = '96061'
netdna.get('/zones/push/' + id + '/customdomains.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response35">
		<pre>
{
    "code": 200,
    "data": {
        "customdomains": [
            {
                "bucket_id": "96061",
                "custom_domain": "cdn.somedomain.com",
                "id": "78330",
                "type": null
            }
        ],
        "total": 1
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab35 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab36">
  <li class="active"><a href="#ruby36" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python36" data-toggle='tab'>Python</a></li>
  <li><a href="#php36" data-toggle='tab'>PHP</a></li>
  <li><a href="#node36" data-toggle='tab'>Node</a></li>
  <li><a href="#response36" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby36">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python36">
		<pre>
id = '96182'
params = {"custom_domain":"cdn.somedomain15.com"}
api.post('/zones/push/'+id+'/customdomains.json', params)</pre>
	</div>
  <div class="tab-pane" id="php36">
  	<pre>
$id = '97181';
$params = array("custom_domain"=>"cdn.somedomain2.net");
$api->post('/zones/push/'.$id.'/customdomains.json', $params);</pre>
  </div>
  <div class="tab-pane" id="node36">
	<pre>
var id = '97181'
netdna.post('/zones/push/' + id + '/customdomains.json', { custom_domain: 'cdn.somedomain2.net' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response36">
		<pre>
{
    "code": 201,
    "data": {
        "customdomain": {
            "bucket_id": "97181",
            "custom_domain": "cdn.somedomain4.net",
            "id": 79283,
            "type": null
        }
    }
}
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab36 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab37">
  <li class="active"><a href="#ruby37" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python37" data-toggle='tab'>Python</a></li>
  <li><a href="#php37" data-toggle='tab'>PHP</a></li>
  <li><a href="#node37" data-toggle='tab'>Node</a></li>
  <li><a href="#response37" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby37">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python37">
		<pre>
zoneId = '96182'
domainId = '79320'
api.get('/zones/push/'+zoneId+'/customdomains.json/'+domainId)</pre>
	</div>
  <div class="tab-pane" id="php37">
  	<pre>
$zoneId = '97181';
$domainId = '79188';
$api->get('/zones/push/'.$zoneId.'/customdomains.json/'.$domainId);</pre>
  </div>
  <div class="tab-pane" id="node37">
	<pre>
var zoneId = '97181'
var domainId = '79188'
netdna.get('/zones/push/' + zoneId + '/customdomains.json/' + domainId, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response37">
		<pre>
{
    "code": 200,
    "data": {
        "customdomain": {
            "bucket_id": "97181",
            "custom_domain": "cdn.somenewdomain2.com",
            "id": "79188",
            "type": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab37 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab38">
  <li class="active"><a href="#ruby38" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python38" data-toggle='tab'>Python</a></li>
  <li><a href="#php38" data-toggle='tab'>PHP</a></li>
  <li><a href="#node38" data-toggle='tab'>Node</a></li>
  <li><a href="#response38" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby38">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python38">
		<pre>
zoneId = '96182'
domainId = '79320'
params = {"custom_domain":"cdn.somenewdomain40.com"}
api.put('/zones/push/'+zoneId+'/customdomains.json/'+domainId,params=params)</pre>
	</div>
  <div class="tab-pane" id="php38">
  	<pre>
$zoneId = '97181';
$domainId = '79188';
$params = array("custom_domain"=>"cdn.somenewdomain2.com");
$api->put('/zones/push/'.$zoneId.'/customdomains.json/'.$domainId, $params);
</pre>
  </div>
  <div class="tab-pane" id="node38">
	<pre>
var zoneId = '97181'
var domainId = '79188'
netdna.put('/zones/push/' + zoneId + '/customdomains.json/' + domainId, { custom_domain: 'cdn.somenewdomain2.com' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response38">
		<pre>
{
    "code": 200,
    "data": {
        "customdomain": {
            "bucket_id": "97181",
            "custom_domain": "cdn.somenewdomain12.com",
            "id": "79188",
            "type": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab38 a:last').tab('show');
  })
</script>

---


## Delete Custom Domain

Deletes a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/push/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab39">
  <li class="active"><a href="#ruby39" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python39" data-toggle='tab'>Python</a></li>
  <li><a href="#php39" data-toggle='tab'>PHP</a></li>
  <li><a href="#node39" data-toggle='tab'>Node</a></li>
  <li><a href="#response39" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby39">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python39">
		<pre>
zoneId = '96182'
domainId = '79320'
api.delete('/zones/push/'+zoneId+'/customdomains.json/'+domainId)</pre>
	</div>
  <div class="tab-pane" id="php39">
  	<pre>
$zoneId = '97181';
$domainId = '79188';
$api->delete('/zones/push/'.$zoneId.'/customdomains.json/'.$domainId);</pre>
  </div>
  <div class="tab-pane" id="node39">
	<pre>
var zoneId = '97181'
var domainId = '79188'
netdna.del('/zones/push/' + zoneId + '/customdomains.json/' + domainId, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response39">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab39 a:last').tab('show');
  })
</script>


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

### Code Samples

<ul class="nav nav-tabs" id="myTab40">
  <li class="active"><a href="#ruby40" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python40" data-toggle='tab'>Python</a></li>
  <li><a href="#php40" data-toggle='tab'>PHP</a></li>
  <li><a href="#node40" data-toggle='tab'>Node</a></li>
  <li><a href="#response40" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby40">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python40">
		<pre>
api.get('/zones/vod.json')</pre>
	</div>
  <div class="tab-pane" id="php40">
  	<pre>
$api->get('/zones/vod.json');</pre>
  </div>
  <div class="tab-pane" id="node40">
	<pre>
netdna.get('/zones/vod.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response40">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 2,
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "total": 2,
        "vodzones": [
            {
                "cdn_url": "cdn.somedomain.com",
                "creation_date": "2013-05-16 16:02:35",
                "direct_url": "d.newvodzone.alias.netdna-cdn.com",
                "ftp_url": "ftp.newvodzone.alias.netdna-cdn.com",
                "id": "96187",
                "inactive": "0",
                "label": null,
                "locked": "0",
                "name": "newvodzone",
                "pseudo_url": "p.newvodzone.alias.netdna-cdn.com",
                "rtmp_url": "r.newvodzone.alias.netdna-cdn.com",
                "server_id": "30",
                "storage_updated": "2013-05-24 06:35:35",
                "storage_used": "4096",
                "suspend": "0",
                "tmp_url": "newvodzone.alias.netdna-cdn.com",
                "token": null,
                "type": "4"
            },
            {
                "cdn_url": "cdn.somenewdomain3.com",
                "creation_date": "2013-05-23 21:25:44",
                "direct_url": "d.newvodzone3.alias.netdna-cdn.com",
                "ftp_url": "ftp.newvodzone3.alias.netdna-cdn.com",
                "id": "97183",
                "inactive": "0",
                "label": "Some other description",
                "locked": "0",
                "name": "newvodzone3",
                "pseudo_url": "p.newvodzone3.alias.netdna-cdn.com",
                "rtmp_url": "r.newvodzone3.alias.netdna-cdn.com",
                "server_id": "30",
                "storage_updated": "2013-05-24 06:35:35",
                "storage_used": "4096",
                "suspend": "0",
                "tmp_url": "newvodzone3.alias.netdna-cdn.com",
                "token": null,
                "type": "4"
            }
        ]
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab40 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab41">
  <li class="active"><a href="#ruby41" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python41" data-toggle='tab'>Python</a></li>
  <li><a href="#php41" data-toggle='tab'>PHP</a></li>
  <li><a href="#node41" data-toggle='tab'>Node</a></li>
  <li><a href="#response41" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby41">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python41">
		<pre>
params = {"name":"newvodZone7","password":"password"}
api.post('/zones/vod.json',data=params)</pre>
	</div>
  <div class="tab-pane" id="php41">
  	<pre>
$params = array("name"=>"newVODZone3","password"=>"password");
$response = $api->post('/zones/vod.json',$params);</pre>
  </div>
  <div class="tab-pane" id="node41">
	<pre>
netdna.post('/zones/vod.json', { name: 'newVODZone3', password: 'password' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response41">
		<pre>
{
    "code": 201,
    "data": {
        "vodzone": {
            "cdn_url": "newvodzone4.alias.netdna-cdn.com",
            "creation_date": "2013-05-24 16:50:18",
            "direct_url": "d.newvodzone4.alias.netdna-cdn.com",
            "ftp_url": "ftp.newvodzone4.alias.netdna-cdn.com",
            "id": 97319,
            "inactive": 0,
            "label": null,
            "locked": 0,
            "name": "newvodzone4",
            "pseudo_url": "p.newvodzone4.alias.netdna-cdn.com",
            "rtmp_url": "r.newvodzone4.alias.netdna-cdn.com",
            "server_id": "30",
            "storage_updated": null,
            "storage_used": null,
            "suspend": 0,
            "tmp_url": "newvodzone4.alias.netdna-cdn.com",
            "token": null,
            "type": 4
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab41 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab42">
  <li class="active"><a href="#ruby42" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python42" data-toggle='tab'>Python</a></li>
  <li><a href="#php42" data-toggle='tab'>PHP</a></li>
  <li><a href="#node42" data-toggle='tab'>Node</a></li>
  <li><a href="#response42" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby42">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python42">
		<pre>
api.get('/zones/vod.json/count')</pre>
	</div>
  <div class="tab-pane" id="php42">
  	<pre>
$api->get('/zones/vod.json/count');</pre>
  </div>
  <div class="tab-pane" id="node42">
	<pre>
netdna.get('/zones/vod.json/count', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response42">
		<pre>
{
    "code": 200,
    "data": {
        "count": "4"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab42 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab43">
  <li class="active"><a href="#ruby43" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python43" data-toggle='tab'>Python</a></li>
  <li><a href="#php43" data-toggle='tab'>PHP</a></li>
  <li><a href="#node43" data-toggle='tab'>Node</a></li>
  <li><a href="#response43" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby43">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python43">
		<pre>
id = '96187'
api.get('/zones/vod.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php43">
  	<pre>
$id = '97183';
$api->get('/zones/vod.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node43">
	<pre>
var id = '97183'
netdna.get('/zones/vod.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response43">
		<pre>
{
    "code": 200,
    "data": {
        "vodzone": {
            "cdn_url": "cdn.somenewdomain3.com",
            "creation_date": "2013-05-23 21:25:44",
            "direct_url": "d.newvodzone3.alias.netdna-cdn.com",
            "ftp_url": "ftp.newvodzone3.alias.netdna-cdn.com",
            "id": "97183",
            "inactive": "0",
            "label": "Some other description",
            "locked": "0",
            "name": "newvodzone3",
            "pseudo_url": "p.newvodzone3.alias.netdna-cdn.com",
            "rtmp_url": "r.newvodzone3.alias.netdna-cdn.com",
            "server_id": "30",
            "storage_updated": "2013-05-24 06:35:35",
            "storage_used": "4096",
            "suspend": "0",
            "tmp_url": "newvodzone3.alias.netdna-cdn.com",
            "token": null,
            "type": "4"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab43 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab44">
  <li class="active"><a href="#ruby44" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python44" data-toggle='tab'>Python</a></li>
  <li><a href="#php44" data-toggle='tab'>PHP</a></li>
  <li><a href="#node44" data-toggle='tab'>Node</a></li>
  <li><a href="#response44" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby44">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python44">
		<pre>
id = '96187'
params = {"label":"Some other description"}
api.put('/zones/vod.json/'+id,params=params)</pre>
	</div>
  <div class="tab-pane" id="php44">
  	<pre>
$id = '97183';
$params =  array("label"=>"Some other description");
$api->put('/zones/vod.json/'.$id,$params);</pre>
  </div>
  <div class="tab-pane" id="node44">
	<pre>
var id = '97183'
netdna.put('/zones/vod.json/' + id, { label: 'Some other description' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response44">
		<pre>
{
    "code": 200,
    "data": {
        "vodzone": {
            "cdn_url": "cdn.somenewdomain3.com",
            "creation_date": "2013-05-23 21:25:44",
            "direct_url": "d.newvodzone3.alias.netdna-cdn.com",
            "ftp_url": "ftp.newvodzone3.alias.netdna-cdn.com",
            "id": "97183",
            "inactive": "0",
            "label": "Some other description",
            "locked": "0",
            "name": "newvodzone3",
            "pseudo_url": "p.newvodzone3.alias.netdna-cdn.com",
            "rtmp_url": "r.newvodzone3.alias.netdna-cdn.com",
            "server_id": "30",
            "storage_updated": "2013-05-24 06:35:35",
            "storage_used": "4096",
            "suspend": "0",
            "tmp_url": "newvodzone3.alias.netdna-cdn.com",
            "token": null,
            "type": "4"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab44 a:last').tab('show');
  })
</script>

---


## Delete VOD Zone

Deletes a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab45">
  <li class="active"><a href="#ruby45" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python45" data-toggle='tab'>Python</a></li>
  <li><a href="#php45" data-toggle='tab'>PHP</a></li>
  <li><a href="#node45" data-toggle='tab'>Node</a></li>
  <li><a href="#response45" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby45">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python45">
		<pre>
id = '96187'
api.delete('/zones/vod.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php45">
  	<pre>
$id = '97183';
$api->delete('/zones/vod.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node45">
	<pre>
var id = '97183'
netdna.del('/zones/vod.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response45">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab45 a:last').tab('show');
  })
</script>

---


## Enable VOD Zone

Enables a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab46">
  <li class="active"><a href="#ruby46" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python46" data-toggle='tab'>Python</a></li>
  <li><a href="#php46" data-toggle='tab'>PHP</a></li>
  <li><a href="#node46" data-toggle='tab'>Node</a></li>
  <li><a href="#response46" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby46">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python46">
		<pre>
id = '96187'
api.enable('/zones/vod.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php46">
  	<pre>
$id = '96187';
$api->enable('/zones/vod.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node46">
	<pre>
var id = '96187'
netdna.enable('/zones/vod.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response46">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab46 a:last').tab('show');
  })
</script>

---


## Disable VOD Zone

Disables a VOD zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod.json/{zone_id}</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab47">
  <li class="active"><a href="#ruby47" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python47" data-toggle='tab'>Python</a></li>
  <li><a href="#php47" data-toggle='tab'>PHP</a></li>
  <li><a href="#node47" data-toggle='tab'>Node</a></li>
  <li><a href="#response47" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby47">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python47">
		<pre>
id = '96187'
api.disable('/zones/vod.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php47">
  	<pre>
$id = '96187';
$api->disable('/zones/vod.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node47">
	<pre>
var id = '96187'
netdna.disable('/zones/vod.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response47">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab47 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab48">
  <li class="active"><a href="#ruby48" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python48" data-toggle='tab'>Python</a></li>
  <li><a href="#php48" data-toggle='tab'>PHP</a></li>
  <li><a href="#node48" data-toggle='tab'>Node</a></li>
  <li><a href="#response48" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby48">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python48">
		<pre>
id = '96187'
api.get('/zones/vod/'+id+'/customdomains.json')</pre>
	</div>
  <div class="tab-pane" id="php48">
  	<pre>
$id = '97183';
$api->get('/zones/vod/'.$id.'/customdomains.json');</pre>
  </div>
  <div class="tab-pane" id="node48">
	<pre>
var id = '97183'
netdna.get('/zones/vod.json/' + id + '/customdomains.json, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response48">
		<pre>
{
    "code": 200,
    "data": {
        "customdomains": [
            {
                "bucket_id": "97183",
                "custom_domain": "cdn.somenewdomain3.com",
                "id": "79191",
                "type": "vod-rtmp"
            }
        ],
        "total": 1
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab48 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab49">
  <li class="active"><a href="#ruby49" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python49" data-toggle='tab'>Python</a></li>
  <li><a href="#php49" data-toggle='tab'>PHP</a></li>
  <li><a href="#node49" data-toggle='tab'>Node</a></li>
  <li><a href="#response49" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby49">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python49">
		<pre>
id = '96187'
params = {"custom_domain":"cdn.somedomain16.com","type":"vod-rtmp"}
api.post('/zones/vod/'+id+'/customdomains.json', params)</pre>
	</div>
  <div class="tab-pane" id="php49">
  	<pre>
$id = '97183';
$params = array("custom_domain"=>"cdn.somedomain2.com","type"=>"vod-rtmp");
$api->post('/zones/vod/'.$id.'/customdomains.json', $params);</pre>
  </div>
  <div class="tab-pane" id="node49">
	<pre>
var id = '97183'
netdna.post('/zones/vod/' + id + '/customdomains.json', { custom_domain: 'cdn.somedomain2.com', type: 'vod-rtmp' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response49">
		<pre>
{
    "code": 201,
    "data": {
        "customdomain": {
            "bucket_id": "97183",
            "custom_domain": "cdn.somedomain2.com",
            "id": 79284,
            "type": "vod-rtmp"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab49 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab50">
  <li class="active"><a href="#ruby50" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python50" data-toggle='tab'>Python</a></li>
  <li><a href="#php50" data-toggle='tab'>PHP</a></li>
  <li><a href="#node50" data-toggle='tab'>Node</a></li>
  <li><a href="#response50" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby50">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python50">
		<pre>
zoneId = '96187'
domainId = '79321'
api.get('/zones/vod/'+zoneId+'/customdomains.json/'+domainId)</pre>
	</div>
  <div class="tab-pane" id="php50">
  	<pre>
$zoneId = '97183';
$domainId = '79191';
$response =  $api->get('/zones/vod/'.$zoneId.'/customdomains.json/'.$domainId);</pre>
  </div>
  <div class="tab-pane" id="node50">
	<pre>
var zoneId = '97183'
var domainId = '79191'
netdna.get('/zones/vod/' + zoneId + '/customdomains.json/' + domainId, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response50">
		<pre>
{
    "code": 200,
    "data": {
        "customdomain": {
            "bucket_id": "97183",
            "custom_domain": "cdn.somenewdomain3.com",
            "id": "79191",
            "type": "vod-rtmp"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab50 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab51">
  <li class="active"><a href="#ruby51" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python51" data-toggle='tab'>Python</a></li>
  <li><a href="#php51" data-toggle='tab'>PHP</a></li>
  <li><a href="#node51" data-toggle='tab'>Node</a></li>
  <li><a href="#response51" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby51">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python51">
		<pre>
zoneId = '96187'
domainId = '79321'
params = {"custom_domain":"cdn.somenewdomain401.com"}
api.put('/zones/vod/'+zoneId+'/customdomains.json/'+domainId,params=params)</pre>
	</div>
  <div class="tab-pane" id="php51">
  	<pre>
$zoneId = '97183';
$domainId = '79191';
$params = array("custom_domain"=>"cdn.somenewdomain3.com");
$api->put('/zones/vod/'.$zoneId.'/customdomains.json/'.$domainId, $params);</pre>
  </div>
  <div class="tab-pane" id="node51">
	<pre>
var zoneId = '97183'
var domainId = '79191'
netdna.put('/zones/vod/' + zoneId + '/customdomains.json/' + domainId, { custom_domain: 'cdn.somenewdomain3.com' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response51">
		<pre>
{
    "code": 200,
    "data": {
        "customdomain": {
            "bucket_id": "97183",
            "custom_domain": "cdn.somenewdomain42.com",
            "id": "79284",
            "type": "vod-rtmp"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab51 a:last').tab('show');
  })
</script>

---


## Delete Custom Domain

Deletes a custom domain specified by the {zone_id} and
{customdomain_id} parameters

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/vod/{zone_id}/customdomains.json/{customdomain_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab52">
  <li class="active"><a href="#ruby52" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python52" data-toggle='tab'>Python</a></li>
  <li><a href="#php52" data-toggle='tab'>PHP</a></li>
  <li><a href="#node52" data-toggle='tab'>Node</a></li>
  <li><a href="#response52" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby52">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python52">
		<pre>
zoneId = '96187'
domainId = '79321'
api.delete('/zones/vod/'+zoneId+'/customdomains.json/'+domainId)</pre>
	</div>
  <div class="tab-pane" id="php52">
  	<pre>
$zoneId = '97183';
$domainId = '79191';
$api->delete('/zones/vod/'.$zoneId.'/customdomains.json/'.$domainId);</pre>
  </div>
  <div class="tab-pane" id="node52">
	<pre>
var zoneId = '97183'
var domainId = '79191'
netdna.del('/zones/vod/' + zoneId + '/customdomains.json/' + domainId, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response52">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab52 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab53">
  <li class="active"><a href="#ruby53" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python53" data-toggle='tab'>Python</a></li>
  <li><a href="#php53" data-toggle='tab'>PHP</a></li>
  <li><a href="#node53" data-toggle='tab'>Node</a></li>
  <li><a href="#response53" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby53">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python53">
		<pre>
api.get('/zones/live.json')</pre>
	</div>
  <div class="tab-pane" id="php53">
  	<pre>
$api->get('/zones/live.json');</pre>
  </div>
  <div class="tab-pane" id="node53">
	<pre>
netdna.get('/zones/live.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response53">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 2,
        "livezones": [
            {
                "cdn_url": "newlivezone.alias.netdna-cdn.com",
                "creation_date": "2013-05-16 16:23:49",
                "id": "96193",
                "inactive": "0",
                "label": null,
                "locked": "0",
                "name": "newlivezone",
                "pub_url": "publish.newlivezone.alias.netdna-cdn.com/live/96193",
                "server_id": "3",
                "suspend": "0",
                "tmp_url": "newlivezone.alias.netdna-cdn.com",
                "type": "5",
                "view_url": "newlivezone.alias.netdna-cdn.com/live/96193"
            },
            {
                "cdn_url": "newlivezone3.alias.netdna-cdn.com",
                "creation_date": "2013-05-23 21:50:00",
                "id": "97185",
                "inactive": "0",
                "label": "Some other description",
                "locked": "0",
                "name": "newlivezone3",
                "pub_url": "publish.newlivezone3.alias.netdna-cdn.com/live/97185",
                "server_id": "3",
                "suspend": "0",
                "tmp_url": "newlivezone3.alias.netdna-cdn.com",
                "type": "5",
                "view_url": "newlivezone3.alias.netdna-cdn.com/live/97185"
            }
        ],
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "total": 2
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab53 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab54">
  <li class="active"><a href="#ruby54" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python54" data-toggle='tab'>Python</a></li>
  <li><a href="#php54" data-toggle='tab'>PHP</a></li>
  <li><a href="#node54" data-toggle='tab'>Node</a></li>
  <li><a href="#response54" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby54">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python54">
		<pre>
params = {"name":"newliveZone7","password":"password"}
api.post('/zones/live.json',data=params)</pre>
	</div>
  <div class="tab-pane" id="php54">
  	<pre>
$api->post('/zones/live.json', array("name"=>"newLiveZone3","password"=>"password"));</pre>
  </div>
  <div class="tab-pane" id="node54">
	<pre>
netdna.post('/zones/live.json',  { name: 'newLiveZone3', password: 'password' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response54">
		<pre>
{
    "code": 201,
    "data": {
        "livezone": {
            "cdn_url": "newlivezone4.alias.netdna-cdn.com",
            "creation_date": "2013-05-24 17:01:30",
            "id": 97323,
            "inactive": 0,
            "label": null,
            "locked": 0,
            "name": "newlivezone4",
            "pub_url": "publish.newlivezone4.alias.netdna-cdn.com/live/97323",
            "server_id": 3,
            "suspend": 0,
            "tmp_url": "newlivezone4.alias.netdna-cdn.com",
            "type": 5,
            "view_url": "newlivezone4.alias.netdna-cdn.com/live/97323"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab54 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab55">
  <li class="active"><a href="#ruby55" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python55" data-toggle='tab'>Python</a></li>
  <li><a href="#php55" data-toggle='tab'>PHP</a></li>
  <li><a href="#node55" data-toggle='tab'>Node</a></li>
  <li><a href="#response55" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby55">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python55">
		<pre>
api.get('/zones/live.json/count')</pre>
	</div>
  <div class="tab-pane" id="php55">
  	<pre>
$api->get('/zones/live.json/count');</pre>
  </div>
  <div class="tab-pane" id="node55">
	<pre>
netdna.get('/zones.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response55">
		<pre>
{
    "code": 200,
    "data": {
        "count": "4"
    }
}
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab55 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab56">
  <li class="active56"><a href="#ruby" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python56" data-toggle='tab'>Python</a></li>
  <li><a href="#php56" data-toggle='tab'>PHP</a></li>
  <li><a href="#node56" data-toggle='tab'>Node</a></li>
  <li><a href="#response56" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby56">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python56">
		<pre>
id = '96193'
api.get('/zones/live.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php56">
  	<pre>
$id = '97185';
$api->get('/zones/live.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node56">
	<pre>
var id = '97185'
netdna.get('/zones/live.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response56">
		<pre>
{
    "code": 200,
    "data": {
        "livezone": {
            "cdn_url": "newlivezone3.alias.netdna-cdn.com",
            "creation_date": "2013-05-23 21:50:00",
            "id": "97185",
            "inactive": "0",
            "label": "Some other description",
            "locked": "0",
            "name": "newlivezone3",
            "pub_url": "publish.newlivezone3.alias.netdna-cdn.com/live/97185",
            "server_id": "3",
            "suspend": "0",
            "tmp_url": "newlivezone3.alias.netdna-cdn.com",
            "type": "5",
            "view_url": "newlivezone3.alias.netdna-cdn.com/live/97185"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab56 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab57">
  <li class="active"><a href="#ruby57" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python57" data-toggle='tab'>Python</a></li>
  <li><a href="#php57" data-toggle='tab'>PHP</a></li>
  <li><a href="#node57" data-toggle='tab'>Node</a></li>
  <li><a href="#response57" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby57">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python57">
		<pre>
id = '96193'
params = {"label":"Some other description"}
api.put('/zones/live.json/'+id,params=params)</pre>
	</div>
  <div class="tab-pane" id="php57">
  	<pre>
$id = '97185';
$params =  array("label"=>"Some other description");
$response =  $api->put('/zones/live.json/'.$id,$params);
</pre>
  </div>
  <div class="tab-pane" id="node57">
	<pre>
var id = '97185'
netdna.put('/zones/live.json/' + id, { label: 'Some other description' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response57">
		<pre>
{
    "code": 200,
    "data": {
        "livezone": {
            "cdn_url": "newlivezone3.alias.netdna-cdn.com",
            "creation_date": "2013-05-23 21:50:00",
            "id": "97185",
            "inactive": "0",
            "label": "Some other description",
            "locked": "0",
            "name": "newlivezone3",
            "pub_url": "publish.newlivezone3.alias.netdna-cdn.com/live/97185",
            "server_id": "3",
            "suspend": "0",
            "tmp_url": "newlivezone3.alias.netdna-cdn.com",
            "type": "5",
            "view_url": "newlivezone3.alias.netdna-cdn.com/live/97185"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab57 a:last').tab('show');
  })
</script>

---


## Delete Live Zone

Deletes a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab58">
  <li class="active"><a href="#ruby58" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python58" data-toggle='tab'>Python</a></li>
  <li><a href="#php58" data-toggle='tab'>PHP</a></li>
  <li><a href="#node58" data-toggle='tab'>Node</a></li>
  <li><a href="#response58" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby58">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python58">
		<pre>
id = '96193'
api.delete('/zones/live.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php58">
  	<pre>
$id = '97185';
$api->delete('/zones/live.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node58">
	<pre>
var id = '97185'
netdna.del('/zones/live.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response58">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab58 a:last').tab('show');
  })
</script>

---


## Enable Live Zone

Enables a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url ENABLE"><span class="http_method">ENABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab59">
  <li class="active"><a href="#ruby59" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python59" data-toggle='tab'>Python</a></li>
  <li><a href="#php59" data-toggle='tab'>PHP</a></li>
  <li><a href="#node59" data-toggle='tab'>Node</a></li>
  <li><a href="#response59" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby59">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python59">
		<pre>
id = '96193'
api.enable('/zones/live.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php59">
  	<pre>
$id = '96061';
$api->enable('/zones/live.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node59">
	<pre>
var id = '96061'
netdna.enable('/zones/live.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response59">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab59 a:last').tab('show');
  })
</script>

---


## Disable Live Zone

Disables a live zone specified by the {zone_id} parameter

<div class="heading">
<div class="url DISABLE"><span class="http_method">DISABLE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/live.json/{zone_id}</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab60">
  <li class="active"><a href="#ruby60" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python60" data-toggle='tab'>Python</a></li>
  <li><a href="#php60" data-toggle='tab'>PHP</a></li>
  <li><a href="#node60" data-toggle='tab'>Node</a></li>
  <li><a href="#response60" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby60">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python60">
		<pre>
id = '96193'
api.disable('/zones/live.json/'+id)</pre>
	</div>
  <div class="tab-pane" id="php60">
  	<pre>
$id = '96061';
api->disable('/zones/live.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node60">
	<pre>
var id = '96061'
netdna.disable('/zones/live.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response60">
		<pre>
{
	"code":200
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab60 a:last').tab('show');
  })
</script>

---


# Zones SSL API

## Get Zone's SSL Information

Get the SSL certificate for the specified {zone_type} and
{zone_id}.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/ssl.json</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab61">
  <li class="active"><a href="#ruby61" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python61" data-toggle='tab'>Python</a></li>
  <li><a href="#php61" data-toggle='tab'>PHP</a></li>
  <li><a href="#node61" data-toggle='tab'>Node</a></li>
  <li><a href="#response61" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby61">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python61">
		<pre>
id = '96061'
type = 'pull'
api.get('/zones/'+type+'/'+id+'/ssl.json')</pre>
	</div>
  <div class="tab-pane" id="php61">
  	<pre>
$id = '96061';
$type = 'pull';
$api->get('/zones/'.$type.'/'.$id.'/ssl.json');</pre>
  </div>
  <div class="tab-pane" id="node61">
	<pre>
var id = '96061'
var type = 'pull'
netdna.get('/zones/' + type + '/' + id + '/ssl.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response61">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab61 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab62">
  <li class="active"><a href="#ruby62" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python62" data-toggle='tab'>Python</a></li>
  <li><a href="#php62" data-toggle='tab'>PHP</a></li>
  <li><a href="#node62" data-toggle='tab'>Node</a></li>
  <li><a href="#response62" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby62">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python62">
		<pre>
id = '96061'
type = 'pull'
ssl_crt = ""
params = {"ssl_crt": ssl_crt,"ssl_key": "somesslkey"}
api.post('/zones/'+type+'/'+id+'/ssl.json',params)</pre>
	</div>
  <div class="tab-pane" id="php62">
  	<pre>
$id = '96061';
$type = 'pull';
$ssl_crt = " ... ";
$params = array("ssl_crt"=>$ssl_crt,"ssl_key"=>"somesslkey");
$api->post('/zones/'.$type.'/'.$id.'/ssl.json',$params);</pre>
  </div>
  <div class="tab-pane" id="node62">
	<pre>
var id = '96061'
var type = 'pull'
var ssl_crt = " ... "
netdna.post('/zones/' + type + '/' + id + '/ssl.json', { ssl_crt: ssl_crt, ssl_key: 'somesslkey' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response62">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab62 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab63">
  <li class="active"><a href="#ruby63" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python63" data-toggle='tab'>Python</a></li>
  <li><a href="#php63" data-toggle='tab'>PHP</a></li>
  <li><a href="#node63" data-toggle='tab'>Node</a></li>
  <li><a href="#response63" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby63">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python63">
		<pre>
id = '96061'
type = 'pull'
ssl_crt = ""
params = {"ssl_crt": ssl_crt,"ssl_key": "somesslkey"}
api.put('/zones/'+type+'/'+id+'/ssl.json',params)</pre>
	</div>
  <div class="tab-pane" id="php63">
  	<pre>
$id = '96061';
$type = 'pull';
$ssl_crt = " ... ";
$params = array("ssl_crt"=>$ssl_crt,"ssl_key"=>"somesslkey");
$api->put('/zones/'.$type.'/'.$id.'/ssl.json',$params);</pre>
  </div>
  <div class="tab-pane" id="node63">
	<pre>
var id = '96061'
var type = 'pull'
var ssl_crt = " ... "
netdna.put('/zones/' + type + '/' + id + '/ssl.json', { ssl_crt: ssl_crt, ssl_key: 'somesslkey' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response63">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab63 a:last').tab('show');
  })
</script>

---


## Remove Zone's SSL Information

Remove the SSL certificate for the specified {zone_type} and
{zone_id}.

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/ssl.json</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab64">
  <li class="active"><a href="#ruby64" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python64" data-toggle='tab'>Python</a></li>
  <li><a href="#php64" data-toggle='tab'>PHP</a></li>
  <li><a href="#node64" data-toggle='tab'>Node</a></li>
  <li><a href="#response64" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby64">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python64">
		<pre>
id = '96061'
type = 'pull'
api.post('/zones/'+type+'/'+id+'/ssl.json')</pre>
	</div>
  <div class="tab-pane" id="php64">
  	<pre>
$id = '96061';
$type = 'pull';
$api->post('/zones/'.$type.'/'.$id.'/ssl.json');</pre>
  </div>
  <div class="tab-pane" id="node64">
	<pre>
var id = '96061'
var type = 'pull'
netdna.post('/zones/' + type + '/' + id + '/ssl.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response64">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab64 a:last').tab('show');
  })
</script>

---


# Zones Upstream API

## Get Upstream information for the current zone

Get the upstream information for the specified {zone_id}.

<div class="heading">
<div class="url GET"><span class="http_method">GET</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/upstream.json</span></div>
</div>

### Code Samples

<ul class="nav nav-tabs" id="myTab65">
  <li class="active"><a href="#ruby65" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python65" data-toggle='tab'>Python</a></li>
  <li><a href="#php65" data-toggle='tab'>PHP</a></li>
  <li><a href="#node65" data-toggle='tab'>Node</a></li>
  <li><a href="#response65" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby65">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python65">
		<pre>
type = 'pull'
id = '96061'
api.post('/zones/'+type+'/'+id+'/upstream.json')</pre>
	</div>
  <div class="tab-pane" id="php65">
  	<pre>
$type = 'pull';
$id = '96061';
$api->post('/zones/'.$type.'/'.$id.'/upstream.json');</pre>
  </div>
  <div class="tab-pane" id="node65">
	<pre>
var type = 'pull'
var id = '96061'
netdna.post('/zones/' + type + '/' + id + '/upstream.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response65">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab65 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab66">
  <li class="active"><a href="#ruby66" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python66" data-toggle='tab'>Python</a></li>
  <li><a href="#php66" data-toggle='tab'>PHP</a></li>
  <li><a href="#node66" data-toggle='tab'>Node</a></li>
  <li><a href="#response66" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby66">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python66">
		<pre>
type = 'pull'
id = '96061'
params = {"server_url": "http://cdn.somedomain.com","server": "http://cdn.somedomain.com","port": "80"}
api.post('/zones/'+type+'/'+id+'/upstream.json')</pre>
	</div>
  <div class="tab-pane" id="php66">
  	<pre>
$type = 'pull';
$id = '96061';
$params = array("server_url"=>"http://cdn.somedomain.com","server"=>"http://cdn.somedomain.com","port"=>"80");
$api->post('/zones/'.$type.'/'.$id.'/upstream.json');</pre>
  </div>
  <div class="tab-pane" id="node66">
	<pre>
var type = 'pull'
var id = '96061'
netdna.post('/zones/' + type + '/' + id + '/upstream.json', { server_url: 'http://cdn.somedomain.com', server: 'http://cdn.somedomain.com', port: '80' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response66">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab67">
  <li class="active"><a href="#ruby67" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python67" data-toggle='tab'>Python</a></li>
  <li><a href="#php67" data-toggle='tab'>PHP</a></li>
  <li><a href="#node67" data-toggle='tab'>Node</a></li>
  <li><a href="#response67" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby67">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python67">
		<pre>
type = 'pull'
id = '96061'
params = {"upsream_id": "93013","server_url": "http://somedomain.net","port": "80"}
api.put('/zones/'+type+'/'+id+'/upstream.json')</pre>
	</div>
  <div class="tab-pane" id="php67">
  	<pre>
$type = 'pull';
$id = '96061';
$params = array("upstream_id"=>"93013","server_url"=>"http://somedomain.net","port"=>"80");
$api->put('/zones/'.$type.'/'.$id.'/upstream.json');</pre>
  </div>
  <div class="tab-pane" id="node67">
	<pre>
var type = 'pull'
var id = '96061'
netdna.put('/zones/' + type + '/' + id + '/upstream.json', { upstream_id: '93013', server_url: 'http://somedomain.net', port: '80' }, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response67">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab67 a:last').tab('show');
  })
</script>

---


## Remove Zone's Upstream Information

Remove the Upstream Information for the specified {zone_id}.

<div class="heading">
<div class="url DELETE"><span class="http_method">DELETE</span>
<span class="path">https://rws.netdna.com/{companyalias}/zones/{zone_type}/{zone_id}/upstream.json</span></div>
</div>


### Code Samples

<ul class="nav nav-tabs" id="myTab68">
  <li class="active"><a href="#ruby68" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python68" data-toggle='tab'>Python</a></li>
  <li><a href="#php68" data-toggle='tab'>PHP</a></li>
  <li><a href="#node68" data-toggle='tab'>Node</a></li>
  <li><a href="#response68" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby68">
		<pre>
</pre>
  </div>
  <div class="tab-pane" id="python68">
		<pre>
type = 'pull'
id = '96061'
api.delete('/zones/'+type+'/'+id+'/upstream.json')</pre>
	</div>
  <div class="tab-pane" id="php68">
  	<pre>
$type = 'pull';
$id = '96061';
$api->delete('/zones/'.$type.'/'.$id.'/upstream.json');</pre>
  </div>
  <div class="tab-pane" id="node68">
	<pre>
var type = 'pull'
var id = '96061'
netdna.del('/zones/' + type + '/' + id + '/upstream.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response68">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab68 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab69">
  <li class="active"><a href="#ruby69" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python69" data-toggle='tab'>Python</a></li>
  <li><a href="#php69" data-toggle='tab'>PHP</a></li>
  <li><a href="#node69" data-toggle='tab'>Node</a></li>
  <li><a href="#response69" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby69">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python69">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php69">
  	<pre>
$reportType = '';
$api->get('/reports/stats.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node69">
	<pre>
var reportType = ''
netdna.get('/reports/stats.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response69">
		<pre>
{
    "code": 200,
    "data": {
        "stats": {
            "cache_hit": "0",
            "hit": "20",
            "noncache_hit": "20",
            "size": "0"
        },
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab69 a:last').tab('show');
  })
</script>

---


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



### Code Samples

<ul class="nav nav-tabs" id="myTab70">
  <li class="active"><a href="#ruby70" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python70" data-toggle='tab'>Python</a></li>
  <li><a href="#php70" data-toggle='tab'>PHP</a></li>
  <li><a href="#node70" data-toggle='tab'>Node</a></li>
  <li><a href="#response70" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby70">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python70">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php70">
  	<pre>
$id = '96061';
$reportType = '';
$api->get('/reports/'.$id.'/stats.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node70">
	<pre>
var id = '96061'
var reportType = ''
netdna.get('/reports/' + id + '/stats.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response70">
		<pre>
{
    "code": 200,
    "data": {
        "stats": {
            "cache_hit": null,
            "hit": null,
            "noncache_hit": null,
            "size": null
        },
        "summary": {
            "cache_hit": null,
            "hit": null,
            "noncache_hit": null,
            "size": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab70 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab71">
  <li class="active"><a href="#ruby71" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python71" data-toggle='tab'>Python</a></li>
  <li><a href="#php71" data-toggle='tab'>PHP</a></li>
  <li><a href="#node71" data-toggle='tab'>Node</a></li>
  <li><a href="#response71" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby71">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python71">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php71">
  	<pre>
$api->get('/reports/nodes.json');</pre>
  </div>
  <div class="tab-pane" id="node71">
	<pre>
netdna.get('/reports/nodes.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response71">
		<pre>
{
    "code": 200,
    "data": {
        "nodes": [
            {
                "description": "Los Angeles",
                "id": "1",
                "name": "lax"
            },
            {
                "description": "New York",
                "id": "3",
                "name": "jfk"
            },
            {
                "description": "Seattle",
                "id": "2",
                "name": "sea"
            },
            {
                "description": "Atlanta",
                "id": "4",
                "name": "atl"
            },
            {
                "description": "Amsterdam",
                "id": "5",
                "name": "ams"
            },
            {
                "description": "Dallas",
                "id": "6",
                "name": "dal"
            },
            {
                "description": "Chicago",
                "id": "8",
                "name": "chi"
            },
            {
                "description": "Virginia",
                "id": "9",
                "name": "vir"
            },
            {
                "description": "Miami",
                "id": "7",
                "name": "mia"
            },
            {
                "description": "London",
                "id": "12",
                "name": "lhr"
            },
            {
                "description": "San Francisco",
                "id": "13",
                "name": "sfo"
            },
            {
                "description": "Los Angeles 3",
                "id": "30",
                "name": "lax"
            }
        ]
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab71 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab72">
  <li class="active"><a href="#ruby72" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python72" data-toggle='tab'>Python</a></li>
  <li><a href="#php72" data-toggle='tab'>PHP</a></li>
  <li><a href="#node72" data-toggle='tab'>Node</a></li>
  <li><a href="#response72" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby72">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python72">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php72">
  	<pre>
$id = '96061';
$api->get('/reports/'.$id.'/nodes.json');</pre>
  </div>
  <div class="tab-pane" id="node72">
	<pre>
var id = '96061'
netdna.get('/reports/' + id + '/nodes.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response72">
		<pre>
{
    "code": 200,
    "data": {
        "nodes": [
            {
                "description": "Dallas",
                "id": "6",
                "name": "dal"
            },
            {
                "description": "Los Angeles",
                "id": "1",
                "name": "lax"
            },
            {
                "description": "Seattle",
                "id": "2",
                "name": "sea"
            },
            {
                "description": "New York",
                "id": "3",
                "name": "jfk"
            },
            {
                "description": "Atlanta",
                "id": "4",
                "name": "atl"
            },
            {
                "description": "Amsterdam",
                "id": "5",
                "name": "ams"
            },
            {
                "description": "Chicago",
                "id": "8",
                "name": "chi"
            },
            {
                "description": "Virginia",
                "id": "9",
                "name": "vir"
            },
            {
                "description": "London",
                "id": "12",
                "name": "lhr"
            },
            {
                "description": "San Francisco",
                "id": "13",
                "name": "sfo"
            }
        ]
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab72 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab73">
  <li class="active"><a href="#ruby73" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python73" data-toggle='tab'>Python</a></li>
  <li><a href="#php73" data-toggle='tab'>PHP</a></li>
  <li><a href="#node73" data-toggle='tab'>Node</a></li>
  <li><a href="#response73" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby73">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python73">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php73">
  	<pre>
$reportType = '';
$api->get('/reports/nodes.json/stats/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node73">
	<pre>
var reportType = ''
netdna.get('/reports/nodes.json/stats/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response73">
		<pre>
{
    "code": 200,
    "data": {
        "stats": [
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "Los Angeles",
                "pop_id": "1",
                "pop_name": "lax",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "Atlanta",
                "pop_id": "4",
                "pop_name": "atl",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "Chicago",
                "pop_id": "8",
                "pop_name": "chi",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "San Francisco",
                "pop_id": "13",
                "pop_name": "sfo",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "Seattle",
                "pop_id": "2",
                "pop_name": "sea",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "Amsterdam",
                "pop_id": "5",
                "pop_name": "ams",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "Virginia",
                "pop_id": "9",
                "pop_name": "vir",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "New York",
                "pop_id": "3",
                "pop_name": "jfk",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "Dallas",
                "pop_id": "6",
                "pop_name": "dal",
                "size": "0"
            },
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "pop_description": "London",
                "pop_id": "12",
                "pop_name": "lhr",
                "size": "0"
            }
        ],
        "summary": {
            "cache_hit": "0",
            "hit": "20",
            "noncache_hit": "20",
            "size": "0"
        },
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab73 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab74">
  <li class="active"><a href="#ruby74" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python74" data-toggle='tab'>Python</a></li>
  <li><a href="#php74" data-toggle='tab'>PHP</a></li>
  <li><a href="#node74" data-toggle='tab'>Node</a></li>
  <li><a href="#response74" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby74">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python74">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php74">
  	<pre>
$id = '96061';
$reportType = '';
$api->get('/reports/'.$id.'/nodes.json/stats/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node74">
	<pre>
var id = '96061'
var reportType = ''
netdna.get('/reports/' + id + '/nodes.json/stats/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response74">
		<pre>
{
    "code": 200,
    "data": {
        "stats": [],
        "summary": {
            "cache_hit": null,
            "hit": null,
            "noncache_hit": null,
            "size": null
        },
        "total": null
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab74 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab75">
  <li class="active"><a href="#ruby75" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python75" data-toggle='tab'>Python</a></li>
  <li><a href="#php75" data-toggle='tab'>PHP</a></li>
  <li><a href="#node75" data-toggle='tab'>Node</a></li>
  <li><a href="#response75" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby75">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python75">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php75">
  	<pre>
$id = '1';
$api->get('/reports/nodes.json/'.$id);</pre>
  </div>
  <div class="tab-pane" id="node75">
	<pre>
var id = '1'
netdna.get('/reports/nodes.json/' + id, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response75">
		<pre>
{
    "code": 200,
    "data": {
        "node": {
            "description": "Los Angeles",
            "id": "1",
            "name": "lax"
        }
    }
}
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab75 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab76">
  <li class="active"><a href="#ruby76" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python76" data-toggle='tab'>Python</a></li>
  <li><a href="#php76" data-toggle='tab'>PHP</a></li>
  <li><a href="#node76" data-toggle='tab'>Node</a></li>
  <li><a href="#response76" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby76">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python76">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php76">
  	<pre>
$zoneId = '96061';
$nodeId = '1';
$api->get('/reports/'.$zoneId.'/nodes.json/'.$nodeId);</pre>
  </div>
  <div class="tab-pane" id="node76">
	<pre>
var zoneId = '96061'
var nodeId = '1'
netdna.get('/reports/' + zoneId + '/nodes.json/' + nodeId, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response76">
		<pre>
{
    "code": 200,
    "data": {
        "stats": [],
        "summary": {
            "cache_hit": null,
            "hit": null,
            "noncache_hit": null,
            "size": null
        },
        "total": null
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab76 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab77">
  <li class="active"><a href="#ruby77" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python77" data-toggle='tab'>Python</a></li>
  <li><a href="#php77" data-toggle='tab'>PHP</a></li>
  <li><a href="#node77" data-toggle='tab'>Node</a></li>
  <li><a href="#response77" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby77">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python77">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php77">
  	<pre>
$id = '1';
$reportType = '';
$api->get('/reports/nodes.json/'.$id.'/stats/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node77">
	<pre>
var id = '1'
var reportType = ''
netdna.get('/reports/nodes.json/' + id + '/stats/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response77">
		<pre>
{
    "code": 200,
    "data": {
        "stats": [
            {
                "cache_hit": "0",
                "hit": "2",
                "noncache_hit": "2",
                "size": "0"
            }
        ],
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab77 a:last').tab('show');
  })7
</script>

---


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



### Code Samples

<ul class="nav nav-tabs" id="myTab78">
  <li class="active"><a href="#ruby78" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python78" data-toggle='tab'>Python</a></li>
  <li><a href="#php78" data-toggle='tab'>PHP</a></li>
  <li><a href="#node78" data-toggle='tab'>Node</a></li>
  <li><a href="#response78" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby78">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python78">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php78">
  	<pre>
$zoneId='96061';
$nodeId='1';
$reportType = '';
$api->get('/reports/'.$zoneId.'/nodes.json/'.$nodeId.'/stats/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node78">
	<pre>
var zoneId = '96061'
var nodeId = '1'
var reportType = ''
netdna.get('/reports/' + zoneId + '/nodes.json/' + nodeId + '/stats/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response78">
		<pre>
{
    "code": 200,
    "data": {
        "stats": [
            {
                "cache_hit": null,
                "hit": null,
                "noncache_hit": null,
                "size": null
            }
        ],
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab78 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab79">
  <li class="active"><a href="#ruby79" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python79" data-toggle='tab'>Python</a></li>
  <li><a href="#php79" data-toggle='tab'>PHP</a></li>
  <li><a href="#node79" data-toggle='tab'>Node</a></li>
  <li><a href="#response79" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby79">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python79">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php79">
  	<pre>
$api->get('/reports/popularfiles.json');</pre>
  </div>
  <div class="tab-pane" id="node79">
	<pre>
netdna.get('/reports/popularfiles.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response79">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "popularfiles": [],
        "summary": {
            "hit": null,
            "size": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab79 a:last').tab('show');
  })
</script>

---


## List Popular Files By Zone Type

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



### Code Samples

<ul class="nav nav-tabs" id="myTab80">
  <li class="active"><a href="#ruby80" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python80" data-toggle='tab'>Python</a></li>
  <li><a href="#php80" data-toggle='tab'>PHP</a></li>
  <li><a href="#node80" data-toggle='tab'>Node</a></li>
  <li><a href="#response80" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby80">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python80">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php80">
  	<pre>
$type='pull';
$api->get('/reports/'.$type.'/popularfiles.json');</pre>
  </div>
  <div class="tab-pane" id="node80">
	<pre>
var type = 'pull'
netdna.get('/reports/' + type + '/popularfiles.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response80">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "popularfiles": [],
        "summary": {
            "hit": null,
            "size": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab80 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab81">
  <li class="active"><a href="#ruby81" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python81" data-toggle='tab'>Python</a></li>
  <li><a href="#php81" data-toggle='tab'>PHP</a></li>
  <li><a href="#node81" data-toggle='tab'>Node</a></li>
  <li><a href="#response81" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby81">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python81">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php81">
  	<pre>
$reportType = '';
$api->get('/reports/statuscodes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node81">
	<pre>
var reportType = ''
netdna.get('/reports/statuscodes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response81">
		<pre>
{
    "code": 200,
    "data": {
        "statuscodes": [
            {
                "definition": "Not Found",
                "hit": "20",
                "status_code": "404"
            }
        ],
        "summary": {
            "hit": "20"
        },
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab81 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab82">
  <li class="active"><a href="#ruby82" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python82" data-toggle='tab'>Python</a></li>
  <li><a href="#php82" data-toggle='tab'>PHP</a></li>
  <li><a href="#node82" data-toggle='tab'>Node</a></li>
  <li><a href="#response82" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby82">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python82">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php82">
  	<pre>
$reportType = '';
$id = '96061';
$api->get('/reports/'.$id.'/statuscodes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node82">
	<pre>
var reportType = ''
var id = '96061'
netdna.get('/reports/' + id + '/statuscodes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response82">
		<pre>
{
    "code": 200,
    "data": {
        "statuscodes": [],
        "summary": {
            "hit": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab82 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab83">
  <li class="active"><a href="#ruby83" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python83" data-toggle='tab'>Python</a></li>
  <li><a href="#php83" data-toggle='tab'>PHP</a></li>
  <li><a href="#node83" data-toggle='tab'>Node</a></li>
  <li><a href="#response83" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby83">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python83">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php83">
  	<pre>
$reportType = '';
$zoneType = 'pull';
$api->get('/reports/'.$zoneType.'/statuscodes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node83">
	<pre>
var reportType = ''
var zoneType = 'pull'
netdna.get('/reports/' + zoneType + '/statuscodes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response83">
		<pre>
{
    "code": 200,
    "data": {
        "statuscodes": [
            {
                "definition": "Not Found",
                "hit": "20",
                "status_code": "404"
            }
        ],
        "summary": {
            "hit": "20"
        },
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab83 a:last').tab('show');
  })
</script>

---


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



### Code Samples

<ul class="nav nav-tabs" id="myTab84">
  <li class="active"><a href="#ruby84" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python84" data-toggle='tab'>Python</a></li>
  <li><a href="#php84" data-toggle='tab'>PHP</a></li>
  <li><a href="#node84" data-toggle='tab'>Node</a></li>
  <li><a href="#response84" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby84">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python84">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php84">
  	<pre>
$reportType = '';
$zoneType = 'pull';
$id = '96061';
$api->get('/reports/'.$zoneType.'/'.$id.'/statuscodes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node84">
	<pre>
var reportType = ''
var zoneType = 'pull'
var id = '96061'
netdna.get('/reports/' + zoneType + '/' + id + '/statuscodes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response84">
		<pre>
{
    "code": 200,
    "data": {
        "statuscodes": [],
        "summary": {
            "hit": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab84 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab85">
  <li class="active"><a href="#ruby85" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python85" data-toggle='tab'>Python</a></li>
  <li><a href="#php85" data-toggle='tab'>PHP</a></li>
  <li><a href="#node85" data-toggle='tab'>Node</a></li>
  <li><a href="#response85" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby85">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python85">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php85">
  	<pre>
$reportType = '';
$api->get('/reports/filetypes.json'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node85">
	<pre>
var reportType = ''
netdna.get('/reports/filetypes.json', function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response85">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 1,
        "filetypes": [
            {
                "file_type": "txt",
                "hit": "20"
            }
        ],
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "summary": {
            "hit": "20"
        },
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab85 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab86">
  <li class="active"><a href="#ruby86" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python86" data-toggle='tab'>Python</a></li>
  <li><a href="#php86" data-toggle='tab'>PHP</a></li>
  <li><a href="#node86" data-toggle='tab'>Node</a></li>
  <li><a href="#response86" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby86">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python86">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php86">
  	<pre>
$reportType = '';
$id = '96061';
$api->get('/reports/'.$id.'/filetypes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node86">
	<pre>
var reportType = ''
var id = '96061'
netdna.get('/reports/' + id + '/filetypes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response86">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "filetypes": [],
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "summary": {
            "hit": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab86 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab87">
  <li class="active"><a href="#ruby87" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python87" data-toggle='tab'>Python</a></li>
  <li><a href="#php87" data-toggle='tab'>PHP</a></li>
  <li><a href="#node87" data-toggle='tab'>Node</a></li>
  <li><a href="#response87" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby87">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python87">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php87">
  	<pre>
$reportType = '';
$zoneType = 'pull';
$api->get('/reports/'.$zoneType.'/filetypes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node87">
	<pre>
var reportType = ''
var zoneType = 'pull'
netdna.get('/reports/' + zoneType + '/filetypes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response87">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 1,
        "filetypes": [
            {
                "file_type": "txt",
                "hit": "20"
            }
        ],
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "summary": {
            "hit": "20"
        },
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab87 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab88">
  <li class="active"><a href="#ruby88" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python88" data-toggle='tab'>Python</a></li>
  <li><a href="#php88" data-toggle='tab'>PHP</a></li>
  <li><a href="#node88" data-toggle='tab'>Node</a></li>
  <li><a href="#response88" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby88">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python88">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php88">
  	<pre>
$reportType = '';
$zoneType = 'pull';
$id = '96061';
$api->get('/reports/'.$zoneType.'/'.$id.'/filetypes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node88">
	<pre>
var reportType = ''
var zoneType = 'pull'
var id = '96061'
netdna.get('/reports/' + zoneType + '/' + id + '/filetypes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response88">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "filetypes": [],
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "summary": {
            "hit": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab88 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab89">
  <li class="active"><a href="#ruby89" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python89" data-toggle='tab'>Python</a></li>
  <li><a href="#php89" data-toggle='tab'>PHP</a></li>
  <li><a href="#node89" data-toggle='tab'>Node</a></li>
  <li><a href="#response89" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby89">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python89">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php89">
  	<pre>
$reportType = '';
$api->get('/reports/filesizes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node89">
	<pre>
var reportType = ''
netdna.get('/reports/filesizes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response89">
		<pre>
{
    "code": 200,
    "data": {
        "filesizes": [
            {
                "gt_100m_hit": "0",
                "le_100k_hit": "0",
                "le_100m_hit": "0",
                "le_10k_hit": "20",
                "le_10m_hit": "0",
                "le_1m_hit": "0",
                "le_500k_hit": "0",
                "le_50k_hit": "0"
            }
        ],
        "summary": {
            "hit": "20"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab89 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab90">
  <li class="active"><a href="#ruby90" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python90" data-toggle='tab'>Python</a></li>
  <li><a href="#php90" data-toggle='tab'>PHP</a></li>
  <li><a href="#node90" data-toggle='tab'>Node</a></li>
  <li><a href="#response90" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby90">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python90">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php90">
  	<pre>
$reportType = '';
$id = '96061';
$api->get('/reports/'.$id.'/filesizes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node90">
	<pre>
var reportType = ''
var id = '96061'
netdna.get('/reports/' + id + '/filesizes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response90">
		<pre>
{
    "code": 200,
    "data": {
        "filesizes": [
            {
                "gt_100m_hit": null,
                "le_100k_hit": null,
                "le_100m_hit": null,
                "le_10k_hit": null,
                "le_10m_hit": null,
                "le_1m_hit": null,
                "le_500k_hit": null,
                "le_50k_hit": null
            }
        ],
        "summary": {
            "hit": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab90 a:last').tab('show');
  })
</script>

---


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

### Code Samples

<ul class="nav nav-tabs" id="myTab91">
  <li class="active"><a href="#ruby91" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python91" data-toggle='tab'>Python</a></li>
  <li><a href="#php91" data-toggle='tab'>PHP</a></li>
  <li><a href="#node91" data-toggle='tab'>Node</a></li>
  <li><a href="#response91" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby91">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python91">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php91">
  	<pre>
$reportType = '';
$zoneType = 'pull';
$api->get('/reports/'.$zoneType.'/filesizes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node91">
	<pre>
var reportType = ''
var zoneType = 'pull'
netdna.get('/reports/' + zoneType + '/filesizes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response91">
		<pre>
{
    "code": 200,
    "data": {
        "filesizes": [
            {
                "gt_100m_hit": "0",
                "le_100k_hit": "0",
                "le_100m_hit": "0",
                "le_10k_hit": "20",
                "le_10m_hit": "0",
                "le_1m_hit": "0",
                "le_500k_hit": "0",
                "le_50k_hit": "0"
            }
        ],
        "summary": {
            "hit": "20"
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab91 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab92">
  <li class="active"><a href="#ruby92" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python92" data-toggle='tab'>Python</a></li>
  <li><a href="#php92" data-toggle='tab'>PHP</a></li>
  <li><a href="#node92" data-toggle='tab'>Node</a></li>
  <li><a href="#response92" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby92">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python92">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php92">
  	<pre>
$reportType = '';
$zoneType = 'pull';
$id = '96061';
$api->get('/reports/'.$zoneType.'/'.$id.'/filesizes.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node92">
	<pre>
var reportType = ''
var zoneType = 'pull'
var id = '96061'
netdna.get('/reports/' + zoneType + '/' + id + '/filesizes.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response92">
		<pre>
{
    "code": 200,
    "data": {
        "filesizes": [
            {
                "gt_100m_hit": null,
                "le_100k_hit": null,
                "le_100m_hit": null,
                "le_10k_hit": null,
                "le_10m_hit": null,
                "le_1m_hit": null,
                "le_500k_hit": null,
                "le_50k_hit": null
            }
        ],
        "summary": {
            "hit": null
        }
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab92 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab93">
  <li class="active"><a href="#ruby93" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python93" data-toggle='tab'>Python</a></li>
  <li><a href="#php93" data-toggle='tab'>PHP</a></li>
  <li><a href="#node93" data-toggle='tab'>Node</a></li>
  <li><a href="#response93" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby93">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python93">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php93">
  	<pre>
$reportType = '';
$api->get('/reports/statsbydir.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node93">
	<pre>
var reportType = ''
netdna.get('/reports/statsbydir.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response93">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "statsbydir": [],
        "summary": {
            "hit": null,
            "size": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab93 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab94">
  <li class="active"><a href="#ruby94" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python94" data-toggle='tab'>Python</a></li>
  <li><a href="#php94" data-toggle='tab'>PHP</a></li>
  <li><a href="#node94" data-toggle='tab'>Node</a></li>
  <li><a href="#response94" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby94">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python94">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php94">
  	<pre>
$reportType = '';
$id = '96061';
$api->get('/reports/'.$id.'/statsbydir.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node94">
	<pre>
var reportType = ''
var id = '96061'
netdna.get('/reports/' + id + '/' + '/statsbydir.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response94">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "statsbydir": [],
        "summary": {
            "hit": null,
            "size": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab94 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab95">
  <li class="active"><a href="#ruby95" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python95" data-toggle='tab'>Python</a></li>
  <li><a href="#php95" data-toggle='tab'>PHP</a></li>
  <li><a href="#node95" data-toggle='tab'>Node</a></li>
  <li><a href="#response95" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby95">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python95">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php95">
  	<pre>
$reportType = '';
$clientId = '';
$api->get('/clients/'.$clientId.'/reports/statsbyfilename.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node95">
	<pre>
var reportType = ''
var clientId = ''
netdna.get('/clients/' + clientId + '/reports/statsbyfilename.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response95">
		<pre>
{
    "code": 200,
    "data": {
        "statsbyfilename": [
            {
                "200": "0",
                "206": "0",
                "2xx": "0",
                "3xx": "0",
                "404": "0",
                "4xx": "0",
                "5xx": "35036",
                "bucket_id": "21597",
                "file_name": "/",
                "hit": "35036",
                "size": "20110664",
                "timestampf": "2013",
                "vhost": "edge02.nycacorp.netdna-cdn.com"
            },
            {
                "200": "0",
                "206": "0",
                "2xx": "0",
                "3xx": "0",
                "404": "0",
                "4xx": "2",
                "5xx": "35032",
                "bucket_id": "21597",
                "file_name": "/favicon.ico",
                "hit": "35034",
                "size": "20108368",
                "timestampf": "2013",
                "vhost": "edge02.nycacorp.netdna-cdn.com"
            }
        ],
        "summary": {
            "200": "0",
            "206": "0",
            "2xx": "0",
            "3xx": "0",
            "404": "0",
            "4xx": "2",
            "5xx": "70068",
            "hit": "70070",
            "size": "40219032"
        },
        "total": "2"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab95 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab96">
  <li class="active"><a href="#ruby96" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python96" data-toggle='tab'>Python</a></li>
  <li><a href="#php96" data-toggle='tab'>PHP</a></li>
  <li><a href="#node96" data-toggle='tab'>Node</a></li>
  <li><a href="#response96" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby96">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python96">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php96">
  	<pre>
$reportType = '';
$id = '96061';
$clientId = '';
$api->get('/clients/'.$clientId.'/reports/'.$id.'/statsbyfilename.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node96">
	<pre>
var reportType = ''
var id = '96061'
var clientId = ''
netdna.get('/clients/' + clientId + '/reports/' + id + '/statsbyfilename.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response96">
		<pre>
</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab96 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab97">
  <li class="active"><a href="#ruby97" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python97" data-toggle='tab'>Python</a></li>
  <li><a href="#php97" data-toggle='tab'>PHP</a></li>
  <li><a href="#node97" data-toggle='tab'>Node</a></li>
  <li><a href="#response97" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby97">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python97">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php97">
  	<pre>
$reportType = '';
$clientId = '';
$api->get('clients/'.$clientId.'/reports/statsbycustomdomain.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node97">
	<pre>
var reportType = ''
var clientId = ''
netdna.get('/clients/' + clientId + '/reports/statsbycustomdomain.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response97">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 1,
        "page": 1,
        "page_size": "50",
        "pages": 1,
        "statsbycustomdomain": [
            {
                "bucket_id": "21597",
                "custom_domain_id": "0",
                "hit": "70320",
                "size": "40362532",
                "vhost": "edge02.nycacorp.netdna-cdn.com"
            }
        ],
        "summary": {
            "hit": "70320",
            "size": "40362532"
        },
        "total": "1"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab97 a:last').tab('show');
  })
</script>

---


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


### Code Samples

<ul class="nav nav-tabs" id="myTab98">
  <li class="active"><a href="#ruby98" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python98" data-toggle='tab'>Python</a></li>
  <li><a href="#php98" data-toggle='tab'>PHP</a></li>
  <li><a href="#node98" data-toggle='tab'>Node</a></li>
  <li><a href="#response98" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby98">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python98">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php98">
  	<pre>
$reportType = '';
$zoneId = '';
$clientId = '';
$api->get('clients/'.$clientId.'/reports/'.$zoneId.'/statsbycustomdomain.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node98">
	<pre>
var reportType = ''
var zoneId = ''
var clientId = ''
netdna.get('/clients/' + clientId + '/reports/' + zoneId + '/statsbycustomdomain.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response98">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "statsbycustomdomain": [],
        "summary": {
            "hit": null,
            "size": null
        },
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab98 a:last').tab('show');
  })
</script>

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

### Code Samples

<ul class="nav nav-tabs" id="myTab99">
  <li class="active"><a href="#ruby99" data-toggle='tab'>Ruby</a></li>
  <li><a href="#python99" data-toggle='tab'>Python</a></li>
  <li><a href="#php99" data-toggle='tab'>PHP</a></li>
  <li><a href="#node99" data-toggle='tab'>Node</a></li>
  <li><a href="#response99" data-toggle='tab'>Response</a></li>
</ul>

<div class="tab-content">
  <div class="tab-pane active" id="ruby99">
		<pre>

		</pre>
  </div>
  <div class="tab-pane" id="python99">
		<pre>

		</pre>
	</div>
  <div class="tab-pane" id="php99">
  	<pre>
$reportType = '';
$api->get('/reports/live/connectionstats.json/'.$reportType);</pre>
  </div>
  <div class="tab-pane" id="node99">
	<pre>
var reportType = ''
netdna.get('/reports/live/connectionstats.json/' + reportType, function(err, response) {
  console.log('err', err, 'response', response)
})</pre>
  </div>
  <div class="tab-pane" id="response99">
		<pre>
{
    "code": 200,
    "data": {
        "current_page_size": 0,
        "page": 1,
        "page_size": "50",
        "pages": 0,
        "stats": [],
        "total": "0"
    }
}</pre>
  </div>
</div>

<script>
  $(function () {
    $('#myTab99 a:last').tab('show');
  })
</script>

---

[@niftylettuce](https://github.com/niftylettuce) was here.
