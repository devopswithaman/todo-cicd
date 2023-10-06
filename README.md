# todo-cicd
This is todo app with jenkins cicd
mkdir projects
cd projects/
git clone https://github.com/shreys7/django-todo.git
cd django-todo
sudo apt-get update
sudo apt install python3-pip
pip install django
python3 manage.py migrate
python3 manage.py runserver 0.0.0.0:8001
Open this port in EC2 security group
vi todoApp/settings.py  and change Allowed Host with '*'
python3 manage.py runserver 0.0.0.0:8001
nohup python3 manage.py runserver 0.0.0.0:8001 &
lsof -i:8001
kill -9 <PID>
type docker to check docker present in system or not 
if not then type sudo apt  install docker.io
create docker file by using vi Dockerfile
	FROM python:3
	RUN pip install django==3.2
	
	COPY . .
	
	RUN python manage.py migrate

	CMD ["python","manage.py","runserver","0.0.0.0:8001"]

sudo docker build . -t todo-app

Copy container ID (container is build but not in running state) to check this use sudo docker ps

sudo docker run -p 8001:8001 <conatiner ID>

sudo docker run -d -p 8001:8001 <conatiner ID>
