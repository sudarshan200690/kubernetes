kubectl exec -it pod_name -- sh
ls /etc/mysql/conf.d
Kubernetes took the map name of mysql_binlog_format.cnf present it as a filewith the contents that were stored in the data source of the configMap. The problem however is it laid that volume on top of the existing directory. The default configuration files for mysql are no longer present. I'd have to create all the mysql configuration files and store them into the configMap. Or, I can use a subPath.

1. in mysql-without-config - only there is deployment and service without config map
2. in mysql-with-config - have mount volumes inside container with help of configmap - so in that case inside container mountpath whatever files are there - got replaced in each fresh deployment - that means file got overwritten
3. To overcome this problem we have added subpath concept in mysql-config-subpath - where files will be appeneded in volumemounts path inside the container for each deployment