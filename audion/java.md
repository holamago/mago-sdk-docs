<div align="center">
  <!-- <img src="https://audion.magovoice.com/static/media/logo.10d2cf1b78c4088112afa09c702c5c2d.svg" width="200">
  <h1>Audion Java SDK</h1> -->

  <p>
    <strong>음성 AI 구현의 복잡함을 없애고, 비즈니스 가능성을 확장하세요.</strong>
  </p>

  <p>
    <a href="https://github.com/magovoice/audion-java-sdk/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" alt="License"></a>
    <a href="https://java.com"><img src="https://img.shields.io/badge/java-11+-blue.svg" alt="Java version"></a>
  </p>
</div>

# Audion Java SDK

> Repository: [github.com/holamago/audion-java-sdk](https://github.com/holamago/audion-java-sdk)

## 목차

- [요구사항](#요구사항)
- [설치](#설치)
- [빠른 시작](#빠른-시작)
- [API 문서](#api-문서)
- [사용 예제](#-사용-예제)
- [지원 파일 형식](#-지원-파일-형식)
- [라이선스](#-라이선스)
- [지원](#-지원)
- [버전 히스토리](#-버전-히스토리)


## 요구사항

- Java 11+
- Maven 3.6+
- API 키 ([Audion 서비스 등록](https://audion.magovoice.com/signup) 필요)
  - 회원가입 후 API Key 발급 받아야 합니다.

## 설치

### 소스에서 빌드

```bash
git clone https://github.com/holamago/audion-java-sdk.git
cd audion-java-sdk
mvn clean install
```

## 빠른 시작

### 1. 클라이언트 초기화

```java
import com.magovoice.audion.AudionClient;

// API 키로 클라이언트 초기화
AudionClient client = new AudionClient("your-api-key-here");
```

### 2. 로컬 파일 처리

```java
// 로컬 오디오/비디오 파일 처리
Object result = client.flow(
    "audion_vu",
    "file",
    "path/to/your/audio.wav"
);
System.out.println(result);
```

### 3. URL 처리

```java
// YouTube URL 처리
Object result = client.flow(
    "audion_vu",
    "url",
    "https://youtu.be/your-video-id"
);
System.out.println(result);
```

## API 문서

### AudionClient

Audion 서비스의 메인 클라이언트 클래스입니다.

#### 생성자

```java
// 기본 생성자
AudionClient(String apiKey)
// 커스텀 URL과 함께
AudionClient(String apiKey, String baseUrl)
// 모든 옵션과 함께
AudionClient(String apiKey, String baseUrl, Integer timeout)
```

**매개변수:**

- `apiKey` (String, 필수): Audion 서비스 인증을 위한 API 키
- `baseUrl` (String, 선택): 서버의 기본 URL. 기본값은 프로덕션 서버
- `timeout` (Integer, 선택): HTTP 요청 타임아웃(초). 기본값은 300초

**예외:**

- `IllegalArgumentException`: apiKey가 제공되지 않은 경우

#### 메서드

##### `flow(flow, inputType, input)`

지정된 플로우로 음성/비디오 처리를 실행합니다.

```java
Object flow(String flow, String inputType, String input) throws IOException
```

**매개변수:**

- `flow` (String): 실행할 플로우의 이름
  - 현재 지원하는 플로우:
    - `audion_vu`: Voice Understanding
    - `audion_vh`: Voice Highlight
  - Custom Flow 지원 가능 (email:contact@holamago.com)
- `inputType` (String): 입력 타입. `"file"` 또는 `"url"`
- `input` (String): 처리할 파일의 경로 또는 URL

**반환값:**

- `Object`: 처리 결과를 포함하는 JSON 응답

**예외:**

- `IllegalArgumentException`: 지원하지 않는 inputType인 경우
- `IOException`: API 호출 실패 시

##### `getFlows()`

사용 가능한 플로우 목록을 가져옵니다.

```java
Object getFlows() throws IOException
```

## 사용 예제

### 호출 예시

로컬 오디오/비디오 파일을 처리하는 가장 단순한 호출 예시입니다.

```java
import com.magovoice.audion.AudionClient;

AudionClient client = new AudionClient("your-api-key-here");

Object result = client.flow(
    "audion_vu",
    "file",
    "samples/audio.wav"
);

System.out.println(result);
```

자세한 예제 코드는 Audion Java SDK 저장소의 [examples 디렉터리](https://github.com/holamago/audion-java-sdk/tree/main/examples)를 참고하세요.

`flow` 메서드의 파라미터와 반환값에 대한 자세한 설명은 위 [`flow` 메서드 섹션](#flowflow-inputtype-input)을 참고하세요.

## 지원 파일 형식

지원하는 오디오/비디오 파일 형식은 [`Audion 지원 파일 형식`](file-formats.md) 문서를 참고하세요.

## 라이선스

이 프로젝트는 [Apache License 2.0](LICENSE) 하에 라이선스됩니다.

## 지원

- **문서**: [Audion 공식 문서](https://audion.magovoice.com)
- **이슈**: [GitHub Issues](https://github.com/holamago/audion-java-sdk/issues)
- **이메일**: contact@holamago.com

## 버전 히스토리

- **v0.1.0**: 초기 릴리스
  - 기본 flow API 지원
  - 파일 및 URL 입력 지원
  - 다중 오디오/비디오 형식 지원
  - Maven 프로젝트 구조
  - JUnit 테스트 포함

<div align="center">
  <p>Made with ❤️ by <a href="https://magovoice.com">MAGO</a></p>
</div>


