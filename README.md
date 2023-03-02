# Practicing-Unity

### 1. 변수 : 데이터를 메모리에 저장하는 장소
 
int : 정수형 데이터

float : 숫자형 데이터(소수점을 포함한). 끝에 꼭 f를 써야한다.

string : 문자열 데이터. 문자열 데이터는 양 끝에 " " 를 써준다.

bool : 논리형 데이터. true, false 두가지만 존재

 

ex)

int level = 5;

float strength = 15.5f  => float 쓸 때는 뒤에 f붙이기

string playerName = "검사";

bool isFullLevel = false;


변수의 타입과 이름을 정하는것이 선언

그것에 값을 넣는것은 초기화


프로그래밍은 선언 > 초기화 > 호출(사용) 순으로 흘러간다.

// (주석) : 실행되지 않는 메모와 같은 역할

### 2. 그룹형 변수 : 변수들을 묶은 하나의 장소
배열 : 가장 기본적인 고정형 그룹형 변수

프로그래밍에서의 시작 순번은 0부터 

ex)

string[] monsters = { "슬라임", "사막뱀", "악마" };

int[] monsterLevel = new int[3];
monsterLevel[0] = 1;
monsterLevel[1] = 6;
monsterLevel[2] = 20;

* 제네릭 : <타입>의 List 생성
List<string> items = new List<string>();
items.Add("생명물략30");
items.Add("마나물략10");

### 연산자 : 상수, 변수값을 연산해주는 기호
 

ex)

        int exp = 1500;

        exp = 1500 + 320;
        exp = exp - 10;
        level = exp / 300;
        strength = level * 3.1f;

 

% : 몫이 아닌 나머지를 출력

 

ex)

        int nextExp = 300 - (exp % 300);

 

 

프로그래밍 부등호 : >(초과), <(미만), >=(이상), <=(이하),
&&(and) : 두 값이 모두 true 일 때 true 출력

||(or) : 두 값중 한가지만 true여도 true를 출력

 

### 4. 키워드 : 프로그래밍 언어를 구성하는 특별한 단어
int float string bool new List 등

변수 이름, 값 등으로 사용할 수 없다.

 

### 5. 조건문 : 조건에 만족하면 로직을 실행하는 제어문
 

if : ( )안의 조건이 true 일 때 { } 안의 로직을 실행

( ) 안에는 bool 타입의 조건이 필요

 

 else : 앞의 if문의 로직이 실행되지 않으면 실행

 

ex)

        if (condition == "나쁨") {
            Debug.Log("플레이어의 상태가 나쁘니 아이템을 사용하세요.");
        }
        else {
            Debug.Log("플레이어의 상태가 좋습니다.");
        }

        if (isBadCondition && items[0] == "생명물약30"){
            items.RemoveAt(0);
            health += 30;
            Debug.Log("생명포션30을 사용하였습니다.");
        }
        else if (isBadCondition && items[0] == "마나물약10"){
            items.RemoveAt(0);
            mana += 30;
            Debug.Log("마나포션10을 사용하였습니다.");
        }

 

switch. case : 변수의 값에 따라 로직을 실행

 

ex)

        string monsterAlarm;
        switch (monsters[1]){
            case "슬라임":
            case "사막뱀":
                monsterAlarm = "소형 몬스터가 출현!";
                break;
            case "악마":
                monsterAlarm = "중형 몬스터가 출현!";
                break;
            case "골렘":
                monsterAlarm = "대형 몬스터가 출현!";
                break;
            default:
                monsterAlarm = "??? 몬스터가 출현!";
                break;
        }

 

### 6. 반복문 : 조건에 마족하면 로직을 반복하는 제어문
while : ( )안의 조건이 true일 때, { }안의 로직을 반복 실행

break : 로직 반복 실행을 하지 말고 로직을 빠져 나감

 

        while (health > 0)
        {
            health--;
            if (health > 0)
                Debug.Log("독 데미지를 입었습니다." + health);
            else
                Debug.Log("사망하였습니다.");

            if (health == 10)
            {
                Debug.Log("해독제를 사용합니다.");
                break;
            }
        }

 

for : 변수를 연산하면서 로직 반복 실행

 

        for (int count = 0; count < 10; count++)
        {
            health++;
            Debug.Log("붕대로 치료중...." + health);
        }

        for (int index = 0; index < monsters.Length; index++)
        {
            //Debug.Log("이 지역에 있는 몬스터:" + monsters[index]);
        }

 

 

foreach : for의 그룹형변수 안에 있는 아이템을 직접 가져와서 사용


        foreach (string monster in monsters)
        {
            Debug.Log("이 지역에 있는 몬스터:" + monster);
        }
     }

 

### 7. 함수(메소드) : 여러 기능을 편하게 사용하도록 구성된 영역
 

지역변수 : 함수 안에서 선언된 변수 

전역변수 (멤버변수) : 함수 밖에서 선언된 변수

return : 함수가 값을 반환할때 사용

 

        health = Heal(health); 

 

    int Heal(int currentHealth)
    {
        health += 10;
        Debug.Log("힐을 받았습니다." + currentHealth);
        return currentHealth;
    } 

 

void : 반환 데이터가 없는 함수 타입

 

    void heal()
    {
        health += 10;
        Debug.Log("힐을 받았습니다." + health);
    }

 

 

 

함수와 반복문을 통해서 로직을 만든 예

 

   }

        for (int index = 0; index < monsters.Length; index++) 
        { 
            Debug.Log("용사는" + monsters[index] + "에게" + Battle(monsterLevel[index])); 
        }
    }

 

 

   string Battle(int monsterLevel)
    {
        string result;
        if (level >= monsterLevel)
            result = "이겼습니다.";
        else
            result = "졌습니다.";
        return result;
     }

 

 

### 8. 클래스 : 하나의 사물(오브젝트)와 대응하는 로직
class : 클래스 선언에 사용

private : 외부 클래스에 비공개로 설정하는 접근자

public : 외부 클래스에 공개로 설정하는 접근자

Monobehavoir : 유니티 게임 오브젝트 클래스

 

 

public class C_actor
{
public int id;
public string name;
public string title;
public string weapon;
public float strength;
public int level;

public string Talk()
{
return "대화를 걸었습니다.";
}

public string HasWeapon()
{
return weapon;
}

public void LelvelUp()
{
level = level + 1;
}
}

 

 

 

        C_actor player = new C_actor();
        player.id = 0;
        player.name = "나법사";
        player.title = "현명한";
        player.strength = 2.4f;
        player.weapon = "나무지팡이";
        Debug.Log(player.Talk());
        Debug.Log(player.HasWeapon());

        player.LelvelUp();
        Debug.Log(player.name + "의 레벨은" + player.level+"입니다.");

