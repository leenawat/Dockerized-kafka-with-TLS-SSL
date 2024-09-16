Please Visit My Article Link For More Detail: 
[Article] (https://medium.com/@solanki.kishan007/dockerized-kafka-with-tls-ssl-ede2107d880d)

[\[git@github.com:leenawat/Dockerized-kafka-with-TLS-SSL.git\](https://github.com/leenawat/Dockerized-kafka-with-TLS-SSL/tree/main](https://github.com/jackysolanki007/Dockerized-kafka-with-TLS-SSL)




edit /etc/hosts
```
192.168.1.244 example.kafka.com
your_ip       example.kafka.com
```

manual create keystore and truststore
```
keytool -genkeypair -alias kafka-key -keyalg RSA -keystore kafka.keystore.jks -keysize 2048 -validity 365 -dname "CN=example.kafka.com, OU=, O=, L=Det Udom, ST=UbonRatchathani, C=TH"

keytool -exportcert -alias kafka-key -keystore kafka.keystore.jks -file kafka-cert.crt

keytool -importcert -alias kafka-cert -file kafka-cert.crt -keystore kafka.truststore.jks

cp kafka.keystore.jks to cert/keystore

cp kafka.truststore.jks to cert/truststore

keytool -list -v -keystore kafka.truststore.jks

docker network create kafka

docker compose up --build --force-recreate
```