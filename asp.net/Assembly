## 닷넷의 Assembly란?
1. Assembly는 하나 이상의 모듈이나 리소스 파일들에 대한 논리적인 그룹이다.

2. 하나의 Assembly는 재사용, 보안, 버전 관리의 가장 작은 단위이다.

CLR 환경에서는 하나의 assembly를 컴포넌트(Component)라고 부른다. 이게 정말 처음 들으면 헷갈리는데, 일단 그냥 exe 파일이나 dll 파일이 assembly 단위라고 생각하자. 
솔루션 안의 프로젝트가 하나의 assembly가 될 수 있으며, 프로젝트 안에서 참조하고 있는 dll 파일도 각각 하나의 assembly다. 그래서 assembly가 논리적인 그룹이라는 정의가 존재하는 것이다.

Microsoft가 aseembly라는 개념을 소개한 것은 우리가 '재사용 가능한 타입'이라는 것에 대해서 논리적인 개념과 물리적인 개념을 구분해서 생각하는 것을 도와주기 때문이다.

예컨대 물리적인 관점에서 aseembly는 여러 개의 타입들로 구성될 수 있으며, 따라서 자주 사용하는 타입들과 그렇지 않은 타입들을 따로 구분해서 분리된 파일에 저장할 수 있다.

한편 논리적인 관점에서 assembly는 타입에 대한 정의가 담겨 있는 파일과 리소스 파일들을 묶은 collection이며 하나의 assembly를 만들면서 여러 다른 프로그래밍 언어로 만든 타입을 하나로 통합할 수 있다. 
예를 들어 어떤 타입은 C#으로 만들고 다른 어떤 타입은 VB.NET으로, 또 다른 어떤 타입은 CLR을 지원하는 다른 프로그래밍 언어로 만들어 포함시킬 수도 있다. 
언어가 다르기 때문에 분리되어 있는 각 소스 코드들은 해당 언어의 컴파일러로 컴파일된 이후에 하나의 assembly로 통합될 수 있다. 

아래 그림이 이 내용을 잘 나타내 준다.

![image](https://github.com/gami03/TIL/assets/128332485/2bbbb65a-5a72-444f-8fd3-c2fee899ab75)

위 그림에서는 여러 개의 managed module과 resource file이 별도의 도구(컴파일러 등)에 의해서 하나의 assembly로 통합됐다. 
Assembly는 이처럼 여러 파일들을 포함하는 그룹이며 단일 entity인 것이다. 
때문에 컴파일러는 Assembly 하나 당 하나의 PE32 또는 PE32+ 파일을 생성하며, 이 파일 안에는 파일들의 논리적인 그룹핑 정보가 담겨있는 동시에 manifest라는 데이터 블록도 적재된다.

manifest는 사실 metadata table의 집합 그 이상도 이하도 아닌 파일이다. 
이 table들은 assembly를 구성하고 있는 파일들과 assembly 밖으로 드러난 public 타입들, 그리고 이 assembly와 연관된 리소스나 데이터 파일들이 어떤 것인지에 대한 상세한 정보를 가지고 있다. 
다음은 managed module을 assembly로 통합하기 위해서 필요한 manifest의 metadata table들의 종류와 설명이다.

![image](https://github.com/gami03/TIL/assets/128332485/bba2d355-1ff5-4379-852f-94dcad07c725)
