#  vagrant ansible django angular2 gulp fullstack
Vagrant + Ansible + Nginx + uWSGI + gulp + Angular2 + Django 

we love it!

#  uWSGI

https://docs.djangoproject.com/en/1.8/howto/deployment/wsgi/uwsgi/


uWSGI model¶

uWSGI operates on a client-server model. Your Web server (e.g., nginx, Apache) communicates with a django-uwsgi “worker” process to serve dynamic content. See uWSGI’s background documentation for more detail.

Configuring and starting the uWSGI server for Django¶

uWSGI supports multiple ways to configure the process. See uWSGI’s configuration documentation and examples.

Here’s an example command to start a uWSGI server:

uwsgi --chdir=/path/to/your/project \
    --module=mysite.wsgi:application \
    --env DJANGO_SETTINGS_MODULE=mysite.settings \
    --master --pidfile=/tmp/project-master.pid \
    --socket=127.0.0.1:49152 \      # can also be a file
    --processes=5 \                 # number of worker processes
    --uid=1000 --gid=2000 \         # if root, uwsgi can drop privileges
    --harakiri=20 \                 # respawn processes taking more than 20 seconds
    --max-requests=5000 \           # respawn processes after serving 5000 requests
    --vacuum \                      # clear environment on exit
    --home=/path/to/virtual/env \   # optional path to a virtualenv
    --daemonize=/var/log/uwsgi/yourproject.log      # background the process
