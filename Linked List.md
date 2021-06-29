# Linked List - 연결 리스트
각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조이다.    
이름에서 말하듯이 데이터를 담고 있는 노드들이 연결되어 있는데, 노드의 포인터가 다음이나 이전의 노드와의 연결을 담당하게 된다.
![asdf](https://user-images.githubusercontent.com/79950254/123733130-ec5bb980-d8d5-11eb-891d-24ffa04665ae.PNG)    
연결 리스트의 종류로는 단일 연결 리스트, 이중 연결 리스트 등이 있다.
***
##### 연결 리스트 구조
![캡처](https://user-images.githubusercontent.com/79950254/123733563-b3701480-d8d6-11eb-9220-1a3c4e51139c.PNG)
##### 
***
##### 배열과 연결 리스트 장단점
![캡처](https://user-images.githubusercontent.com/79950254/123733028-bae2ee00-d8d5-11eb-942b-7851d1ca9347.PNG)
***
##### 단일 연결
단일 연결 리스트는 각 노드에 자료 공간과 한 개의 포인터 공간이 있고, 각 노드의 포인터는 다음 노드를 가리킨다.
![image](https://user-images.githubusercontent.com/79950254/123733402-63914d80-d8d6-11eb-984e-6918c9faf288.png)

***
##### 이중 연결
이중 연결 리스트의 구조는 단일 연결 리스트와 비슷하지만,포인터 공간이 두 개가 있고 각각의 포인터는 앞의 노드와 뒤의 노드를 가리킨다.

![image](https://user-images.githubusercontent.com/79950254/123733426-7015a600-d8d6-11eb-9f63-4847046e5f9c.png)

***
##### 원형 연결
원형 연결 리스트는 일반적인 연결 리스트에 마지막 노드와 처음 노드를 연결시켜 원형으로 만든 구조이다.
![image](https://user-images.githubusercontent.com/79950254/123733436-79067780-d8d6-11eb-80dd-deb4e4168e64.png)
***
##### 연결리스트 구현
초기화(init) / 삽입(Insert) / 삭제(Remove)

* 초기화   
위에서 설명한 노드를 생성하는 과정. 노드를 접근하기 위해서는 맨 처음 노드의 주소를 가리킬 노드가 필요한데 이 노드를 head라고 표현함.    
나중에 구현할 삽입의 시간복잡도를 줄이기 위해 마지막 노드를 가리키는 노드 tail을 하나 만듬.삽입 기능 구현에서 자세히 설명   
초기화하는 과정에서 다음 주소를 가리키는 포인터는 null로 설정. null은 '가리키는 노드가 없음' 을 의미함.
<img width="352" alt="캡처" src="https://user-images.githubusercontent.com/79950254/123734077-9e47b580-d8d7-11eb-9598-6e8047ca0b5d.PNG">

* 초기화 코드    
<pre><code>void init(){
    head = new Node;
    tail = new Node;

    head->next = NULL;
    tail->next = NULL;
    }
</code></pre>

* 삽입
<img width="705" alt="캡처" src="https://user-images.githubusercontent.com/79950254/123734409-43628e00-d8d8-11eb-9799-f38ae5c09d8b.PNG">
 1)맨 앞에 삽입하는 방법   
 맨 앞에 노드를 추가하는 경우    
새로 추가되는 노드의 다음주소  --> 현재 head가 가리키는 주소    
head가 가리키는 주소 --> 새로 추가된 노드
<img width="741" alt="캡처" src="https://user-images.githubusercontent.com/79950254/123734485-69882e00-d8d8-11eb-95db-c486cb501aa2.PNG">
<pre><code>
void Addnode(int data){
    
    //추가할 노드 만들기
    Node *NewNode = new Node;
    
    NewNode->data = data;
    NewNode->next = NULL;
    
    //노드가 하나도 없으면 head에 연결하기
    if(head->next == NULL){
        head->next = NewNode;
    }
    else{
        
        //새로 추가되는 노드의 다음주소 --> 현재 head가 가리키는 주소
        NewNode->next = head->next;
        
        //head가 가리키는 주소 --> 새로 추가된 노드
        head->next = NewNode;
        
    }
}
</code></pre>

2) 맨 마지막에 삽입하는 방법   
head 대신 tail를 사용    
여기서 tail 노드의 필요성을 알 수 있다. 만약 tail노드가 없다면 매번 삽입할 때마다 처음부터 끝까지 탐색해야 하는 번거로움이 발생.    
그래서 매번 O(n)의 시간복잡도가 발생합. 만약 tail노드가 있다면 O(1)의 시간복잡도로 처리할 수 있다.    
맨 마지막에 추가하는 과정    
새로 추가되는 노드의 다음주소  -->  Null (마지막 노드이기 떄문에)    
tail이 가리키는 노드의 다음 주소 - > 새로 추가되는 노드   
tail이 가리키는 주소 --> 새로 추가된 노드
<img width="758" alt="캡처" src="https://user-images.githubusercontent.com/79950254/123734728-d13e7900-d8d8-11eb-8d55-c928339f740c.PNG">

3)  원하는 위치에 삽입하는 방법   
탐색을 통해 원하는 위치를 찾고 그 위치에 새로운 노드를 추가   
위 예제에서 2번째노드(4)와 3번째노드(1) 사이에 추가한다고 가정    
우선 삽입할 위치를 찾는 노드 cur (current)가 필요    
위 두 가지 경우에선 head, tail과 같은 위치는 담고 있는 노드가 있었지만, 이번 경우엔 직접 설정   
다음과 같은 과정을 통해 노드를 추가    
1. 탐색을 통해 cur노드가 4를 가리키게 만듭니다.    
2. 새로운 노드 5가 가리키는 주소 --> cur이 가리키는 노드4가 가리키는 다음 노드(1)    
3. cur이 가리키는 노드4가 가리키는 다음노드 --> 새로운 노드 5 
<img width="737" alt="캡처" src="https://user-images.githubusercontent.com/79950254/123734857-15ca1480-d8d9-11eb-8ee6-989fa849b4f4.PNG">

* 삭제    
노드의 삭제는 '원하는 자리에 삽입' 하는 과정과 유사    
그러나 삭제할 노드의 전과 삭제할 노드의 후를 연결해줘야 하기 때문에 또 하나의 노드가 필요   
이 노드를 pre라고 표현    
삭제할 노드를 1 이라고 가정
<img width="746" alt="캡처" src="https://user-images.githubusercontent.com/79950254/123735041-70637080-d8d9-11eb-9079-9b402007dc5e.PNG">
1. 탐색을 통해 삭제할 노드를 cur이 가리키게 하고 , 삭제할 노드의 바로 전 노드를 pre가 가리키게 합니다.
2. pre가 가리키는 노드의 다음 주소 --> cur이 가리키는 다음 주소 
3. cur이 가리키는 노드는 free합니다.
<pre><code>
void RemoveNode(int remove_data){
    Node *cur = head->next;
    Node *pre = head;
    
    
    //탐색을 통해 삭제할 노드를 cur이 가리키게 하고
    //삭제할 노드의 바로 전 노드를 pre가 가리키게 합니다.
    while(cur->data != remove_data){
        pre = cur;
        cur = cur->next;
    }
    
    //pre가 가리키느 노드의 다음 주소 --> cur이 가리키는 다음 주소
    pre->next = cur->next;
    
    //cur이 가리키는 노드 free
    free(cur);
    free(pre);
}
</code></pre>
