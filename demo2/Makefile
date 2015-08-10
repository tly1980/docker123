image:
	docker build -t nginx_demo .

all: image

run:
	@echo "Please run: curl YOUR_DOCKER_HOST:5000/a/"
	docker run -p 5000:80 nginx_demo /usr/sbin/nginx -c /etc/my_nginx.conf
