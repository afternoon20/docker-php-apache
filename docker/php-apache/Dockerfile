FROM centos:7

RUN yum update -y
RUN yum install -y sudo
RUN yum install -y epel-release
RUN sed -i -e "s/metalink/#metalink/g" /etc/yum.repos.d/epel.repo
RUN sed -i -e "s/#baseurl=http:\/\/download.fedoraproject/baseurl=http:\/\/dl.fedoraproject/g" /etc/yum.repos.d/epel.repo
RUN yum install -y http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
RUN yum clean all
RUN yum -y install wget
RUN yum -y install httpd
RUN yum -y install --enablerepo=remi,remi-php80 php php-mbstring php-pdo php-gd php-xml php-mcrypt php-mysql composer curl

RUN yum install -y http://opensource.wandisco.com/centos/7/git/x86_64/wandisco-git-release-7-1.noarch.rpm
RUN yum install -y git

RUN systemctl enable httpd

RUN curl -fsSL https://deb.nodesource.com/setup_lts.x
RUN yum install -y nodejs npm
RUN npm install -g n

CMD ["/usr/sbin/httpd", "-DFOREGROUND"]
