# ADO.Net 이란?

닷넷 환경에서 어떠한 언어(C#, VB.Net, J#,C++.Net)를 사용하여 DataBase 관련 Application을 만들든지 ADO.Net이라는 기술은 공통적으로 적용 가능합니다. 
즉 어떤 언어에서든지 같은 클래스를 가져다 쓴다는 이야기 입니다. 

- C# 과 .Net Framework 에서 관계형 , 테이블 지향적인 형식의 데이터에 접근하는데 사용하는 일련의 클래스에 붙인 이름 입니다.
- Microsoft Accss 와 SQL Server, Oracle 과 같은 관계 형 데이터베이스 뿐 아니라 비 관계형 데이터 원본도 조작이 가능 합니다. 
- .Net Framework 안에 통합 되어 있으며 .NET 언어들 (특히 C#) 과 같이 쓰이도록 설계 되었습니다.

기존의 ADO 와 비교해 볼 때 ADO.Net 은 확장성과 상호 운영성이 개선된 ADO 입니다. 
ADO가 연결 지향형인데 반해 ADO.Net 의 경우 비 연결성 데이터 집합을 처리 하도록 설계 되었습니다. 
연결이 끊어진 레코드 집합은 응용 프로그램에만 도움이 되는데 이는 데이터를 로컬 상태에서 보다 빠르게 처리하고 전송 할 수 있기 때문이다. 
또한 ADO.Net 은 XML 을 보편적인 데이터 전송 형식으로 사용하고 있습니다.

ADO.Net 은 System.Data.dll 어셈블리 안에 들어 있는데 ADO.Net 의 모든 클래스들이 System.Data.dll 안에 들어 있으므로 결국 System.Data.dll 자체가 곧 ADO.Net 이라고 할 수 있습니다. 
그럼 왜 이름을 Syste,.Data 라고 하지 않고 ADO.Net 이라고 했을까? 
ADO.Net 이라는 이름은 ADO(ActiveX Data Object) 로부터 따온 것입니다. 
<br>MS 는 .NET 환경에서 권장 되는 데이터 액세스 인터페이스 임을 나타내기 위해 ADO.Net 이라고 명명 한 것입니다.

.NET Framework 에서의 클래스 라이브러리 (Class Library) 들을 굳이 다시 크게 나누어, Base Class Library 와 그 외의 클래스 라이브러리 (Class Library) 로 구분하자면, 
Base Class Library(BCL) 에는 Collections 나 IO 등과 같은 프로그래밍에 있어서의 좀 더 근원적인 알고리즘(Algorithm) 과 자료구조 및 하드웨어(Hardware) 에 보다 근접한 부분에 해당한다고 볼 수 있습니다. 
그 외의 라이브러리들에는 Directory Service, XML Support 등과 같은 보다 추상적이고 다양한 종류의 라이브러리를 접할 수 있고 그 중의 하나가 ADO.NET 이라고 불리는 데이터 (Data) 관련 클래스 라이브러리 (Class Library) 입니다.

## 아키텍쳐 개요(Architectural Overview)

ADO.Net 에서 개체들을 크게 소비자 (Consumer) 개체들과 .Net 데이터 공급자 ( .NET Data Providers) 개체들로 분리 해 볼 수 있습니다. 
공급자 개체들은 Connection, Command, DataReader, DataAdapter 개체 들이며 소비자 개체들은 DataSet, DataTable, DataColumn, DataRow, DataRelation 개체 등으로 구성 되어 있습니다. 
데이터 원본에 대한 실질적인 데이터 읽기 및 쓰기는 공급자에 국한된 개체에서 일어 납니다. 
데이터를 일단 메모리로 읽어 들인 후에는 소비자 개체들을 이용하여 조작 하는데, 즉 소비자 개체들은 연결이 끊어진 상태에서 작동 한다고 볼 수 있습니다. 
다시 말하면 데이터 베이스와 연결이 끊어진 상태에서 메모리 안에 있는 데이터를 다루는 것 입니다. 
반면 공급자 개체들은 연결이 되어 있는 상태에서 작동을 합니다. 
일단 공급자 개체들을 이용하여 데이터를 읽은 후 메모리 안의 데이터를 소비자 개체들로 조작하고 변경된 것들을 다시 공급자 개체들을 통해 데이터 원본에 보내는 방법을 취하고 있습니다.

### 공급자 개체(Data Providers) OverView

- Connection 개체 : 가장 먼저 사용되는 개체로 데이터 원본에 대한 기본적인 연결을 제공 합니다 .

- Command 개체 : 데이터 베이스에 수행 하는 명령 (“select * from emp”) 을 대표 합니다 . SQL Server 에 대한 구체적인 명령 개체는 SqlCommand 이고 OLE DB 인 경우 OleDbCommand 입니다.

- DataReader 개체 : 데이터 원본으로부터 forward only, read only 등의 데이터를 빠르고 손 쉽게 얻을 수 있는 개체 입니다 . 단순히 데이터를 읽는 경우라면 이 개체가 가장 좋은 성능을 냅니다 . SQL Server 용으로는 SqlDataReader, OLE DB 용으로는 OleDbDataReader 가 있습니다 .

- DataAdapter 개체 : 이것은 데이터 원본에 대한 다양한 작업 ( 갱신 , DataSet 채우기 ) 을 수행하는 법용적인 클래스 입니다 . SQL Server 의 경우 SqlDataAdapter, OLE DB 인 경우 OleDbDataAdapter 가 쓰입니다 .



### 소비자 개체 OverView

- DataSet 개체 :
  <br> 이 개체는 응용 프로그램 안에서 하나의 단위로 참조되는 관련된 테이블들의 집합을 대표 합니다.
  <br>예를들어 Customers, Orders, Products 의 모든 고객들과 그들이 주문한 제품들은 하나의 DataSet 에 담기는 것이 가능 하며 이 개체를 이용하면 원하는 데이터를 각 테이블로부터 빨리 가져와 서버와 연결이 끊어진 상태에서 데이터를 변경 하고,
  다시 한번의 명령으로 변경된 것들을 데이터 베이스 서버에 저장 할 수 있습니다.
  <br>한마디로 데이터 테이블 컬렉션, 관계 및 제약 조건으로 구성되어 있는 데이터의 집합입니다. DataSet안에는 데이터 테이틀 컬렉션(DataTableCollection)이 있어서 DataTable들을 가질 수 있습니다.

- DataTable 개체 :
  <br> 이 개체는 DataSet 안의 하나의 테이블을 나타 냅니다 . 각각의 Customers, Orders, Products 등

- DataColumn 개체 :
  <br> 이 개체는 테이블 안의 하나의 열 (Column) 을 대표 합니다.

- DataRow 개체 :
  <br> 이 개체는 테이블의 하나의 행 (Row) 을 대표 합니다.


### DataVeiw
DataView는 DataTable의 데이터들을 정렬하거나 필터링하면 만들어지는 개체입니다.

## 네임스페이스의 사용

C# 에서 ADO.Net 을 사용하는 첫번째 단계는 모든 ADO.NET 클래스들이 있는 System.Data NameSpace 에 참조를 정의 하는 것인데 아래와 같이 using 문을 사용해야 합니다 .
<br><br> using System.Data;

- SQL Server .Net 공급자를 위한 using 문
<br><br> using System.Data.SqlClient;

- OLE DB .NET 공급자를 위한 using 문
<br><br> using System.Data.OleDb;

- Oracle 전용 Data Provider for .Net 의 경우 using 문
<br><br> using System.Data.OracleClient;

- ODBC .Net 공급자
<br> OLE DB 공급자를 제공 하지 않는 데이터 원본 ( 예를들어 PostageSQL 등등 ) 이라면 ODBC .Net 공급자를 사용 하면 됩니다. ODBC .Net 데이터 공급자 (Data Provider) 는 VS.Net 과는 별개로 다운 받아야 합니다.

![image](https://github.com/gami03/TIL/assets/128332485/68ad5d8f-6dc1-450e-a8f7-02ac3e7b2373)

![image](https://github.com/gami03/TIL/assets/128332485/c97fad21-f1fc-4bc8-8f07-7ce35df9e28d)

ADO.NET에는 또한 아래와 같은 공통 인터페이스와 추상 클래스가 있다.

![image](https://github.com/gami03/TIL/assets/128332485/18f6c435-13de-4495-88a4-c6edb9deded3)
