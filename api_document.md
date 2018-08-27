# API Document

This is the api document for *URLHits* website.

We use `Express.js` for our backend framework and `mongodb` for database.

## Show Category 
    Returns json data about category list by month.

* **URL**

    */category/:time*

* **Method**

    `GET`
  
* **URL Params**

    Required: `time=[string]`
 

* **Response**

  * **Code:** `200` <br />
      
    **Content:** 
        
        {"category":["Sports > Basketball","Sports","Games > Online"] }
 

* **Sample Call**

    ```javascript
    fetch('/category/'+date)
        .then(res => res.json())
        .then(Cate => {
            // code block
        });
    ```
----

## Show Monthly Data Filtered by Category
    Returns json array data about month URL clicks filtered by category for one month.

* **URL**

    */month/:time/:cate*

* **Method**

    `GET`
  
* **URL Params**

    Required: `time=[string] / cate=[string]`
 

* **Response**

  * **Code:** `200` <br />
      
    **Content:** 
        
        { [{"url":"imageproxy.pimg.tw","clicktimes":193868,"category":"Sports"},{"url":"pic.pimg.tw","clicktimes":2734,"category":"Sports"}] }
 

* **Sample Call**

    ```javascript
   fetch('/'+text+'/'+date+'/'+cate)
        .then(res => res.json())
        .then(web => this.setState({ web: web }))
    ```
----

## Show URL Trend
    Returns json array data about specific URL daily click times for one month.

* **URL**

    */poly/:url/:time*

* **Method**

    `GET`
  
* **URL Params**

    Required: `url=[string] / time=[string]`

* **Response**

  * **Code:** `200` <br />
  
    **Content:** 
        
        { [{"clicktimes":[126108,111101,107999,121823]}] }
 
* **Sample Call**

    ```javascript
    fetch('/poly/'+url+'/'+date)
        .then(res => res.json())
        .then((Poly) => {
            var data = [];
            for (var i in Poly[0].clicktimes){
                data.push({ date: parseInt(i, 10)+1, clicks: Poly[0].clicktimes[i]}); 
            }
            // code block
        });
    ```
----

## Show previous and next Route
    Returns json array data about specific URL previous and next top 3 Route data for one month.

* **URL**

    */route/:url/:time*

* **Method**

    `GET`
  
* **URL Params**

    Required: `url=[string] / time=[string]`
 

* **Response**

  * **Code:** `200` <br />
      
    **Content:** 
        
        { [{"ref":[{"ref":"dns.weixin.qq.com","times":167168} ... ]"des":[{"des":"hkminorshort.weixin.qq.com","times":312296} ... ]}] }
 

* **Sample Call**

    ```javascript
    fetch('/route/'+url+'/'+date)
        .then(res => res.json())
        .then((Route) => {
            var refdata = [];
            var desdata = [];
            Route[0].ref.forEach(item => {
                refdata.push({ref: item.ref, times: item.times}); 
            });
            Route[0].des.forEach(item => {
                desdata.push({des: item.des, times: item.times}); 
            });
            // code block
        });
    ```
----

## Show Specific URL clicks 
    Returns json array data about specific URL clicks by month.

* **URL**

    */specific/:url/:time*

* **Method**

    `GET`
  
* **URL Params**

    Required: `url=[string] / time=[string]`
 

* **Response**

  * **Code:** `200` <br />
      
    **Content:** 
       
        { [{"url":"hkextshort.weixin.qq.com","clicktimes":2835719}] }
 

* **Sample Call**

    ```javascript
    fetch('/specific/'+url+'/'+date)
        .then(res => res.json())
        .then(Specific => this.setState({ clicks:  Specific[0].clicktimes}));
    ```
----

## Show Day/Week/Month URL clicks
    Returns json array data about top 100 day/week/month URL clicks by interval users choose.

* **URL**

    */:interval/:time*

* **Method**

    `GET`
  
* **URL Params**

    Required: `interval=[string] / time=[string]`
 

* **Response**

  * **Code:** `200` <br />
      
    **Content:** 
       
        { [{"url":"hkextshort.weixin.qq.com","clicktimes":137167},{"url":"hkminorshort.weixin.qq.com","clicktimes":126108}... }
 

* **Sample Call**

    ```javascript
    fetch('/'+interval+'/'+date)
        .then(res => res.json())
        .then(web => this.setState({ web: web }))
    ```
