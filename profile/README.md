<img src="../smoodi_banner.png" alt="Smoodi Banner">

# Smoodi 프레임워크
by Daybreak312

<br/>

## Smoodi란?
Smoodi는 자바 엔터프라이즈 기반의 웹 서버 애플리케이션을 제작하기 위한 프레임워크입니다.

Smoodi의 목표는 개발자가 비즈니스 로직에만 집중할 수 있도록 애플리케이션 실행에 필요한 비즈니스 로직 외의 요소들을 지원하여 보다 편리한 개발 환경을 지원하는 것입니다.

<br/>

# Smoodi 시작하기
### Smoodi 의존성 설정

의존성에 아래와 같이 Smoodi 의존성을 추가합니다.
**version**에는 팀에서 요구하는 Smoodi 버전을 입력합니다.

_build.gradle (Groovy)_
```gradle
dependencies {
  implementation 'org.smoodi.framework:smoodi-core:version'
}
```

_build.gralde.kts (Kotlin DSL)_
```gradle
dependencies {
  implementation("org.smoodi.framework:smoodi-core:version")
}
```

<br/>

### Smoodi Repository 추가

Smoodi는 현재 **Github Packages**를 통해 배포되어 있습니다.
아래와 같이 **Smoodi Github Packages**를 Repository 설정에 추가합니다.

_build.gradle (Groovy)_
```gradle
repositories {
    maven {
        name = "GitHubPackages"
        url = uri("https://maven.pkg.github.com/Project-Smoodi/Smoodi-Core")
    }
    mavenCentral() // Maven Repository를 통해 배포된 다른 의존성을 의존하기 위해 필요합니다. 대다수의 경우 필요하지만, 필요하지 않을 경우 제거하세요.
}
```

_build.gralde.kts (Kotlin DSL)_
```gradle
repositories {
    maven {
        name = "GitHubPackages"
        url = uri("https://maven.pkg.github.com/Project-Smoodi/Smoodi-Core")
    }
    mavenCentral() // Maven Repository를 통해 배포된 다른 의존성을 의존하기 위해 필요합니다. 대다수의 경우 필요하지만, 필요하지 않을 경우 제거하세요.
}
```
