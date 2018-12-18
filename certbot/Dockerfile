FROM centos:7

RUN yum -y install epel-release && yum -y install certbot-nginx cronie && echo "43 */12 * * * certbot renew >> /var/log/letsencrypt/cetbot.log" | crontab

ENTRYPOINT ["bash", "-c", "crond -s; tail -f /var/log/letsencrypt/*.log"]
