### REST Architecture

A simple example of a request throught a web browser

``` 
GET /tarragona.html HTTP/1.1
Host: www.eltiempo.es
Cache-Control: no-cache

...
<!doctype html>
<html lang="es">
....
<script>popup_temp="21&deg;C"; popup_forecast="Nuboso"</script>

...
Cache-Control → max-age=600, public
Content-Type → text/html; charset=utf-8
ETag → W/"2f1ab748966f126a254040ad6b1f3482"
```