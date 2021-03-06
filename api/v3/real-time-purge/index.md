# Real-Time **Purge**

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/api/v3/real-time-purge/index.md)

If you need to delete an object from the Edge Caching or L2 Caching layers before it expires, you can use the Real-Time Purge API. If desired, integrate the Azion API with your CMS to automate your content update processes.

See below how to:

> 1. [Create a URL Purge request](#criar-uma-solicitacao-de-url-purge)
> 2. [Create a Cache Key Purge request](#criar-uma-solicitacao-de-cache-key-purge)
> 3. [Create a Wildcard Purge request](#criar-uma-solicitacao-de-wildcard-purge)

---

## 1. Create a URL Purge request {#criar-uma-solicitacao-de-url-purge}

To delete a list of objects from Azion's Edge Caching layer through their URLs, you can use the endpoint:

#### **POST**  */purge/url*

Required permission: **Purge**

| Parameter | Description | Type of Parameter | Type of Data |
|--------|--------|--------|--------|
| Authorization (required) | Token authentication previously created through the [Token Creation]({% tl api_v3_authentication %}#criacao-de-token) endpoint. <br><br>e.g.: <br><br>Authorization: Token 583f8a9ca8d6d5ff2cb50f1d3c4d35cb8939f1bf | header | string |
| Content-Type (required) | The type of encoding used in Body (application/json).<br><br>e.g.: <br><br>Content-Type: application/json | header | string |
| Body (required) | List of URLs you want to remove from the Azion Edge Servers cache. <br><br>**urls** (array): list of up to 50 URLs to be expired from the cache, per request.<br><br>**method** (choice): purge method, use the “delete” value for removal. | body | json |

**Request Example**

~~~
POST /purge/url
Accept: application/json; version=3
Authorization: Token 583f8a9ca8d6d5ff2cb50f1d3c4d35cb8939f1bf
Content-Type: application/json
~~~

~~~
{
    "urls": [
       "http://www.domain.com/", 
       "http://www.domain.com/test.js", 
       "http://static.mistaken-domain.com/image1.jpg"
    ],
    "method": "delete"
 }
 ~~~

 **Answer Example**

 ~~~
 HTTP/1.1 207 MULTI-STATUS
[
   {
      "status": "HTTP/1.1 201 CREATED",
      "urls": [
         "http://www.domain.com/", 
         "http://www.domain.com/test.js"
      ],
      "details": "Purge request successfully created"
   },
   {
      "status": "HTTP/1.1 403 FORBIDDEN",
      "urls": ["http://static.mistaken-domain.com/image1.jpg"],
      "details": "Unauthorized domain for your account"
   }
]
~~~

---

## 2. Create a Cache Key Purge request {#criar-uma-solicitacao-de-cache-key-purge}

To delete a list of objects from Azion's Edge Caching or L2 Caching layers through their Cache Keys, you can use the endpoint:

#### **POST** */purge/cachekey*

Required permission: **Purge**

| Parameter | Description | Type of Parameter | Type of Data |
|--------|--------|--------|--------|
| Authorization (required) | Token authentication previously created through the [Token Creation]({% tl api_v3_authentication %}#criacao-de-token) endpoint. <br><br>e.g.: <br><br>Authorization: Token 583f8a9ca8d6d5ff2cb50f1d3c4d35cb8939f1bf | header | string |
| Content-Type (required) | The type of encoding used in Body (application/json).<br><br>e.g.: <br><br>Content-Type: application/json | header | string |
| Body (required) | List of Cache Keys you want to remove from the Azion Edge Servers cache. <br><br>**urls** (array):list of up to 50 Cache Keys to be expired from the cache, per request.<br><br>**method** (choice): purge method, use the “delete” value for removal.<br><br>**Layer** (choice):layer where the purge will be done. Use the value "edge_caching" (default value if not informed) to purge on the Edge Caching layer and the value "l2_caching" to purge on L2 Caching. | body | json |

**Request Example**

~~~
POST /purge/cachekey
Accept: application/json; version=3
Authorization: Token 583f8a9ca8d6d5ff2cb50f1d3c4d35cb8939f1bf
Content-Type: application/json
~~~

~~~
{
    "urls": [
       "http://www.domain.com/@@cookie_name=cookie_value", 
       "http://www.domain.com/test.js", 
       "http://static.domain.com/image1.jpg?ims=arguments@@variants"
    ],
    "method": "delete",
    "layer": "l2_caching"

 }
 ~~~

 **Answer Example**

 ~~~
 HTTP/1.1 201 CREATED
{
    "details": "Purge request successfully created"
}
~~~

---

## 3. Create a Wildcard Purge request {#criar-uma-solicitacao-de-wildcard-purge}

To delete a list of objects from Azion's Edge Caching layer through a Wildcard URL or Wildcard Cache Key, you can use the endpoint:

#### **POST** */purge/wildcard*

Required permission: **Purge**

| Parameter | Description | Type of Parameter | Type of Data |
|--------|--------|--------|--------|
| Authorization (required) | Token authentication previously created through the [Token Creation]({% tl api_v3_authentication %}#criacao-de-token) endpoint. <br><br>e.g.: <br><br>Authorization: Token 583f8a9ca8d6d5ff2cb50f1d3c4d35cb8939f1bf | header | string |
| Content-Type (required) | The type of encoding used in Body (application/json).<br><br>e.g.: <br><br>Content-Type: application/json | header | string |
| Body (required) | The Wildcard expression that represents the list of objects that you want to remove from the Azion Edge Servers cache. <br><br>**urls** (array):the Wildcard URL or Wildcard Cache Key that represents the list of objects you want to expire. You can only use one Wildcard expression per request.<br><br>**method** (choice): purge method, use the “delete” value for removal. | body | json |

**Request Example**

~~~
POST /purge/wildcard
Accept: application/json; version=3
Authorization: Token 583f8a9ca8d6d5ff2cb50f1d3c4d35cb8939f1bf
Content-Type: application/json
~~~

~~~
{
    "urls": ["http://www.domain.com/path/image.jpg*"],
    "method": "delete"
 }
 ~~~

 **Answer Example**

 ~~~
 HTTP/1.1 201 CREATED
{
    "detail": "Purge request successfully created"
}
~~~

---

Didn't find what you were looking for? [Open a ticket.](https://tickets.azion.com/)