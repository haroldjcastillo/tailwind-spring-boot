# Tailwindcss - Spring Boot

## What's tailwindcss?

A utility-first CSS framework packed with classes like flex, pt-4, text-center and rotate-90 that can be composed to build any design, directly in your markup.

## Important files

to integrate _tailwindcss_  with _spring-boot_ we need to start a node js application, which is already loaded here: `src/main/webapp`.

The `pom.xml` will load the processed tailwind file during compilation time.

````xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-resources-plugin</artifactId>
    <version>${maven-resources-plugin.version}</version>
    <executions>
        <execution>
            <id>copy-resources</id>
            <phase>process-classes</phase>
            <goals>
                <goal>copy-resources</goal>
            </goals>
            <configuration>
                <outputDirectory>${basedir}/target/classes/static</outputDirectory>
                <resources>
                    <resource>
                        <directory>src/main/webapp/public/static</directory>
                    </resource>
                </resources>
            </configuration>
        </execution>
    </executions>
</plugin>
````

And then execute the command `node run build:css` with maven.

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
            <id>npm build</id>
            <goals>
                <goal>npm</goal>
            </goals>
            <phase>compile</phase>
            <configuration>
                <arguments>run build:css</arguments>
            </configuration>
        </execution>
    </executions>
</plugin>
````

## Testing without spring-boot

Into the webapp folder `src/main/webapp` run `npm run build:css` and `node index.js`, it will start a server `http://localhost:3000` then a `Hello World!` will be displayed on the browser.