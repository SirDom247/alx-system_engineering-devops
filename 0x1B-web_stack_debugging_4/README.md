This directory contains files for testing how well my web server setup featuring Nginx is doing under pressure. I'm using ApacheBench which allows me to simulate HTTP requests to a web server. In this case, I will make 2000 requests to my server with 100 requests at a time. Usage: ab -c 100 -n 2000 localhost/

