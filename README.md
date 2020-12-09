# lombok-plugin

**简要描述：**

- mybatis generator插件生成mapper时自动加入lombok注解，并生成model中字段注释
- 在model中自动生成@Getter、@Setter、@Builder(toBuilder=true)、@AllArgsConstructor、@NoArgsConstructor、@ToString等lombok注解

**第一步：**
- `pom文件中引入maven配置 `

```
<plugin>
	<!-- MyBatis generator -->
	<groupId>org.mybatis.generator</groupId>
	<artifactId>mybatis-generator-maven-plugin</artifactId>
	<version>1.3.2</version>
	<configuration>
		<verbose>true</verbose>
		<overwrite>true</overwrite>
	</configuration>

	<!-- lombok-plugin -->
	<dependencies>
		<dependency>
			<groupId>com.joy.plugin</groupId>
			<artifactId>lombok-plugin</artifactId>
			<version>0.0.1</version>
		</dependency>
	</dependencies>
</plugin>
```

**第二步：**
- `generatorConfig.xml 中加入lombok-plugin配置，应在 jdbcConnection 之前`

```
<!-- 整合lombok-->
<plugin type="com.bai.plugin.mybatis.generator.LombokPlugin" >
	<property name="hasLombok" value="true"/>
</plugin>

<commentGenerator>
	<property name="suppressAllComments" value="true" />
</commentGenerator>
```

**第三步：**
- `执行 generatorConfig.xml`

