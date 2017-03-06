#hibernate + hikari 설정

#마지막 수정일
2017-03-07

    스프링 공부중에 정리한거라 틀릴수도 있다.

    pom.xml 설정
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-orm</artifactId>
            <version>${springframework-version}</version>
        </dependency>
        <!-- jpa, 하이버네이트 -->
        <dependency>
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-entitymanager</artifactId>
            <version>4.3.11.Final</version>
        </dependency>
        <!-- mariadb -->
        <dependency>
            <groupId>org.mariadb.jdbc</groupId>
            <artifactId>mariadb-java-client</artifactId>
            <version>1.4.6</version>
        </dependency>
        <!-- connection pool -->
        <dependency>
            <groupId>com.zaxxer</groupId>
            <artifactId>HikariCP</artifactId>
            <version>2.6.0</version>
        </dependency>

    config.xml
        <bean id="hikariConfig" class="com.zaxxer.hikari.HikariConfig">
            <property name="maximumPoolSize" value="10"/>
            <property name="minimumIdle" value="5"/>
            <property name="poolName" value="springHikariCP" />
            <property name="connectionTestQuery" value="SELECT 1" />
            <property name="dataSourceClassName" value="org.mariadb.jdbc.MariaDbDataSource" />
            <property name="dataSourceProperties">
                <props>
                    <prop key="url">${jdbc.연결문}</prop>
                    <prop key="user">${jdbc.아이디}</prop>
                    <prop key="password">${jdbc.암호}</prop>
                </props>
            </property>
        </bean>

        <bean id="hikariDataSource" class="com.zaxxer.hikari.HikariDataSource" destroy-method="close">
            <constructor-arg ref="hikariConfig"></constructor-arg>
        </bean>

        <bean id="jpaTransactionManager" class="org.springframework.orm.jpa.JpaTransactionManager">
            <property name="dataSource" ref="hikariDataSource"/>
        </bean>

        <bean class="org.springframework.dao.annotation.PersistenceExceptionTranslationPostProcessor"/>

        <bean id="entityManagerFactory" class="org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean">
            <property name="dataSource" ref="hikariDataSource"/>
            <property name="packagesToScan" value="entity 클래스 위치 패키지명"/>
            <property name="jpaVendorAdapter">
                <bean class="org.springframework.orm.jpa.vendor.HibernateJpaVendorAdapter"/>
            </property>
            <property name="jpaProperties">
                <props>
                    <prop key="hibernate.connection.provider_class">com.zaxxer.hikari.hibernate.HikariConnectionProvider</prop>
                    <prop key="hibernate.dialect">org.hibernate.dialect.MySQL5Dialect</prop> <!-- 방언 -->
                    <prop key="hibernate.show_sql">true</prop>                   <!-- SQL 보기 -->
                    <prop key="hibernate.format_sql">true</prop>                 <!-- SQL 정렬해서 보기 -->
                    <prop key="hibernate.use_sql_comments">true</prop>           <!-- SQL 코멘트 보기 -->
                    <prop key="hibernate.id.new_generator_mappings">true</prop>  <!-- 새 버전의 ID 생성 옵션 -->
                    <prop key="hibernate.hbm2ddl.auto">create</prop>             <!-- DDL 자동 생성 -->
                </props>
            </property>
        </bean>