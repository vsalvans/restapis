<section><pre>
<h3>REST Architecture:&nbsp;&nbsp;&nbsp;&nbsp;Hipermedia and HATEOAS</h3>
Request:
```
GET /
Accept: application/json+userdb
```
Response:
```
200 OK
Content-Type: application/json+userdb
{
    "version": "1.0",
    "links": [{
            "href": "/user",
            "rel": "list",
            "method": "GET"
        },{
            "href": "/user",
            "rel": "create",
            "method": "POST"
        }
    ]
}
```
</pre>
</section>
<section>
<pre>
<h4>RESTFul API Hipermedia enabled with hipermedia controls</h4>
Request:
```
GET /user
Accept: application/json+userdb
```
Response:
```
200 OK
Content-Type: application/json+userdb

{
"users": [{
    "id": 1,
    "name": "Emil",
    "country: "Sweden",
    "links": [{ "href": "/user/1", "rel": "self", "method": "GET"},
        {"href": "/user/1", "rel": "edit","method": "PUT"},
        {"href": "/user/1", "rel": "delete", "method": "DELETE"}]
}, {...}],
"links": [{"href": "/user", "rel": "create", "method": "POST"}]
}
```
</pre>
</section>
<section>
<pre>
<h4>RESTFul API example POSTing a new user</h4>Request:
```
POST /user
Accept: application/json+userdb
Content-Type: application/json+userdb
{
    "name": "Karl",
    "country": "Austria"
}
```
Response:
```
201 Created
Content-Type: application/json+userdb
{
    "user": {
        "id": 3,
        "name": "Karl",
        "country": "Austria",
        "links":[{ "href": "/user/3", "rel": "self", "method": "GET"},
        {"href": "/user/3", "rel": "edit","method": "PUT"},
        {"href": "/user/3", "rel": "delete", "method": "DELETE"}]
	},
	"links": [{"href": "/user", "rel": "create", "method": "POST"}]
}
```
</pre>
</section>
<section>
<pre>
	<h3>What about relations among resources?</h3>
Retrieves list of comments for post #12
```
GET /post/12/comments 
```
Retrieves comment #5 for post #12
```
GET /post/12/comments/5
```
Creates a new comment in post #12 
```
POST /post/12/comments 
```
Updates comment #5 for post #12
```
PUT /post/12/comments/5 
```
Partially updates comment #5 for post #12
```
PATCH /post/12/comments/5 
```
Deletes comment #5 for post #12
```
DELETE /post/12/comments/5
```
</pre>
</section>
<section>
	<h3>What about filters?</h3>
There is no a standard and is not part of RESTFul architecture
because it's low-grained oriented to leverage <strong>cacheability,
scalability and code-on-demand</strong>.
But it's most agree to use them in the query string
<pre>
Retrieves the second page of posts with tag 'tgndevs'

```
GET /post?page=2&tag=tgndevs
```
</pre>
</section>
<section>
    <h3>What about versioning?</h3>
There is no a standard and is not part of RESTFul architecture, again
it helps to keep a uniform interface and introduce new features 
without breaking API Consumers
<p></p>
<ul>
<li>Use an uri parameter <code style="color: lightgreen;">/v1/users</code></li>
<li>Use a query parameter <code style="color: lightgreen;">/users?version=v1</code></li>
<li>Use a custom mime-type with an Accept header <code style="color: lightgreen;">Accept: application/json; version=1.0</code></li>
<li>Use a custom header <code style="color: lightgreen;">X-Accept-Version: v1</code></li>
</ul>

</section>
<section>
<pre><h3>What about actions that can't be mapped in a HTTP verb</h3><ul style="width: 70%"><li class="fragment">Be creative like this example. GitHub's API lets you star a gist with <code>PUT /gists/:id/star</code> and unstar with <code>DELETE /gists/:id/star</code></li>
		<li class="fragment">You souldn't but... we have to be pragmatic... for instance <code>GET /search</code></li></ul><p class="fragment">It's ok as long as you make API consumer happy but most important documented cleary <img src="resources/images/happy.gif" width="250" style="margin-left: 30%"></p>
</pre>
</section>