elasticsearch  https://blog.csdn.net/xiaoxiaole0313/article/details/105631065
https://github.com/macrozheng/mall/blob/14f0a625bfa421dbf9d5e7f357c9dc0c6ac03f86/mall-search/src/main/java/com/macro/mall/search/domain/EsProduct.java#L21

https://github.com/spring-petclinic/spring-petclinic-microservices
https://github.com/doit01/demo-gitlab-cicd/blob/master/.gitlab-ci.yml  
echo "##1 : kill old application if exists"
sudo kill -9 $(lsof -i tcp:8088)
echo "##2 create new package of project"
mvn clean package
cd target
JAR_FILE=$(find . -maxdepth 3 -iname "*.jar" | sort -rfV  | head -n 1 | awk "{print $9}" | cut -d "/" -f 2)
mv $JAR_FILE .. && cd ..
echo "##3 run project"
rm nohup.out
nohup java -jar $JAR_FILE &
tail -f ./nohup.out
https://github.com/smzerehpoush/spring-boot_prometheus_grafana/blob/master/spring-boot-v2/src/main/resources/application.yml
<dependency>
            <groupId>io.micrometer</groupId>
            <artifactId>micrometer-core</artifactId>
            <version>1.4.1</version>
        </dependency>
        <!-- https://mvnrepository.com/artifact/io.micrometer/micrometer-registry-prometheus -->
        <dependency>
            <groupId>io.micrometer</groupId>
            <artifactId>micrometer-registry-prometheus</artifactId>
            <version>1.4.1</version>
        </dependency>

global:
  scrape_interval: 5s

scrape_configs:
  - job_name: 'spring_micrometer'
    metrics_path: '/actuator/prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['192.168.1.101:8088']
