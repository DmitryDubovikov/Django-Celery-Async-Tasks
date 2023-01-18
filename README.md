# Django-Celery-Async-Tasks

Django application that works in conjunction with Celery to handle long-running processes outside the normal request/response cycle.

![image](https://github.com/DmitryDubovikov/Django-Celery-Async-Tasks/blob/main/django-celery-flow.png)

Create virtual env:

    pipenv install
    pipenv shell

Run containers:

    docker-compose up

Trigger a new task:

    curl -F type=1 http://localhost:1337/tasks/


Grab the task_id from the response and call the updated endpoint 

    curl http://localhost:1337/tasks48d012e4-8c83-4fac-b24e-d5a5a7ca80ed/

to view the status:

    {"task_id": "48d012e4-8c83-4fac-b24e-d5a5a7ca80ed", "task_status": "SUCCESS", "task_result": true}


Test it out in the browser as well:

    http://localhost:1337/

See the log file fill up locally: logs/celery.log


Navigate to http://localhost:5555 and http://localhost:5555/tasks to view the Flower dashboard while triggering new task in terminal or in browser.

Try adding a few more workers to see how that affects things:

    docker-compose up -d --build --scale celery=3




https://testdriven.io/blog/django-and-celery/