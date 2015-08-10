image:
	docker build -t nginx_demo .

all: image

run:
	docker run -p 5000:80 nginx_demo /usr/sbin/nginx -c /etc/my_nginx.conf
	@echo "curl 192.168.59.103:5000/a/"