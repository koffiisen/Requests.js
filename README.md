# Requests.js

HTTP client for the browser

## Features

- Make [XMLHttpRequests](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) from the browser
- Supports the [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) API

## Browser Support

![Chrome](https://raw.github.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png) | ![Firefox](https://raw.github.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png) | ![Safari](https://raw.github.com/alrra/browser-logos/master/src/safari/safari_48x48.png) | ![Opera](https://raw.github.com/alrra/browser-logos/master/src/opera/opera_48x48.png) | ![Edge](https://raw.github.com/alrra/browser-logos/master/src/edge/edge_48x48.png) | ![IE](https://raw.github.com/alrra/browser-logos/master/src/archive/internet-explorer_9-11/internet-explorer_9-11_48x48.png) |
--- | --- | --- | --- | --- | --- |
Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | Latest ✔ | 11 ✔ |


## Installing

```html
<script src="dist/requests.min.js"></script>
```

## Example

```js
var r = new Requests()
```

##### Performing a `GET` request

```js
r.get("https://api.github.com/events").then(function (g) {
        console.log(g.json());
    }).catch(function (err) {
        console.log("error : ", err)
    });
```

##### Performing a `POST` request

```js
r.post('https://httpbin.org/post', {data: {'key': 'value'}}).then(function (p) {
        console.log(p);
    }).catch(function (err) {
        console.log("error : ", err)
    });
```

## Requests response return

````js
response.status_code,
response.content,
response.json(),
response.xml(),
response.blob(),
response.buffer(),
response.text,
response.type,
response.headers,
response.url,
response.getHeader(s),
response.history
````

## Requests API

##### Requests(url[, config])

```js
    var options = {
        async: true,
        auth: null, // BasicAuth(username,password) or TokenAuth(token)
        data: null, // can be formData or JSON.stringify(dd)
        headers: {'X-Requested-With': 'XMLHttpRequest'},
        responseType: responseType.default,
        timeout: 0,
        withCredentials: false
    };
```

### Requests method

* ###### Request#request(method,url[, config])
* ###### Request#get(url[, config])
* ###### Request#delete(url[, config])
* ###### Request#head(url[, config])
* ###### Request#options(url[, config])
* ###### Request#post(url[, data[, config]])
* ###### Request#put(url[, data[, config]])
* ###### Request#patch(url[, data[, config]])
* ###### Request#ping(ip,callback)
* ###### Request#HTMLSession

## Request ~ HTMLSession

```js
    //var html_session = new Requests().HTMLSession();
    var html_session = new HTMLSession();
        var hss = html_session.get("https://getbootstrap.com/docs/4.0/components/input-group/", true);
        hss.then(function (session) {
            console.log(session);
            var txt = session.search("Button addons");
            var element = session.find("#elemID");
            var class_name = session.find(".className");
            var pageTitle = session.title;
            console.log(txt);
        });
```

* ###### HTMLSession#find(query)
* ###### HTMLSession#findAll(query)
* ###### HTMLSession#find(query)
* ###### HTMLSession#findAllByTagName(tag)
* ###### HTMLSession#getAttrs(elem)
* ###### HTMLSession#html
* ###### HTMLSession#links
* ###### HTMLSession#search
* ###### HTMLSession#searchTagByText
* ###### HTMLSession#title


### Extra ~ Ping
```js
new Requests().ping("localhost", function (status, e) {
            console.log("PING", status)
        })
// status : responded | timeout
```

### Auto export

````js

window.Requests = Requests;
window.HTMLSession = new Requests().HTMLSession;
// currently is disable. Just copy and paste to your main.js
window.get = new Requests().get;
window.post = new Requests().post;
window.put = new Requests().put;
window.patch = new Requests().patch;
window.head = new Requests().head;
window.options = new Requests().options;
window.delete = new Requests().delete;
window.request = new Requests().request;
window.ping = new Requests().ping;
// End of disable
````

## License

[MIT](LICENSE)