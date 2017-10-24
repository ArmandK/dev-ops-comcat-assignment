--Create a user called 'comcast' with admin privileges.  The ACCOUNT ID : 794768789958
--Create an AWS instance (comcast_test) that a user called 'comcast' can login with a pem key.
--This user will have admin access to the instance	
--A Chef starter kit will be downloaded
--Chef tools will be install to that instance
--Create an Apache web server's recipe
--Create a self-signed certificate with openssl and configure in tha Apache virtual host
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout comcast.key -out comcast.crt

<VirtualHost *: 443 >  
  ServerName localhost
  SSLEngine on
  SSLCertificateFile      /etc/httpd/comcast.crt
  SSLCertificateKeyFile   /etc/httpd/comcast.key
  DocumentRoot "/var/www/html"
</VirtualHost>