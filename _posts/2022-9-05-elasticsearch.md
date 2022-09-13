# ElasticSearch

### Download

https://www.elastic.co/de/downloads/elasticsearch
https://www.elastic.co/guide/en/elasticsearch/reference/7.15/deb.html#deb-repo

### JAVA INSTALLIEREN

sudo apt-get install -y openjdk-8-jdk

### INSTALL

sudo apt install /home/tp/Downloads/elasticsearch-7.6.1-amd64.deb

### START

sudo systemctl start elasticsearch

### Configurate

cd /etc/apache2/

sudo gedit /etc/apache2/ports.conf

```php
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default.conf

Listen 80
Listen 8080

<IfModule ssl_module>
	Listen 443
</IfModule>

<IfModule mod_gnutls.c>
	Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

cd /etc/apache2/sites-available/

sudo gedit mydomainelasticsearch.conf

```php
<VirtualHost *:8080>
	ProxyPass "/" "http://localhost:9200/"
	ProxyPassReverse "/" "http://localhost:9200/"
</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```


### START

sudo service apache2 restart

sudo systemctl start elasticsearch

### TEST

curl -X GET 'http://localhost:9200'

```php
{
"name" : "Magentip",
"cluster_name" : "elasticsearch",
"cluster_uuid" : "lwRtnBr-RcO3v3VR0Qh1XQ",
"version" : {
"number" : "7.10.0",
"build_flavor" : "default",
"build_type" : "zip",
"build_hash" : "51e9d6f22758d0374a0f3f5c6e8f3a7997850f96",
"build_date" : "2020-11-09T21:30:33.964949Z",
"build_snapshot" : false,
"lucene_version" : "8.7.0",
"minimum_wire_compatibility_version" : "6.8.0",
"minimum_index_compatibility_version" : "6.0.0-beta1"
},
"tagline" : "You Know, for Search"
}
```

