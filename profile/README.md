---

<img src="../smoodi_banner.png" alt="Smoodi Banner">

# Project Smoodi - The Framework
by Daybreak312

<br/>

# What is _Smoodi_?  
**Smoodi** is a Java enterprise-based framework for building web application servers.  

It provides the foundational infrastructure needed to run applications, enabling developers to focus solely on business logic.

Smoodi aims to deliver a streamlined and highly productive development environment.  

<br/>

# Getting Started

<br/>

## Adding Smoodi Dependencies  

To add Smoodi to your project, include the following dependency in your `dependencies` block.

Replace `version` with the desired Smoodi version.

<br/>

_**Groovy** (build.gradle)_
```gradle
dependencies {
  implementation 'org.smoodi.framework:smoodi-web:version'
}
```

<br/>

_**Kotlin DSL** (build.gradle.kts)_
```gradle
dependencies {
  implementation("org.smoodi.framework:smoodi-web:version")
}
```
<br/>

## Configuring the Smoodi Repository

Smoodi is distributed via **GitHub Packages**.

Add the repository to your `repositories` block.

<br/>

_**Groovy** (build.gradle)_
```gradle
repositories {
    maven {
        name = 'GitHubPackages'
        url = 'https://maven.pkg.github.com/Project-Smoodi/Smoodi-Core'
        credentials {
            username = project.findProperty('gpr.user') // GitHub username, set via Gradle properties
            password = System.getenv('TOKEN') // GHP token with 'read:packages' permission, set via environment variables
        }
    }
    mavenCentral() // Include if you need dependencies from Maven Central.
}
```

<br/>

_**Kotlin DSL** (build.gradle.kts)_
```gradle
repositories {
    maven {
        name = "GitHubPackages"
        url = uri("https://maven.pkg.github.com/Project-Smoodi/Smoodi-Core")
        credentials {
            username = project.findProperty("gpr.user") // GitHub username, set via Gradle properties
            password = System.getenv("TOKEN") // GHP token with 'read:packages' permission, set via environment variables
        }
    }
    mavenCentral() // Include if you need dependencies from Maven Central.
}
```

The `credentials` section provides authentication for accessing GitHub Packages.  
- **`username`:** Your GitHub username.  
- **`password`:** A GitHub token (GHP token) with the `read:packages` permission.  

⚠️ **Security Tip:** Avoid hardcoding credentials. Use Gradle properties (`gradle.properties`) or system environment variables for security.  

For details on generating a GHP token, refer to the [GitHub documentation](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token).  

<br/>

## Running Gradle

Once the dependencies are configured, download them by running the following command in your project’s root directory:

```bash
./gradlew 
```

---
