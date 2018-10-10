#docker run -d --privileged -p 8080:80 -p 8022:22 -p 8443:443 image
FROM debian

EXPOSE 80 22 443
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y curl openssh-server ca-certificates tzdata
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get install -y gitlab-ce
RUN echo "#!/bin/bash\n/opt/gitlab/embedded/bin/runsvdir-start &\necho \"external_url 'https://gitlab.exemple.fr'\" >> /etc/gitlab/gitlab.rb\ngitlab-ctl reconfigure\ntail -f /dev/null" > /root/script_start.sh && chmod +x /root/script_start.sh
ENTRYPOINT ["/root/script_start.sh"]
