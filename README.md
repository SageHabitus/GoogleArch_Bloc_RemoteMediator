### 📚 GitHub 사용자 검색 및 저장소 리스트 앱 (Flutter with Clean Architecture and BLoC)

본 프로젝트는 최신 Flutter 프레임워크와 **Clean Architecture** 패턴을 기반으로 개발된 **GitHub 사용자 검색 및 저장소 리스트** 애플리케이션입니다. **BLoC** 및 **Riverpod** 상태 관리 패턴을 사용하여 사용자 인터페이스와 비즈니스 로직을 분리하며, 로컬 데이터 캐싱, 페이징 처리, 광고 배너 표시 등 다양한 기능을 구현하였습니다.

---

### **주요 기능 ✨**

1. **GitHub 사용자 목록 검색 및 표시 🌐**
   - GitHub API를 사용하여 실시간으로 사용자 데이터를 검색하고, 아바타와 사용자명을 리스트로 보여줍니다.
   - 사용자 리스트는 **무한 스크롤**을 통해 동적으로 로드되며, GitHub API의 페이지네이션을 활용하여 성능 최적화를 구현했습니다.
   - **광고 배너**는 10번째, 20번째, 30번째 항목마다 표시되며, 클릭 시 특정 URL로 이동됩니다.

2. **사용자 저장소 목록 🔍**
   - 특정 사용자의 GitHub 저장소 목록을 검색하여 이름, 설명, 별 수, 사용 언어 등의 정보를 제공합니다.

3. **페이징 처리 🔄**
   - 원격 API에서 데이터를 가져올 때, 페이지 단위로 데이터를 로드하며, **무한 스크롤**을 구현하였습니다. 로컬 캐싱과 함께 사용되어 API 호출 최적화 및 성능 향상을 달성했습니다.

4. **로컬 데이터 캐싱 🏠**
   - **SQLite**를 사용하여 사용자 정보와 광고 데이터를 로컬에 캐싱합니다. 네트워크 연결이 끊기더라도, 로컬에 저장된 데이터를 이용해 사용자 경험을 유지할 수 있습니다.

5. **상태 관리 🧠**
   - **BLoC** 패턴과 **Riverpod**를 조합하여 복잡한 상태 관리 문제를 해결했습니다. 사용자 이벤트 기반 데이터 흐름 관리와 전역 상태 관리를 동시에 처리할 수 있도록 설계되었습니다.

6. **테스트 🧪**
   - **JUnit**, **Mockito**를 사용하여 비즈니스 로직, 로컬 및 원격 데이터 소스에 대한 유닛 테스트를 작성했습니다. 주요 기능에 대한 테스트를 포함하여 높은 안정성을 보장합니다.

---

### **기술 스택 🛠️**

- **언어**: Dart
- **프레임워크**: Flutter
- **상태 관리**: Riverpod, BLoC
- **로컬 데이터베이스**: SQLite
- **네트워크 통신**: Dio
- **테스트**: JUnit, Mockito

---

### **Clean Architecture 적용 🚀**

이 프로젝트는 **Clean Architecture** 패턴을 적용하여 각각의 책임 영역을 분리하고, 유지보수와 확장성을 극대화했습니다.

- **Data Layer**:
   - **GithubLocalDataSource**: SQLite를 통해 로컬 데이터를 관리합니다.
   - **GithubRemoteDataSource**: GitHub API에서 데이터를 불러옵니다.

- **Domain Layer**:
   - **GithubRepositoryImpl**: 데이터를 관리하고 Presentation Layer에 제공합니다. 원격 데이터 소스와 로컬 데이터 소스 간의 동기화를 관리합니다.

- **Presentation Layer**:
   - BLoC 패턴과 함께 상태 관리를 수행하며, Flutter UI에서 데이터를 표시합니다.

---

### **프로젝트 구조 🗂️**

```
lib/
├── data/
│   ├── constants/    # 상수 정의
│   ├── model/        # 데이터 모델 정의
│   ├── repository/   # 레포지토리 구현
│   ├── source/
│   │   ├── local/    # 로컬 데이터 소스 (SQLite)
│   │   └── remote/   # 원격 데이터 소스 (GitHub API)
├── presentation/
│   ├── bloc/         # 상태 관리 로직
│   ├── screens/      # UI 화면
│   └── widgets/      # 재사용 가능한 위젯
└── main.dart         # 앱 진입점
```

---

### **상태 관리 패턴 선택 이유 🎯**

1. **BLoC 패턴**: 이벤트 기반 데이터 흐름과 상태 변경을 처리하기에 적합한 패턴으로, 사용자 이벤트에 따른 명확한 상태 변경을 보장합니다.

2. **Riverpod**: 전역 상태 관리의 편리함을 제공하여 복잡한 상태 관리 문제를 간단하게 해결할 수 있습니다.

---

### **Mediator 패턴 및 페이징 처리 강조 🔄**

이 프로젝트는 **Paging Mediator 패턴**을 적용하여 대량의 데이터를 효율적으로 관리합니다. 이를 통해 원격 API와 로컬 데이터 소스 간의 동기화를 유지하고, 네트워크 장애 시에도 사용자가 앱을 원활하게 사용할 수 있도록 설계되었습니다. 페이징 처리와 함께 데이터를 캐싱하여 성능을 최적화하고, 사용자 경험을 개선했습니다.

---

### **테스트 전략 🧪**

- **JUnit**과 **Mockito**를 사용하여 유닛 테스트를 작성했습니다.
- 로컬 및 원격 데이터 소스, 비즈니스 로직의 테스트를 통해 앱의 안정성을 보장합니다.

---

### **프로젝트 빌드 및 실행 방법**

1. **환경 설정**
   - Flutter SDK 및 Android Studio 설치.
   - Git을 사용하여 프로젝트 클론:
     ```bash
     git clone <프로젝트 깃허브 URL>
     cd <프로젝트 폴더>
     ```

2. **의존성 설치**
   - Flutter 패키지 설치:
     ```bash
     flutter pub get
     ```

3. **프로젝트 실행**
   - 에뮬레이터 또는 실제 기기에서 앱 실행:
     ```bash
     flutter run
     ```