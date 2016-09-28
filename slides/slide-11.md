### REST Architecture

What's that uniform interface.

* It's **resource** oriented not like *SOAP* or *RMI* or *CORBA*
* Each resource has a <span style="color:lightgreen">Uniform Resource Identifier</span>, the URI
* The server has to define a media type, like HTML, JSON, XML, etc.
* In HTTP, we'll use a verb for each type of request on a specific resource: <span style="color:lightgreen">GET, PUT, POST, PATCH, DELETE, PURGE, etc.</span> and it's defined by the server
* The server has to define the interface, HATEOAS Principle  (Hypermedia as the Engine of Application State)
* Has to be hypermedia or hypertext enabled using links (explicit or markup)

