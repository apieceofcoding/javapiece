# 4. 자바 개발환경 설정

자바 개발을 시작하려면 적절한 개발 환경을 설정해야 합니다.

### 4.1 자바 개발 도구 설치

#### JDK (Java Development Kit) 설치

* **JDK란?**: JDK는 자바 개발 키트로, 자바 애플리케이션을 개발하기 위한 핵심 도구와 라이브러리를 제공합니다.
* **다운로드**: Oracle 또는 OpenJDK와 같은 공식 웹사이트에서 JDK를 다운로드합니다.

#### IDE (Integrated Development Environment) 설치

* **IDE란?**: IDE는 통합 개발 환경으로, 코드 편집, 디버깅, 빌드, 배포 등을 편리하게 수행할 수 있는 개발 도구입니다.
* **추천 IDE**: IntelliJ IDEA



### 4.2 환경 변수 설정

**환경변수(PATH)에 추가하는 이유**: JDK의 실행 파일들이 있는 경로를 PATH에 추가하면 터미널에서 어디서든 Java 컴파일러(`javac`)와 실행기(`java`)를 실행할 수 있습니다.

#### 4.2.1 JAVA\_HOME 설정

* **JAVA\_HOME이란?**: JAVA\_HOME 환경 변수는 시스템에서 사용하는 기본 JDK의 경로를 지정합니다.
* **설정 방법 (Windows)**:
  * 제어판 > 시스템 및 보안 > 시스템 > 고급 시스템 설정 > 고급 탭 > 환경 변수 버튼 클릭.
  * 시스템 변수 아래에서 "새로 만들기" 버튼을 클릭하고 변수 이름에 "JAVA\_HOME"을 입력하고, 변수 값에 JDK의 설치 경로를 입력합니다.
* **설정 방법 (Linux/macOS)**:
  *   터미널에서 `~/.bashrc` 또는 `~/.bash_profile` 파일을 열고 다음 줄을 추가합니다.

      ```sh
      export JAVA_HOME=/path/to/your/jdk
      ```
  * 변경사항을 저장하고 터미널에서 `source ~/.bashrc` 또는 `source ~/.bash_profile` 명령어를 실행하여 적용합니다.

\
