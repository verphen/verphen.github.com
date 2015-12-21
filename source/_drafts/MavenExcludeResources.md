title: MavenExcludeResources
tags:
---
排除依赖包

  <dependency>
    <groupId>commons-dbcp</groupId>
    <artifactId>commons-dbcp</artifactId>
    <version>1.2.1</version>
    <exclusions>
        <exclusion>
            <artifactId>xercesImpl</artifactId>
            <groupId>xerces</groupId>
        </exclusion>
    </exclusions>
</dependency>


2、过滤文件
	<build>        
	        <resources>
	            <resource>
	                <directory>src/main/java</directory>
	                <!-- 包含 -->
	                <includes>
	                    <include>**/*.vm</include>
	                    <include>**/*.properties</include>
	                </includes>
	                <!-- 排除  -->
	                <excludes>
	                <exclude>**/*.log</exclude>
	                </excludes>
	            </resource>
	            <resource>
	                <directory>src/main/resources</directory>
	                <filtering>true</filtering>
	                <includes>
	                    <include>**/*.*</include>
	                </includes>
	                <excludes>
	                <exclude>**/*.log</exclude>
	                </excludes>
	            </resource>
	        </resources>
	</build>

过滤web资源
<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-war-plugin</artifactId>
				<version>2.3</version>
				<configuration>
					<encoding>utf-8</encoding>
					<failOnMissingWebXml>false</failOnMissingWebXml>
					<warSourceExcludes>
						deploy/**,
						static/js/**,
						static/css/**,
						static/images/**
					</warSourceExcludes>
				</configuration>
			</plugin>