<h1>Application server</h1>

<p>This was the application deployment project for our AirBnB clone. In this project, I configured Nginx on the web servers provided me by ALX to serve a WSGI Flask app running through Gunicorn. Additionally, I set up an Upstart script to keep the application running on server reboots.</p>
<h3>Task</h3>
<li>0. Set up development with Python</li>
   <li>In this task, I configured the file web_flask/0-hello_route.py from my AirBnB_clone_v2 to serve content on the route /airbnb-onepage/, running on port 5000.</li>
<li><b>1. Set up production with Gunicorn</li>
   <li>This task involved setting up a production environment, installing and configuring Gunicorn to serve the same file from task 0.</li>
<li><b>2. Serve a page with Nginx</li>
   <li>2-app_server-nginx_config: Nginx configuration file proxying requests on the route /airbnb-onepage/ to the Gunicorn app running on port 5000.</li>
<li><b>3. Add a route with query parameters</li>
   <li>3-app_server-nginx_config: Nginx configuration file proxying requests on the route /airbnb-dynamic/number_odd_or_even/<int: num> to the Gunicorn app running on port 5000.</li>
<li><b>4. Let's do this for your API</li>
   <li>In this task, I configured the API from my AirBnB_clone_v3 to run on Gunicorn.</li>
   <li>4-app_server-nginx_config: Nginx configuration file that proxies requests on the AirBnB API to the corresponding Gunicorn app.</li>
<li><b>5. Serve your AirBnB clone</li>
   <li>In this task, I configured the complete AirBnB app from AirBnB_clone_v4 to run on Gunicorn and be served through Nginx.</li>
   <li>5-app_server-nginx_config: Nginx configuration file configured to serve the static assets from web_dynamic/static/ on the Gunicorn AirBnB app.</li>
<li><b>6. Deploy it</li>
   <li>gunicorn.conf: Configuration file for an Upstart script that starts a Gunicorn process bounded to port 5003 that serves the content from task 5.</li>
   <li>The Gunicorn process spawns three worker processes and logs errors to /tmp/airbnb-error.log, access to /tmp/airbnb-access.log.</li>
<li><b>7. No service interruption</li>
   <li>4-reload_gunicorn_no_downtime: Bash script that gracefully reloads Gunicorn.</li> 
