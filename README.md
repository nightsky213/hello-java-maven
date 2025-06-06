# ☕ Hello Java Maven - Jenkins CI Build

This project demonstrates a simple Java Maven application built using Jenkins — a great starting point for understanding CI/CD basics.

## 🛠 Tech Stack

- Java (JDK 8 or 11)
- Maven (3.8.x)
- Jenkins (via Docker or local install)

## 📁 Project Structure

```
hello-java-maven/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java
```

### 🔤 HelloWorld.java

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
```

### 🧾 pom.xml

Basic Maven config to compile Java 8 code.

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>hello</artifactId>
  <version>1.0</version>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.1</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```

## 🚀 Steps to Run Jenkins Job

1. **Start Jenkins using Docker**:

   ```bash
   docker run -p 8080:8080 jenkins/jenkins:lts
   ```

2. **In Jenkins Dashboard**:
   - Go to: `Manage Jenkins → Global Tool Configuration`
   - Add **Maven** (check "Install automatically")

3. **Create Freestyle Project**:
   - Job name: `hello-java-build`
   - In **Build** section, choose `Invoke top-level Maven targets`
   - Goals: `clean package`

4. **Build & Verify**:
   - Click **Build Now**
   - Go to **Console Output**
   - ✅ Look for: `BUILD SUCCESS`

## ✅ Verifying Output

If you want to test locally:

```bash
mvn clean package
java -cp target/hello-1.0.jar HelloWorld
```

Expected:

```
Hello, Jenkins + Maven!
```
