depois de criar o container

exec -it

consult agend -dev

consul members

curl localhost:8500/v1/catalog/nodes

apk -U add bind-tools #para poder da dig e trabalhar com server dns

dig @localhost -p 8600 consul01.node.consul

ifcongig #para pegar o ip do container

consul agent -server -bootstrap-expect=3

 

#lembrar de criar as pastas acimas. /var/lib/consul e /etc/consul.d

para juntar é so dar join

consul join (ip da maquina que quer juntar)

consul agent -bind=172.19.0.5 -data-dir=/var/lib/consul -config-dir=/etc/consul.d #p agent


consul agent -bind=172.19.0.6 -data-dir=/var/lib/consul -config-dir=/etc/consul.d -retry-join=172.19.0.3 -retry-join=172.19.0.4


com o docker-compose.yaml, tem que entrar em cada container do server e dar consul agent -config-dir=/etc/consul.d

dentro de um consul dar -- consul keygen 
para gerar a chave

tem User interface - localhost:8500/ui

se for trabalhar em prod sempre criptografia e TLS

https://www.consul.io/