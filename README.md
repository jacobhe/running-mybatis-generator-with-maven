This Maven project demonstrates how we can run MyBatis Generator with Maven

CONFIGURATION:
- Enter profiles folder
- Copy demo folder as your actual project name eg. `myproject`
- Enter myproject folder
- Edit `config.properties`, change configs as you need.

	Configs list bellow are required.
```
mybatis.generator.configurationFile=profiles/myproject/mybatis-generator-config.xml
mybatis.generator.jdbcDriver=com.mysql.jdbc.Driver
mybatis.generator.jdbcPassword=[your database password]
mybatis.generator.jdbcURL=[your database url]
mybatis.generator.jdbcUserId=[your database username]
mybatis.generator.outputDirectory=generated-sources/myproject
```

	For more information about mybatics generator configs, visit [Running MyBatis Generator With Maven](http://mybatis.github.io/generator/running/runningWithMaven.html)

- Edit `mybatis-generator-config.xml`, change `targetPackage` to your actual package add add tables as your need.

	For more information about mybatics configuration file , visit [MyBatis GeneratorXML Configuration File Reference](http://mybatis.github.io/generator/configreference/xmlconfig.html)

- Go back to root folder, Edit `pom.xml`, add a new profile config targeting your new profile folder
eg.
```
<profiles>
	...
    <profile>
        <id>myproject</id>
        <properties>
            <build.profile.id>myproject</build.profile.id>
        </properties>
    </profile>
</profiles>
```

RUN:
```
mvn properties:read-project-properties mybatis-generator:generate -P myproject
```
Generated sources will be placed in `generated-sources/myproject`

Actually, your can just modify configs in demo forlder and run the default profile. But it's easier to manager many project for separete configs.

