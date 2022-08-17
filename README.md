# DewChain-README
Enterprise-grade distributed ledger software solutions provide modularity and versatility for a broad industry use case. Its modular architecture accommodates the diversity of enterprise use cases through [REST-APIs](https://en.wikipedia.org/wiki/Representational_state_transfer).




## SignUP
Create a new account using the email, password and full name.

<img width="1385" alt="Screenshot 2022-08-09 at 2 34 16 PM" src="https://user-images.githubusercontent.com/59052352/183609940-4e448c42-9278-4d8f-b49d-59ce2d3538ee.png">




## Keys
Generate **Asymmetric Key(Public Key and Private Key)** for the **JSON Web Tokens (JWT Tokens)** Algorithm **ES256**. 🗝️
    
**Cryptography Type:** Elliptic Curve Cryptography (ECC) 🔒
    
### Request Body Details
    
* **email** (Email Address). 📨
* **password** (Email Password). 📨🔒
* **enc_password** (Password for Encrypting ECC Private Key). 🗝️ 🔐

<img width="1385" alt="Screenshot 2022-08-09 at 2 48 08 PM" src="https://user-images.githubusercontent.com/59052352/183612874-919c6034-78bd-4ae6-8223-67a75d89efaf.png">


### Server Responce
<img width="1385" alt="Screenshot 2022-08-09 at 2 47 31 PM" src="https://user-images.githubusercontent.com/59052352/183614258-4dca1ca9-e573-4499-b811-860e4093fa92.png">




## Token
Generate OAuth2 Access Token for API Authentication. 🪪

**Token Type:** Bearer

### Request Body Details

* **username** (Please enter your Email Address). 📨
* **password** (Please enter your Email Password). 📨🔒
* **client_id** (Please enter Encrypted _Private Key_ hear. You can get it from the GET "create_token_key" Endpoint). 🔑
* **client_secret** (Please enter the password used for Encrypting Key. Password entered inside "enc_password" request body during GET "create_token_key" Endpoint). 🔐


<img width="1385" alt="Screenshot 2022-08-09 at 3 01 37 PM" src="https://user-images.githubusercontent.com/59052352/183620876-3e8ffeb0-0f59-4376-b808-dce488ef6716.png">


### Server Responce
<img width="1385" alt="Screenshot 2022-08-09 at 3 22 39 PM" src="https://user-images.githubusercontent.com/59052352/183621119-b36ce783-34fb-4f81-b091-813990406a25.png">


#### _(Here, the **OAuth2 access token** is not required for authorization as it is auto-generated and used after authentication using the 'Authorize' button above.)_
<img width="169" alt="Screenshot 2022-08-09 at 3 43 46 PM" src="https://user-images.githubusercontent.com/59052352/183624044-fab29c52-3ea4-40e6-b367-1ad4dd27f0b1.png">




## Step-By-Step Guide of API Authentication :

* **Step 1:** Click the **Authorize** Button above.
* **Step 2:** Enter your **Email Address and Password** inside the **"username" and "password"** text box.
* **Step 3:** Select **Request body** from **"Client credential location"** drop-down menu.
* **Step 4:** Enter **Encrypted Private Key** inside **"client_id"** text box. You can get it from the GET **create_token_key** Endpoint.
* **Step 5:** Enter the password used for Encrypting Key inside **"client_secret"** text box. Password entered inside **"enc_password"** request body during GET **create_token_key** Endpoint.
* **Step 6:** Press **Authorize** Button.

<img width="1440" alt="Screenshot 2022-08-09 at 4 09 54 PM" src="https://user-images.githubusercontent.com/59052352/183630592-a4772889-b123-4a31-b17e-3b8467f7ffb3.png">




## Wallet
Wallet allows **Cryptographically Signed / Verify Data and the Block.**


### Authorization Required!
<img width="1384" alt="Screenshot 2022-08-09 at 4 00 17 PM" src="https://user-images.githubusercontent.com/59052352/183627803-d9b7a04c-b79d-4864-8da7-880fa6bd3ad7.png">



### Parameters

* **public-token-key** (Please enter _Public Key_ hear. You can get it from the GET "create_token_key" Endpoint). 🔑
* **enc_password** (Password for Encrypting Wallet).👜 🔒


<img width="1384" alt="Screenshot 2022-08-09 at 3 55 09 PM" src="https://user-images.githubusercontent.com/59052352/183631450-d8207f04-81f6-44f1-afe7-1b10437d0bb1.png">


### Server Responce

<img width="1383" alt="Screenshot 2022-08-09 at 4 27 27 PM" src="https://user-images.githubusercontent.com/59052352/183631679-8fb4d07f-52ed-46ed-a85b-0695b8186575.png">




## Data Model
Data Model allows for **Validating Data Proposal**. ✅


### Parameters
* **public-token-key** (Please enter _Public Key_ hear. You can get it from the GET "create_token_key" Endpoint). 🔑
* **Request Body** (Please enter **NodeURLs** and **UserModel** for Data Validation.). 📖

<img width="1383" alt="Screenshot 2022-08-11 at 4 29 09 PM" src="https://user-images.githubusercontent.com/59052352/184119147-afb3273b-1ab6-4a13-a801-69965683cf25.png">


**application/json**

```javascript
{
  "NodeUrls": {
    "node_url_1": "postgres://postgres:password@localhost:5432/Node_1",
    "node_url_2": "postgres://postgres:password@localhost:5432/Node_2",
    "node_url_3": "postgres://postgres:password@localhost:5432/Node_3"
  },
  "UserModel": {
  "title": "Person",
  "type": "object",
  "properties": {
    "first_name": {
      "type": "string",
      "description": "The person's first name."
    },
    "last_name": {
      "type": "string",
      "description": "The person's last name."
    },
    "age": {
      "description": "Age in years.",
      "type": "integer",
      "minimum": 0
    },
    "pets": {
      "type": "object"
    },
    "comment": {
      "type": "string"
    }
  }
}
}
```

### NodeURLs

Use SQL DB as a node.

```javascript

"NodeURLs": 
{
    "node_url_1": "postgres://postgres:password@localhost:5432/Node_1",
    "node_url_2": "postgres://postgres:password@localhost:5432/Node_2",
    "node_url_3": "postgres://postgres:password@localhost:5432/Node_3"
}

```

#### DewChain currently supports the following databases as Nodes:

* PostgreSQL >= 9.4
* MySQL
* MariaDB

##### Node_URL
DewChain supports specifying Database configuration in a URL form.

The form is:

``
DB_TYPE://USERNAME:PASSWORD@HOST:PORT/DB_NAME?PARAM1=value&PARAM2=value
``

If password contains special characters it need to be URL encoded:

```python

>>> import urllib.parse
>>> urllib.parse.quote_plus("kx%jj5/g")
'kx%25jj5%2Fg'


```
The supported **DB_TYPE**

``
postgres:
``

    Typically in the form of ``postgres://postgres:pass@db.host:5432/somedb``

``
mysql:
``

     Typically in the form of ``mysql://myuser:mypass@db.host:3306/somedb``
     
``
mariadb
``

    Typically in the form of ``mariadb://myuser:mypass@db.host:3306/somedb``
    
   
### UserModel
We use [JSON schema](https://json-schema.org/) to describe the structure and validation constraints of data.


```javascript

"UserModel": 
{
  "title": "Person",
  "type": "object",
  "properties": {
    "first_name": {
      "type": "string",
      "description": "The person's first name."
    },
    "last_name": {
      "type": "string",
      "description": "The person's last name."
    },
    "age": {
      "description": "Age in years.",
      "type": "integer",
      "minimum": 0
    },
    "pets": {
      "type": "object"
    },
    "comment": {
      "type": "string"
    }
  }
}

```




## Data
Data is stored **Provisionally and Encrypted** in the **Transaction Pool** for _future use_. 🔒💾

### Parameters

* **public-token-key** (Please enter _Public Key_ hear. You can get it from the GET "create_token_key" Endpoint). 🔑
* **private_key** (Please enter **Wallet Encrypted Private Key** hear.  You can get it from the GET "create_wallet_key" Endpoint). 👜 🗝️ 🔐
* **key_id** (Please enter **Wallet Key Id** hear. You can get it from the GET "create_wallet_key" Endpoint).👜 🔑 🆔
* **enc_password** (Please enter the **Password** used for **Encrypting Wallet**. Password entered inside "enc_password" request body during GET "create_wallet_key" Endpoint).👜 🔐
* **header** (This section is **optional**. This section stores some essential **metadata** about the transaction).
* **proposal** (Please enter your data in **JSON** format. PPlease validate the data based on your Data Model.). 📚

### _(We use Private key for **Data Signature**)_

<img width="1383" alt="Screenshot 2022-08-09 at 6 06 28 PM" src="https://user-images.githubusercontent.com/59052352/184116049-06f97466-abdd-4df3-b21e-df4bad7a3051.png">

### proposal

Enter data in JSON format. Please validate the data based on your Data Model.

(YES, I know this data doesn't make any sense. STOP taking everything so seriously!)

```javascript
{
  'comment': 'null',
  'first_name': 'hi',
  'last_name': 'yo',
  'age': 433,
  'pets': {
    'name': 'sdsd',
    'age': 433
  }
}
```

### Server Responce
<img width="1383" alt="Screenshot 2022-08-09 at 6 06 49 PM" src="https://user-images.githubusercontent.com/59052352/184121670-6ddb5c35-4513-436f-abef-4f39eaa7f306.png">




## Mine Block
**Add Transaction** to the **Distributed Ledger.**

### Parameters

* **data_uid** (Please enter **data_uid**).
* **public-token-key** (Please enter _Public Key_ hear. You can get it from the GET "create_token_key" Endpoint). 🔑
* **private_key** (Please enter **Wallet Encrypted Private Key** hear.  You can get it from the GET "create_wallet_key" Endpoint). 👜 🗝️ 🔐
* **key_id** (Please enter **Wallet Key Id** hear. You can get it from the GET "create_wallet_key" Endpoint).👜 🔑 🆔
* **enc_password** (Please enter the **Password** used for **Encrypting Wallet**. Password entered inside "enc_password" request body during GET "create_wallet_key" Endpoint).👜 🔐

### _(We use Private key for **Block Signature**)_

<img width="1383" alt="Screenshot 2022-08-09 at 6 13 07 PM" src="https://user-images.githubusercontent.com/59052352/184124215-03fe3a9d-abdd-4c78-aa3a-8b3e7611575c.png">

### Server Responce

<img width="1383" alt="Screenshot 2022-08-09 at 6 13 50 PM" src="https://user-images.githubusercontent.com/59052352/184124782-3ed05b6c-7b2d-474b-9e56-58dc76c76715.png">




## Broadcast Transaction
**Broadcast Transaction** across the **nodes.** 📢


### Parameters
* **index** (Block Index)
* **public-token-key** (Please enter _Public Key_ hear. You can get it from the GET "create_token_key" Endpoint). 🔑
* **[NodeURLs](https://github.com/tusharyadav511/DewChain-README/blob/main/README.md#nodeurls)**

```javascript
{
    "node_url_1": "postgres://postgres:password@localhost:5432/Node_1",
    "node_url_2": "postgres://postgres:password@localhost:5432/Node_2",
    "node_url_3": "postgres://postgres:password@localhost:5432/Node_3"
}
```

<img width="1383" alt="Screenshot 2022-08-09 at 9 39 46 PM" src="https://user-images.githubusercontent.com/59052352/184327584-1b4136f6-6db1-4417-91b4-aa9d4ffe3a3f.png">

















