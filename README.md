Installation

The installation is a three-part process:

    Add the required third party repositories
    Install the gluu-gateway package
    Run setup-gluu-gateway.py

Required Third Party repositories

!!! Note Always run the following commands as root.
For Ubuntu 14

    Add the Gluu repo:

echo "deb https://repo.gluu.org/ubuntu/ trusty-devel main" > /etc/apt/sources.list.d/gluu-repo.list
curl https://repo.gluu.org/ubuntu/gluu-apt.key | apt-key add -

    Add the Postgresql-10 repo:
    
echo "deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main" > /etc/apt/sources.list.d/psql.list
get --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

    Add the Node repo:

curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -

For Ubuntu 16

    Add the Gluu repo:

echo "deb https://repo.gluu.org/ubuntu/ xenial-devel main" > /etc/apt/sources.list.d/gluu-repo.list
curl https://repo.gluu.org/ubuntu/gluu-apt.key | apt-key add -

    Add the Postgresql-10 repo:

echo "deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main" > /etc/apt/sources.list.d/psql.list
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

    Add the Node repo:

curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -


For Debian 8

    Add the Gluu repo:

echo "deb https://repo.gluu.org/debian/ testing main" > /etc/apt/sources.list.d/gluu-repo.list
curl https://repo.gluu.org/debian/gluu-apt.key | apt-key add -

    Add the Postgresql-10 repo:

echo "deb http://apt.postgresql.org/pub/repos/apt/ jessie-pgdg main" > /etc/apt/sources.list.d/psql.list
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

    Add the Node repo:

curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -

For Debian 9

    Add the Gluu repo:

echo "deb https://repo.gluu.org/debian/ stretch-testing main" > /etc/apt/sources.list.d/gluu-repo.list
curl https://repo.gluu.org/debian/gluu-apt.key | apt-key add -

    Add the Postgresql-10 repo:

echo "deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main" > /etc/apt/sources.list.d/psql.list
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

    Add the Node repo:

curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -

For CentOS 6

    Add the Gluu repo:

wget https://repo.gluu.org/centos/Gluu-centos-testing.repo -O /etc/yum.repos.d/Gluu.repo
wget https://repo.gluu.org/centos/RPM-GPG-KEY-GLUU -O /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU

    Add the Postgresql-10 repo:

rpm -Uvh https://yum.postgresql.org/10/redhat/rhel-6-x86_64/pgdg-redhat10-10-2.noarch.rpm

    Add the Node repo:

curl -sL https://rpm.nodesource.com/setup_8.x | sudo -E bash -

For CentOS 7

    Add the Gluu repo:

wget https://repo.gluu.org/centos/Gluu-centos-7-testing.repo -O /etc/yum.repos.d/Gluu.repo
wget https://repo.gluu.org/centos/RPM-GPG-KEY-GLUU -O /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU

    Add the Postgresql-10 repo:

rpm -Uvh https://yum.postgresql.org/10/redhat/rhel-7-x86_64/pgdg-centos10-10-2.noarch.rpm

    Add the Node repo:

curl -sL https://rpm.nodesource.com/setup_8.x | sudo -E bash -

For RHEL 6

    Add the Gluu repo:

wget https://repo.gluu.org/rhel/Gluu-rhel-testing.repo -O /etc/yum.repos.d/Gluu.repo
wget https://repo.gluu.org/rhel/RPM-GPG-KEY-GLUU -O /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU

    Add the Postgresql-10 repo:

rpm -Uvh https://yum.postgresql.org/10/redhat/rhel-6-x86_64/pgdg-redhat10-10-2.noarch.rpm

    Add the Node repo:

curl -sL https://rpm.nodesource.com/setup_8.x | sudo -E bash -

For RHEL 7

    Add the Gluu repo:

wget https://repo.gluu.org/rhel/Gluu-rhel-7-testing.repo -O /etc/yum.repos.d/Gluu.repo
wget https://repo.gluu.org/rhel/RPM-GPG-KEY-GLUU -O /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-GLUU

    Add the Postgresql-10 repo:

rpm -Uvh https://yum.postgresql.org/10/redhat/rhel-7-x86_64/pgdg-centos10-10-2.noarch.rpm

    Add the Node repo:

curl -sL https://rpm.nodesource.com/setup_8.x | sudo -E bash -

Install the gluu-gateway package
For Ubuntu 14, Ubuntu 16, Debian 8, Debian 9

apt update
apt install gluu-gateway

For CentOS 6, Centos 7, RHEL 6, RHEL 7

yum clean all
yum install gluu-gateway

Run the setup script

cd /opt/gluu-gateway/setup
python setup-gluu-gateway.py

You will be prompted to answer some questions. Just hit Enter to accept the default value, which is specified in square brackets.

!!! Warning When you are prompted to provide a two-letter value, make sure you follow the instructions. A mistake may result in the lack of certificates.
Question        Explanation
Enter IP Address        IP Address of your API gateway
Enter Kong hostname     Internet-facing FQDN to generate certificates and metadata. Do not use an IP address or localhost.
Country         Used to generate web X.509 certificates
State   Used to generate web X.509 certificates
City    Used to generate web X.509 certificates
Organization    Used to generate web X.509 certificates
Email   Used to generate web X.509 certificates
Password        If you already have a database password for user postgres, enter it here. Otherwise, enter a new password.
Would you like to configure oxd-server?         If you already have oxd-web on the network, skip this configuration.
OP hostname     Used to configure the oxd default OP hostname. Many deployments use a single domain's OP service, so it makes sense to set it as the default.
License Id      From oxd-server license
Public key      From oxd-server license
Public password         From oxd-server license
License password        From oxd-server license
oxd https url   Make sure oxd-https-extension is running.
Would you like to generate client_id/client_secret for konga?   You can register a new OpenID Client or enter existing client credentials manually. You may want to extend the client expiration date on the Gluu Server if you plan to use this service more than one day. If you enter existing client details, then your client must have the https://localhost:1338 URL entry in Redirect Login URIs and Post Logout Redirect URIs.
oxd_id  Used to manually set oxd id.
client_id       Used to manually set client id.
client_secret   Used to manually set client secret.
Finish the setup

 Gluu Gateway configuration successful!!! https://localhost:1338

If you see the above message, it means the installation was successful. To log into the Gluu Gateway admin portal, create an SSH tunnel on port 1338 from your workstation to the Gluu Gateway server, and point your browser at https://localhost:1338.

!!! Note See FAQ for global access configuration.
                                                                                                                                                       185,1         Bot

