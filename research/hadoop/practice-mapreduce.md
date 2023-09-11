# MapReduce 실습하기

마지막 업데이트 날짜: 2023-09-11 <br>
작성자: 김예진

> **목차**
> 1. MapReduce 실행을 위한 YARN 설정
>    1. `etc/hadoop/mapred-site.xml`설정
>    2. `etc/hadoop/yarn-site.xml` 수정
>    3. YARN 실행
> 2. Hadoop에서 제공하는 기본 MapReduce 실행

# 1. MapReduce 실행을 위한 YARN 설정

1. ### `etc/hadoop/mapred-site.xml`설정
   MapReduce jobs 실행 시 YARN 프레임워크 위에서 YARN이 리소스 할당과 MapReduce 업무를 실행할 것임을 선언한다. 이 설정은 YARN이 다양한 워크로드 실행을 위한 더 나은 리소스 관리와 유연성을 제공하기 때문에 이 설정은 하둡 클러스터 설정 시 가장 일반적인 구성이 된다.
   ```xml
   <configuration>
       <property>
           <name>mapreduce.framework.name</name>
           <value>yarn</value>
       </property>
   </configuration>
   ```
2. ### `etc/hadoop/yarn-site.xml` 수정
   YARN 자체는 MapReduce를 위해 만들어진 것이 아니기 때문에 Map 단계가 끝나고 Reduce로 넘어갈 때 Shuffle 과정을 YARN에서 실행하라는 설정을 따로 해야 한다.
   ```xml
   <configuration>
       <property>
           <name>yarn.nodemanager.aux-services</name>
           <value>mapreduce_shuffle</value>
       </property>
       <property>
           <name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name>
           <value>org.apache.hadoop.mapred.SuffleHandler</value>
       </property>
   </configuration>
   ```
3. ### YARN 실행
   ```bash
   sbin/start-yarn.sh
   ```
   ```bash
   jps
   ```
   ![](images/hadoop08.PNG)

# 2. Hadoop에서 제공하는 기본 MapReduce 실행

```bash
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.6.jar wordcount input output_notice
```

