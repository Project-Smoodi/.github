<img src="../smoodi_banner.png" alt="Smoodi Banner">

# Smoodi 프레임워크
by Daybreak312

<br/>

## Smoodi란?
Smoodi는 자바 엔터프라이즈 기반의 웹 애플리케이션 서버를 제작하기 위한 프레임워크입니다.

Smoodi는 비즈니스 로직 외에 요구되는 애플리케이션 실행의 기반을 제공하여,

개발자가 비즈니스 로직에만 집중할 수 있도록 셍신상 높은 개발 환경 지원을 목표로 합니다.

<br/>

# Smoodi 시작하기
### Smoodi 의존성 설정

의존성에 아래와 같이 Smoodi 의존성을 추가합니다.
**version**에는 팀에서 요구하는 Smoodi 버전을 입력합니다.

_build.gradle (Groovy)_
```gradle
dependencies {
  implementation 'org.smoodi.framework:smoodi-web:version'
}
```

_build.gralde.kts (Kotlin DSL)_
```gradle
dependencies {
  implementation("org.smoodi.framework:smoodi-web:version")
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
        name = 'GitHubPackages'
        url = 'https://maven.pkg.github.com/Project-Smoodi/Smoodi-Core'
        credentials {
            username = project.findProperty("gpr.user") // Github 유저 이름, Gradle 환경 변수를 이용한 설정
            password = System.getenv("TOKEN") // 'read:packages' 권한이 활성화된 GHP 토큰, 시스템 환경 변수를 이용한 설정
        }
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
        credentials {
            username = project.findProperty("gpr.user") // Github 유저 이름, Gradle 환경 변수를 이용한 설정
            password = System.getenv("TOKEN") // 'read:packages' 권한이 활성화된 GHP 토큰, 시스템 환경 변수를 이용한 설정
        }
    }
    mavenCentral() // Maven Repository를 통해 배포된 다른 의존성을 의존하기 위해 필요합니다. 대다수의 경우 필요하지만, 필요하지 않을 경우 제거하세요.
}
```

repositories > maven > credentials 영역은 Github 계정 인증을 위한 인증 정보를 기입하는 곳입니다.

Github Packages는 패캐지(Smoodi처럼, 배포된 프로젝트들)에 접근하기 위해 Github 계정 인증이 필요합니다.

username 부분은 사용자의 Github 이름, password 부분은 Github 계정의 정보를 담은 Github 토큰(GHP 토큰)을 입력합니다.

이 부분은 다른 사용자에게 노출되어서는 안되며, 위 코드 블럭에 제시된 것처럼 'Gradle 환경 변수 (gradle.properties 파일)' 또는 '시스템 환경 변수'를 이용해 설정하기를 권고합니다.

GHP 토큰 발급은 아래의 문서를 참고해주세요.
> https://docs.github.com/ko/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#personal-access-token-classic
