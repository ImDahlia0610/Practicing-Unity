# 게임 오브젝트(GameObject)
### 게임 오브젝트(GameObject) 란?

'게임 속에 존재하는 모든 오브젝트'이며, 기능을 수행하는 컴포넌트(Components)의 컨테이너 역할을 합니다.

게임 오브젝트 자체로는 아무것도 할 수 없으며, 캐릭터, 환경, 특수 효과가 될 수 있으려면 먼저 프로퍼티를 부여해야 합니다.

 

간단히 예시를 들면 게임 오브젝트를 빈 냄비라고 생각하고 컴포넌트를 게임 요리에 사용되는 다양한 재료라고 생각할 수 있습니다.

 

컴포넌트 예) 캐릭터, 아이템, 광원, 카메라, 특수 효과 등..

 

 

### 사용법

 

#### 게임 오브젝트 생성

- Hierarchy 창에서 우클릭을 하면 아래 사진같이 창이 뜨는데 여기서 Create Empty를 클릭하면 게임 오브젝트가 생성됩니다.

- 단축키는 Ctrl + Shift + N / Cmd + Shift + N을 누르면 생성됩니다.

 
#### 게임 오브젝트 컴포넌트


#### Transform
게임 월드와 씬 뷰에서 게임 오브젝트의 위치, 회전, 스케일을 설정할 수 있는 컴포넌트이며, 이 구성 요소를 제거할 수 없습니다.

트랜스폼의 포지션, 회전 및 스케일 값은 트랜스폼 부모를 기준으로 측정됩니다.

트랜스폼에 부모가 없는 경우 프로퍼티는 월드 공간에서 측정됩니다.

#### 속성	 기능
Position	 X, Y, Z 좌표에서의 트랜스폼 포지션

Rotation	 X, Y, Z 축 주변의 트랜스폼 회전으로, 도 단위로 측정

Scale	 X, Y, Z 축을 따르는 트랜스폼 스케일이며, “1” 값은 오리지널 크기(오브젝트를 임포트했을 때의 크기)입니다.
 

 

자주 사용하는 문법

 

- GameObject

새 게임 오브젝트를 생성합니다.

 

GameObject player = new GameObject("Player");
 

- AddComponent

게임 오브젝트에 구성 요소를 추가합니다.

 

Text name = gameObject.AddComponent<Text>();
 

- GetComponent

다른 구성 요소에 액세스 하는 기본 방법입니다. 이 함수를 사용하여 내장 구성 요소 또는 스크립트에 모두 액세스 할 수 있습니다. 해당 게임 오브젝트가 추가한 컴포넌트 타입을 반환하며, 없다면 null를 반환합니다.

 

GameObject player = new GameObject("Player");
Text name = player.GetComponent<Text>();
 

- SetActive

GameObject를 활성화 / 비활성화합니다.

게임 오브젝트를 비활성화하면 모든 컴포넌트가 비활성화되고 연결된 렌더러, 충돌체, 리지드 바디, 스크립트 등이 꺼집니다 Update(). 예를 들어 게임 오브젝트에 연결 한 모든 스크립트는 더 이상 호출되지 않습니다.

 

gameObject.SetActive(false);
 

- Instantiate

오브젝트의 인스턴스 ID를 반환하며, 선택한 오브젝트를 복제해서 생성합니다.

GameObject 또는 Component를 복제하면 모든 하위 개체 및 구성 요소도 해당 속성과 함께 복제됩니다. 

그러나 복제된 개체의 부모 속성은 null이므로 원본의 개체 계층에 속하지 않습니다.

복제 시 GameObject의 활성 상태가 전달되므로 원본이 비활성 상태이면 복제도 비활성 상태로 생성됩니다.

 

 Missile missileCopy = Instantiate<Missile>(missile);
 

- Find

게임 오브젝트를 찾는 함수이며, 게임 오브젝트를 찾을 수 없다면, null이 반환됩니다

성능상의 이유로 매 프레임 마다이 함수를 사용하지 않는 것이 좋습니다.

대신 시작 시 멤버 변수에 결과를 캐시 하거나 GameObject.FindWithTag를 사용하십시오.

이 기능은 로드 시 다른 객체에 대한 참조를 자동으로 연결하는 데 가장 유용합니다.

일반적인 사용 패턴은 MonoBehaviour.Start 내부의 변수에 게임 오브젝트를 할당하는 것입니다. 

그리고 MonoBehaviour.Update에서 변수를 사용하십시오.

 

GameObject message = GameObject.Find("Message");
 

- FindWithTag

태그 된 하나의 활성 GameObject를 반환합니다. 게임 오브젝트를 찾지 못했으면 null을 반환합니다.

태그가 존재하지 않거나 빈 문자열이나 null이 태그로 전달되면 UnityException을 발생합니다.

 

GameObject player = GameObject.FindWithTag("Player");
 

- FindGameObjectsWithTag

태그 된 활성 게임 오브젝트 리스트를 반환합니다. 게임 오브젝트를 찾지 못했다면, 빈 배열이 반환됩니다.

태그가 존재하지 않거나 빈 문자열이나 null이 태그로 전달되면 UnityException을 발생합니다.

 

GameObject[] monster = GameObject.FindGameObjectsWithTag("Monster");
 

- Destroy

게임 오브젝트, 컴포넌트나 애셋을 삭제합니다.

실제 객체 제거는 항상 현재 업데이트 루프 이후까지 지연되지만 항상 렌더링 전에 수행됩니다.

 

// 게임 오브젝트 제거
Destroy (gameObject); 

// 게임 오브젝트에서 스크립트 인스턴스를 제거
Destroy (this); 

// 객체를 로드 한 후 5 초 안에 게임 객체를 제거
Destroy (gameObject, 5); 
 

- DontDestroyOnLoad

새로운 Scene이 로드될 때 자동으로 파괴되지 않는 target 오브젝트를 만듭니다.

개체가 구성 요소 또는 게임 개체인 경우 전체 변환 계층도 파괴되지 않습니다.

 

DontDestroyOnLoad (transform.gameObject);
 
