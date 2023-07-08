# Tailwindcss - Spring Boot

## What's tailwindcss?

A utility-first CSS framework packed with classes like flex, pt-4, text-center and rotate-90 that can be composed to build any design, directly in your markup.

## Important files

to integrate _tailwindcss_  with _spring-boot_ we need to start a node js application, which is already loaded here: `src/main/webapp`.

The `pom.xml` will load the processed tailwind file during compilation and packaging phase.

````xml
 <plugin>
    <groupId>com.github.eirslett</groupId>
    <artifactId>frontend-maven-plugin</artifactId>
    <version>${frontend-maven-plugin.version}</version>
    <configuration>
        <workingDirectory>src/main/webapp</workingDirectory>
    </configuration>
    <executions>
        <execution>
            <id>install node</id>
            <goals>
                <goal>install-node-and-npm</goal>
            </goals>
            <configuration>
                <nodeVersion>${node.version}</nodeVersion>
            </configuration>
        </execution>
        <execution>
            <id>npm install</id>
            <goals>
                <goal>npm</goal>
            </goals>
            <phase>compile</phase>
            <configuration>
                <arguments>install</arguments>
            </configuration>
        </execution>
        <execution>
            <id>npm build</id>
            <goals>
                <goal>npm</goal>
            </goals>
            <phase>package</phase>
            <configuration>
                <arguments>run build</arguments>
            </configuration>
        </execution>
    </executions>
</plugin>
````

## Live Reload

Add the spring boot dev tools and configure the IDE to build automatically.

````xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <scope>runtime</scope>
    <optional>true</optional>
</dependency>
````

Run the tailwind watch.

````shell
npm run build:dev
````

### IntelliJ

https://stackoverflow.com/a/63975477/4775487
https://stackoverflow.com/a/12744431/4775487
