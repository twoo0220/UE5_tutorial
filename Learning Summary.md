# 입문자를 위한 UE5. Part4 언리얼 엔진 C++

## 없어도 상관없는 폴더

- Binaries : 최종 결과물, 실행 파일
- DerivedCache : 폴더명에서 유츄할 수 있듯이 캐시 파일들이기 때문에 없어도 무방
- Intermediate : 중간 컴파일, 임시 파일들
- Saved : 임시 로그와 스크린샷들
- 위 폴더들을 삭제해도 다시 생성할 수 있으나 시간이 걸림
- uproject → 우클릭 → Generate Visual Studio project files 선택하면 재생성

## 지우면 안되는 폴더

- Config : 언리얼엔진 기본 설정
- Content : 리소스 저장소, 맵, 아트 등등
- Source : 소스 파일들

## 기본 내용

- 기본적으로 C++, C#을 자주 사용하지만 블루프린트를 종종 사용하며, 애니메이션 등을 볼 때는 유용하므로 제3의 언어 느낌으로 사용
- 언리얼 엔진 구조는 유니티와 다르게 좀 더 타이트하게 잡혀있음

## 블루프린트

- 일종의 블럭 코딩
- 블루 프린트도 내부적으로 보면 히든 Actor
  - class LevelBlueprint : public Actor
  - 클래스 내부 함수 구조로 생각하면 편함
- 블루 프린트의 상자(노드) 하나가 함수라고 보면 됨
  - 노드 위치와 관계없이 선(링크)로 연결된 순서대로 실행
  - 선을 누르고 우클릭해서 Break this link 해도 되지만 번거로우니 Alt + 왼쪽 키 누르면 취소됨
- 주석을 남기고 싶으면 단축키 C (Comment)
  - 주석을 남기고 싶은 노드 선택 후 블럭 단위로 남길 수 있음
- 코드 작업 후 컴파일 저장해줄 것
- BeginPlay
  - 블루프린트 시작할 때 딱 한번 실행
- Tick
  - 매번 실행
- 블루 프린트에서 작업하는 변수들은 멤버변수에 가깝다고 볼 것
  - 변수 추가 후 오른쪽 Details 창에서 단일 변수냐 배열이냐, Map이냐를 선택할 수 있음
- Float과 double이 통합되어서 전부 Float 이라 보면 됨
- Name과 String과 Text
  - 언리얼 엔진 내부에서 거의 변하지 않는 것들은 Name으로 해주면 좋음. 리소스 이름 등등 해쉬값을 떠서 빠르게 비교할 수 있는 값들
  - String은 자주 변하는 값들
  - Text는 다국어 시스템으로 변환되는 애들. 가령 UI에서 국가별로 다르게 보여줘야할 때 등등
- getter와 setter
  - 변수를 선택한 상태에서 Ctrl 누른 채로 드래그 앤 드롭하면 getter
  - 변수를 선택한 상태에서 Alt 누른 채로 드래그 앤 드롭하면 setter
- 노드마다 F9를 누르면 Break Point가 걸림
  - VS랑 동일
  - 실행 흐름도 볼 수 있음
- Sequence
  - 실행 순서를 여러번 나눌 수 있음
- 선 정리를 도와주는 플러그인도 있음(유료)
- 블루프린트로 작업할 때는 while문 보다는 foreach를 주로 사용
- 언리얼에서는 가급적 STL과 섞어쓰지 말고 만들어놓은 템플릿 활용할 것


## Unity vs Unreal

- 유니티는 Component 개념으로 부품/레고를 붙이는 방식
  - 스크립트 역시 생성하면 Start()와 Update()가 기본적으로 만들어지는데 언리얼의 BeginPlay와 Tick과 동일
  - 부품을 자유롭게 붙이고 뗄 수 있으니 자유도가 높음
- 언리얼은 상속 개념이 주 핵심
  - 생성한 객체가 기본 상속이 Actor냐 Pawn이냐 등등
  - Actor는 박스처럼 인게임에서 배치만 하고 끝
  - Pawn은 외부 컨트롤러에 의해 조작되는 녀석
  - 따라서 언리얼은 이 기본 개념에 맞추어서 만들어야함