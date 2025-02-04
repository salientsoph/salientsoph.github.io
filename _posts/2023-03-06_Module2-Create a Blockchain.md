---
layout: single 
title: "Module2-Create a Blockchain"
categories: 블록체인
tags: [blockchain, blockchainA-Z]
toc: true
toc_sticky: true
toc_label: 목차
---

강의 목록

: 3가지 블록체인 기술을 생성해본다. 

Module1. Create a Blockchain 

Module2. Create a Cryptocurrency

Module3. Create a Smart Contract



이를 위해서 아나콘다IDE를 설치한다. 파이썬을 이용해 블록체인, 암호화폐를 생성할 예정. 

Spyder(studio)가 아나콘다에 가장 좋은 IDE.





## 01. step1

### Python vs Anaconda

1. anaconda란? 

   - 라이브러리들을 쉽게 설치하고 관리할 수 있게 해주는 도구
   - 수학, 과학 분야에서 사용되는 여러 패키지를 묶어 놓은 파이썬 배포판
   - 특히 최근 데이터 사이언스와 머신 러닝 분야에서 파이썬을 사용하기 위해 기본적으로 설치하는 배포판이 되었다.

   ![img](https://t1.daumcdn.net/cfile/tistory/99CD603A5C5DB5301B)

   - sklearn : (scikit-learn) 머신러닝 교육을 위한 파이썬 패키지

   - pandas(판다스) : 데이터 분석, 데이터 처리 등을 쉽게 하기 위해 만들어진 패키지

   - numpy(넘파이) : 벡터, 메트릭스, 고수준의 배열 등등, 과학계산 컴퓨팅에 사용되는 패키지

   - scipy(사이파이) : 고급 수학 함수, 수치적 미적분, 미분방정식 계산, 최적화, 신호 처리 등을 위한 다양한 과학 기술 계산 기능을 제공하는 패키지

2. 파이썬

   - 기본적으로 패키지 관리 시스템인 pip만을 포함하고 있음

     - 필요한 툴, 패키지가 있다면 pip을 통해 수동으로 추가해야 한다. 

     - 이 작업은 컴퓨터 자체에 적용되기 때문에, 프로젝트를 여러번 진행하다 보면 필요한 패키지는 2~3개 정도면 된다.. 10개~15개의 패키지들이 설치되어 필요 이상으로 공간을 차지하기도 합니다.

       -> 하지만, 아나콘다를 사용하면 이런 문제를 해결할 수 있다!

       -> 아나콘다는 가상환경을 만들어 그 안에 필요한 패키지들을 설치하고, 그 가상환경안에서 다른 모든 요소들과 '논리적' 으로 분리되어 개발환경이 조성된다. 



### 환경 세팅

1. Anaconda를 다운로드 받는다. (파이썬 3.6 버전을 다운받아야 한다.)

   - 아나콘다는 그냥 최신 것으로 받았다.

   - https://www.anaconda.com/
   - https://repo.anaconda.com/archive/

2. terminal 에서 `conda install python=3.6` 입력 (실패)

2-1. terminal에서 `conda create -n new_environment python=3.6` 입력 (성공)

(참고. https://stackoverflow.com/questions/53972362/how-to-downgrade-python-from-3-7-to-3-5-in-anaconda)

2-2. 위에서 가상 환경을 바꿔준다. (강의에선 root에서 하라고 권장함.)

- 파이썬에서 가상 환경(virtual environment)은 하나의 PC에서 프로젝트 별로 독립된 파이썬 실행 환경(runtime/interpreter)을 사용할 수 있도록 해준다.
- venv 모듈은 virtualenv의 경량화된 모듈.

![Screen Shot 2023-01-05 at 8.37.05 PM](/Users/salient/Desktop/untitled folder/Screen Shot 2023-01-05 at 8.37.05 PM.png)

3. 추후 설치 예정인 패키지들 
   - flask
   - request: 블록을 채굴하거나, 블록체인에 새로운 트랜잭션 추가를 위한 패키지
   - postman: 블록체인과의 상호 작용하기 위해 사용자 친화적인 패키지
     - 기존 cURL(블록체인과 상호 작용할 수 있지만 일부 bash 코드를 사용한다)과는 다르게 사용자 친화적이다. 
4. IDE를 선택한다. 
   - Jupyter Notebook: LaTex로 작성한 수학을 코드에 포함할 때 주로 사용(논문 쓸 때..)
   - Spyder: 사용하기 쉽고, 실용적인 도구가 많음 
5. Spyder 설치 후 들어가서 new file 로 파일 하나 생성해본다. 
   - 설치 시, Install Specific Version 가서 가장 최신 거 다운로드 받으려다가 충돌나서, 적당히 골라서 설치했다. (5.0.3 버전)





## 02. step2

### Flask 설치 

1. 설치 이유
   - 블록체인을 포함시킬 웹 애플리케이션 구축에 사용할 웹 프레임워크 
   - 일부 서버를 이용해서 누구나 온라인에서 사용할 수 있는 블록체인을 만들기 위해 

2. Flask란?

3. 설치 방법
   1. 터미널에서 `pip install Flask==0.12.2` 하랬지만.. `2.0.3` 버전 다운로드함(python 3.6을 사용할 수 있는 버전 중에 가장 최근 걸로 검색)
      - windows의 경우, anaconda prompt 에서 실시



### Postman 설치

1. 설치 이유
   - 서버를 요청하기 위한 것 
   - 기존 cURL보다 사용자 친화적 인터페이스를 가졌음
2. Postman이란?
   - HTTP 클라이언트 
   - API 개발을 빠르고 쉽게 개발된 플랫폼
   - API를 만들수도, 공유할수도, 테스트에 문서화까지 가능하며, API로 리퀘스트해서 나오는 응답까지 확인할 수 있는 툴
3. 설치 방법
   1. https://www.postman.com/downloads/
   2. 설치 필요 x (그냥 어플리케이션으로 나옴)
4. Request
   - Get: 블록체인의 실제 상태를 확인하거나, 블록을 채굴하는 경우에 사용
   - Post: 일부 사이에 발생하는 새로운 트랜잭션 추가에 사용
     - 발신자 주소와 수신자 주소 및 교환된 코인의 양을 입력할 때, Json 파일을 사용하기 때문에 Get 대신 Post를 사용한다. 





## 03. step3

파트를 2개로 나누어 설계한다. 

파트1 - 블록체인 설계 (블록체인의 아키텍쳐)

파트2 - 2가지 함수 생성 (postman에 블록체인의 상태를 표시하는 함수, 블록체인에서 새로운 블록을 채굴하기 위한 함수)



1. 라이브러리를 import 한다 

   ```python
   #Importing the libraries 
   import datetime 
   import hashlib
   import json 
   from flask import Flask, jsonify 
   ```

   - datetime: 각 블록마다 블록이 생성되고 채굴된 정확한 날짜의 타임스탬프를 가짐
   - hashlib: 블록을 해시할 때 사용함
   - json: 블록을 해시하기 전 블록 인코딩을 위해 dumps 함수 사용을 위해
   - Flask: 웹 애플리케이션이 되는 Flask 클래스의 객체를 생성
   - jsonify
     - postman에서 블록체인과 상호작용할 때 메세지를 보내기 위해 사용하는 함수
     - 예시1) postman에서 전체 블록체인을 표시하기 위해 블록체인의 실제 상태를 요청할 때 사용 - Jsonify를 이용해 요청에 관한 응답을 표시함
     - 예시2) 새로운 블록을 채굴하여 블록체인에 추가할 때. Jsonify 함수를 이용해 Json 형식으로 채굴된 새로운 블록의 핵심 정보로 돌아감

2. 블록체인 설계 

   - 몇 가지 옵션이 있음 

     1. 몇 가지 함수를 만들고, 블록체인을 설계할 때 함수를 사용하는 것 - 좋지않음, 블록체인은 수많은 블록들이 계속 추가되어야 하기 때문.
     2. 가장 좋은 방법은 클래스를 만드는 것. 클래스는 속성, 함수, 도구, 메서드 등을 포함할 수 있기에 설계하려는 것과 상호작용함. 
        - ex) 자율 주행 차 클래스: 자율 주행 차의 모든 속성을 클래스에서 정의 + 전진, 후진, 좌회전, 우회전, 가속, 브레이크 등 메서드를 정의

   - 클래스 정의

     ```python
     Class Blockchain:
         def __init__(self): 
             self.chain = []
             self.create_block(proof = 1, previous_hash = '0')
     ```

     - 클래스 안에선 모든 컴포넌트와 특징을 정의한다. 

     - 클래스를 생성할 때 원하는 만큼의 객체를 생성할 수 있다.

     - init 메서드: 

       1. 블록이 포함될 체인을 초기화한다. 
       2. 제네시스 블록(블록체인의 첫 번째 블록) 생성
          - chain: 나중에 채굴할 다른 블록에 첨부할 예정
          - create_block: 블록을 생성하는 메서드 
          - proof: 각 블록은 자체 증명을 가지고 임의의 값을 선택할 수 있음 
          - previous_hash: 각 블록은 이전 블록과의 링크인 Prev.hash 값을 가짐
          - proof = 1, previous_hash 값은 없으므로 임의의 값을 넣어줌(보통 '0'을 넣는다.)
            - '0': 인코딩된 문자열만 수용하는 hashlib 라이브러리에서 SHA256 함수를 사용하기 때문에 '0' 으로 입력. 

       - 늘 self 라는 인수를 지님
         - self: 클래스가 생성되면 생성하는 객체(클래스의 인스턴스 객체)에 적용됨 





## 04. step4

### create_block function vs mine_block function

1. create_block function

   - 채굴 직후, create_block 함수를 적용한다. 

   1. 인덱스, 타임스탬프, 증명, Prev.hash 등 다양한 특성의 블록을 생성한다. 
   2. 새롭게 채굴한 블록을 블록체인에 추가한다. 



2. mine_block function
   - 해결해야할 작업 증명을 얻게 된다. 
   - 문제를 정의하고, 작업 증명을 찾기 위한 알고리즘을 정의한다. 
   - 작업 증명을 찾으면, 새로운 블록이 채굴됨. 블록체인에 추가할 수 있다. 





### create_block function

```python
Class Blockchain:
    def create_block(self, proof, previous_hash):
        block = {'index' : len(self.chain) + 1,
                 'timestamp': str(datetime.date.now()),
                 'proof': proof,
                 'previous_hash': previous_hash
                 }
        self.chain.append(block)
        return block
```

1. 블록체인의 각 블록을 4개의 필수 키로 정의하는 dictionary를 만든다.  

   1. 블록의 인덱스
      - chain의 길이를 가져와서 + 1
   2. 블록이 채굴된 정확한 시간인 타임스탬프
      - string으로 변환해야 Json 형식으로 작업할 때 형식 문제가 발생하지 않는다. 
   3. 이 블록을 새로 채굴할 때 괜찮았다는 proof 
   4. previous hash
   5. (나중에 추가 예정) 암호화폐의 트랜잭션이 될 데이터

2. 사용 시기

   - 작업 증명 해결 직후(블록 채굴 직후)에 사용한다.

   - mine_block 함수 끝에 create_block 함수를 적용한다.

     - mine_block 함수

       1. 먼저 작업 증명을 해결해 증명을 얻는다. 

       2. create_block 함수를 적용한다. 





## 05. step5

### get_previous_block function

- 이전 블록 호출 방법

- 현재 체인의 마지막 블록을 이용한다. 

  ```python
  Class Blockchain:
      def get_previous_block(self):
          return self.chain[-1]
  
  ```

  - self.chain[-1]: -1은 체인의 마지막 인덱스를 불러온다. 즉, 해당 체인의 마지막 블록을 불러온다. 





## 06. step6

### PoW(작업 증명)이란?

![Proof of Work (PoW)](https://www.investopedia.com/thmb/pNxupnErsUbSdn1h2BWls_MssjE=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/proof-work_final-f69ec3198310425f9145b7cdfb6ee28e.png)

1. **채굴자들이 새로운 블록을 채굴하기 위해 찾아내야 하는 데이터 또는 숫자 **(즉, nonse값)
2. 채굴자들이 해결해야 하는 문제들을 정의해본다. 이 문제를 해결하면 특정 숫자를 찾게되는데, 이 숫자를 작업 증명이라고 한다. 이는 create_block 함수에 의해 예상되는 proof 가 된다. 
3. 작업 증명이란 찾기는 어렵지만, 증명은 쉬운 숫자이다. 



Additional URLs:

https://www.ledger.com/ko/academy/%EC%9E%91%EC%97%85-%EC%A6%9D%EB%AA%85%EC%9D%B4%EB%9E%80



### proof_of_work function 

```python
Class Blockchain:
    def proof_of_work(self, previous_proof):
        new_proof = 1
        check_proof = False
        while check_proof is False:
            hash_operation = hashlib.sha256(str(new_proof**2 - previous_proof**2).encode()).hexadigest()
            if hash_operation[:4] == '0000':
                check_proof = True
            else:
                new_proof += 1 
        return new_proof #nonse 반환
```

1. 풀어야 할 문제를 정의할 뿐 아니라, 해결하기까지 한다. 

2. 함수의 연산 끝에 나오는 작업 증명은 create_block에서 예상하는 proof가 된다. 

3. 인수 2개 

   1. self: 클래스로부터 생성될 인스턴스 객체에 proof_of_work function을 적용해야 하므로.
   2. previous_proof: 채굴자들이 해결할 문제를 생성하기 위해서 이전 증명을 고려해야 하기 때문. 즉, 이전 증명은 채굴자들이 새로운 증명을 찾기 위해 고려해야 할 문제의 한 요소.

4. `new_proof = 1` : 문제를 해결하기 위해 올바른 증명을 얻기까지 while문으로 1씩 증가시킬 예정. (nonse의 개념인듯..)

5. `check_proof = False` : 이 증명이 올바른 증명인지 확인한다. new_proof가 문제에 대한 해답이 아니므로 False로 설정.

6. while roop: 채굴자가 해결해야 하는 문제를 써본다. 

   해시 함수를 사용한다. SHA256 암호화 함수 + hexdigest 함수를 이용해 64자 문자열을 도출한다. 이 문자열은 4개의 leading zeros로 시작한다. 

   1. 해시 연산

   2. 해시 연산이 leading zeros 4개로 시작하는지 확인한다.

      - leading zeros: 채굴자들이 pow를 찾기 위해 문제를 정의하는 대표적인 방법.

      - leading zeros가 많을수록, 채굴자가 문제를 해결하기 어려워진다. 

6-1. 해시 연산

1. `hash_operation`: 64자 문자열(16진수 숫자만을 포함하는 이중 길이 문자열)

   - `new_proof`와 `previous_proof`를 모두 사용하는 연산으로 정의한다.
   - 연산은 비대칭으로 이루어져야 한다.
   - `new_proof + previous_proof ` == `previous_proof + new_proof `이기에, `new_proof`를 증가시키다보면 어느 시점에 `new_proof`이 곧 과거의 `previous_proof`가 된다. 블록을 채굴할 때, 두 블록마다 동일한 증명이 나오는 것을 보면 알 수 있다.(연산이 대칭이기 때문)
   - 따라서 연산을 `new_proof - previous_proof ` 로 하면 비대칭 연산이 된다. 
   - 여기서 약간의 복잡함을 부여하여 `new_proof**2 - previous_proof**2`

2. `encode()`: SHA256 함수에 적합한 형식으로 문자열을 포함시키는 함수. 콘솔을 확인하고, 문자열 전에 b를 추가시킨다. 

   ex) `new_proof**2 - previous_proof**2`= 5라면, 

   `str(new_proof**2 - previous_proof**2)`는 '5',

   `str(new_proof**2 - previous_proof**2).encode()`는 `b'5'`가 나온다.

3. `hexdigest()`: 16진수 숫자만을 포함하는 이중 크기 문자열을 생성한다. 

6-2. 해시 연산이 leading zeros 4개로 시작하는지 확인한다. 

1. `if hash_operation[:4] == '0000'` : 인덱스로 0, 1, 2, 3을 들고온다. 
2. `else:`: 특정 단계에서 신규 증명을 찾을 수 없는 경우. 값을 증가시키며 다시 증명을 찾아본다. 

 - new_proof를 +1 씩 하며 4개의 leading zeros가 '0000'이 되는 증명을 찾는다.





## 07. step7

마지막으로, 블록체인의 모든 것이 알맞게 구축되었는지 확인한다. 

모든 것이 알맞다면 2가지 필수적인 사항을 확인한다.(유효한 블록체인을 갖는지 확인한다.)

1. 블록체인의 각 블록이 leading zeros 4개로 시작하는 암호 해시를 반환하여 문제를 해결하는 작업 증명을 갖는지 확인한다.
2. 각 블록의 Prev.hash가 이전 블록의 hash와 같은지 확인한다.
   - 이 때는 해시 함수를 실행해서 확인해야 한다. 각 블록을 해싱하는 해시 함수를 따로 구축해서 좀 더 구조화된 코드를 가져야한다. 



### hash function

블록을 입력값으로 갖고, 해당 블록에 대한 SHA256 암호화 해시를 그 결과로 return한다. 

```python
Class Blockchain:
    def hash(self, block):
        encoded_block = json.dumps(block, sort_keys=true).encode()
        return hashlib.sha256(encoded_block).hexdigest()
        
```

1. 인수

   - self: 현재 구축하려는 블록체인 클래스의 메서드, 블록체인 채굴에서도 사용될 메서드
   - block: 블록체인의 모든 블록 

2. `encoded_block`
   - hashlib에서 SHA256 해시 함수가 사용될 수 있는 형식으로 블록을 인코딩하기 때문. 

   - block의 dictionary를 문자열로 변환한다.

   - Json의 `dumps(블록, sort_keys=true)`: 객체를 가져와 문자열을 생성한다. 
     - str() 대신 쓰는 이유: 암호화폐 모듈에서 block dictionary를 Json 형식으로 Json 파일에 저장하기 때문.
     - `sort_keys=true`: block, block dictionary를 키 별로 정렬할 수 있도록 만드는 인수
   - `encode()`: 문자열 앞에 b를 추가한다. 





## 08. step8

전체 블록체인이 유효한지 확인한다. 

1. 각 블록의 Prev.hash가 이전 블록의 해시값이 맞는지 확인한다. 
2. proof_of_work 함수로 정의한 작업 증명 문제에 따라 각 블록의 증명이 유효한지 확인한다. 



### is_chain_valid function 

```python
Class Blockchain:
    def is_chain_valid(self, chain):
        previous_block = chain[0]
        block_index = 1
        while block_index < len(chain): #모든 block을 다 확인하도록 설정한다.
          	#현재 블록을 불러온다
            block = chain[block_index]
            #1. 각 블록의 Prev.hash가 이전 블록의 해시값이 맞는지 확인한다. 
            if block['previous_hash'] != self.hash(previous_block):
                return False
            #2. 각 블록의 증명이 유효한지 확인한다. 
            previous_proof = previous_block['proof']
            proof = block['proof']
            hash_operation = hashlib.sha256(str(proof**2 - previous_proof**2).encode()).hexadigest()
            if hash_operation[:4] != '0000':
                return False
            #다음 블록을 위한 준비
            previous_block = block 
            block_index += 1
        return True
```

1. 인수

   - chain: 각 블록의 체인이 각 블록에 해당하는 것이 맞는지 확인한다. 

2. while 루프를 통해 모든 블록을 확인한다.

   - 변수는 block의 인덱스. 인덱스를 초기화하고, 이전 블록의 변수도 초기화한다.
   - Genesis Block인 이전 블록 변수를 해당 체인에 대한 인덱스 0으로 초기화한다. 
   - 다음 while루프가 끝날 때 해당 이전 블록 변수의 값을 신규 블록과 동일하도록 업데이트한다. 

3. `while block_index < len(chain)`: 모든 block을 다 확인하도록 설정한다.

4. 각 블록의 증명이 유효한지 확인하는 부분 

   즉, 문제가 해결된 경우, 해당 연산의 암호화 해시가 leading zeros 4개로 시작하는지 확인한다. 

   1. `previous_proof = previous_block['proof']` : 이전 증명을 가지고 온다.
   2. `proof = block['proof']` :  현재 블록의 증명 키를 가져와서 현재 증명을 불러온다.
   3. `hash_operation = hashlib.sha256(str(proof**2 - previous_proof**2).encode()).hexadigest()` : 이전 증명과 현재 증명을 통해 해시 연산을 한다.
   4. `if hash_operation[:4] != '0000'` : 해당 해시 연산이 4개의 leading zeros 로 시작하는지 확인한다. 
   5. `previous_block = block ` : 변수 재설정
   6. `block_index += 1` : 다음 블록으로 가도록 설정





## 09. step9

이번 시간부턴: 블록체인 체굴 클래스를 만들어본다. 

지난 시간까지: 실제 블록체인이자 상호작용할 클래스의 객체 생성 뿐만 아니라, Postman에서 Get 요청을 만들어 블록체인과의 상호 작용을 가능하게 만드는 Flask 기반의 웹 애플리케이션 생성의 준비도 완료됐다.



파트2에선 4가지를 한다.

1. Flask 클래스에 객체를 생성하여 Flask 기반의 웹 애플리케이션을 생성한다. 
2. 블록체인 클래스의 인스턴스 객체를 생성해서 실제 블록체인을 생성한다. 
3. 작업 증명의 문제를 해결해서 블록 채굴을 위한 첫번째 Get 요청을 만든다. 
4. 전체 체인을 얻기 위한 Get 요청을 만든다. 



### Flask 사용하기

참고) https://flask.palletsprojects.com/en/2.0.x/quickstart/

Flask를 사용할 때 1단계: 웹 애플리케이션 자체를 생성한다. (객체를 생성한다.)

````python
from flask import Flask

app = Flask(__name__)  #Flask 객체

# 블록 채굴이나, 전체 블록체인을 Postman에 나타나게 하는 요청의 예시도 확인 가능
@app.route("/")  #route(요청): mine block 요청 & Get요청을 만든다
def hello_world():
    return "<p>Hello, World!</p>"
````



### 소스

 ```python
# Part 2 - Mining our Blockchain
# Creating a Web App
app = Flask(__name__)

# Creating a Blockchain
blockchain = Blockchain()
 ```





## 10. step10

### Flask 사용하기 

1. Flask를 사용할 때 2단계: route 데코레이터로 Flask에 어떤 URL이 함수(mine_block function)를 작동시켜야 하는지 알려준다.	

   ```python
   from flask import Flask
   
   app = Flask(__name__) 
   
   @app.route("/")  #route(요청): mine block 요청 & Get요청을 만든다
   def hello_world():
       return "<p>Hello, World!</p>"
   ```

2. route 함수 안에 들어가는 URL은 전체 주소. 전체 주소는 QuickStart를 본다. 

   https://flask.palletsprojects.com/en/2.0.x/quickstart/

   ```bash
   $ export FLASK_APP=hello
   $ flask run
    * Running on http://127.0.0.1:5000/
   ```

3. 인수에 요청 메서드(Http method)를 추가한다.

   https://flask.palletsprojects.com/en/2.0.x/quickstart/#http-methods

   ```python
   from flask import request
   
   @app.route('/login', methods=['GET', 'POST'])
   def login():
       if request.method == 'POST':
           return do_the_login()
       else:
           return show_the_login_form()
   ```

   - Get: 뭔가를 얻을 수만 있다. 
   - Post: 뭔가를 생성할 수 있다. 
   - 모듈2에서 Json 파일로 트랜잭션을 생성할 때 Post 메서드를 사용한다. 
   - 여기서는 채굴을 하여 새 블록을 얻으므로 Get 메서드를 사용한다. 



### Mine_block function

```python
# Mining a Blockchain
@app.route("http://127.0.0.1:5000/mine_block", method = ['GET']) # 새 블록 채굴 요청을 보낸다.
def mine_block():
  	# 1.이전 증명을 얻는다.
    previous_block = blockchain.get_previous_block()
    previous_proof = previous_block['proof']
    # 2.작업 증명 해결
    proof = blockchain.proof_of_work(previous_proof)
    # 3.이전 해시를 가져온다.
    previous_hash = blockchain.hash(previous_block)
    # 4.블록을 만든다.
    block = blockchain.create_block(proof, previous_hash)
    response = {'message' : 'Congratulations, you just mined a block!'
               ,'index' : block['index']
               ,'timestamp' : block['timestamp']
               ,'proof' : block['proof']
               ,'previous_hash' : block['previous_hash']}
    return jsonify(response), 200
```

1. 이전 증명을 기반으로 증명을 찾아서 작업 증명 문제를 해결한다.(마지막 블록의 마지막 증명) 

   &rightarrow; 증명을 얻는다면 성공적인 채굴을 의미한다.

   &rightarrow; 증명을 얻으면 필요한 다른 키(블록 생성에 필요한 키)도 얻게 된다(index, timestamp, proof, previous_hash)

   1. 작업 증명을 얻기 위해서 proof_of_work 함수를 사용하면 되지만, 이는 previous_proof를 적용해야 하므로 이전 증명이 필요하다. 
   2. 이전 증명을 얻기 위해 이전 블록을 가져온다.(get_previous_block)
   3. 이전 증명을 얻는다.(`previous_block['proof']`)

2. 블록을 생성한다. 

   1. `create_block(증명, 이전 해시)`를 사용한다. 이를 위해 이전 해시를 얻어야 한다. 
   2. 블록을 해싱하는 해시 메서드를 사용한다.(`hash(블록)`&rightarrow;`hash(previous_block)`)
   3. 블록을 생성한다. (`create_block(proof, previous_hash)`)

3. get 요청의 응답으로 데모를 실행할 때 Postman에 표시한다. 

   블록의 모든 정보뿐만 아니라 채굴자에게 보내는 블록 채굴 메세지인 응답 변수를 삽입한다.

   1. Postman에서 Json 형식으로 표시한다. 따라서 dictionary를 이용한다. 
   2. `Jsonify()`: 응답을 Json 형식으로 반환한다.

   2-1. HTTP state code도 함께 반환한다. 

   ​		https://en.wikipedia.org/wiki/List_of_HTTP_status_codes

   ![HTTP status codes: Full List of HTTP Response Status Codes](https://www.infidigit.com/wp-content/uploads/2019/12/20191227_012601_0000.png)

   





## 11. step11

지난 시간: 새 블록 채굴을 위한 첫 번째 Get 요청을 생성했다. 

이번 시간: 전체 블록체인을 얻기 위한 두 번째 Get 요청을 만든다. 



```python
# Getting the full Blockchain
@app.route("http://127.0.0.1:5000/get_chain", method = ['GET'])
def get_chain():
    response = {'chain': blockchain.chain
               ,'length': len(blockchain.chain)}
    return jsonify(response), 200
```

1. get 요청을 보낼 때 표시되는 response를 만든다. 

   - `Jsonify()`: 전체 블록체인을 포함하여 Json 형식으로 변환한다. 

   1. 체인. 블록체인 객체에 있는 체인 리스트[] 를 넣는다. 

      &rightarrow; `__init__ `에서 체인 리스트는 빈 리스트로 초기화되나, `mine_block` 으로 채굴한 블록의 체인은 모든 키로 가득찼다.

   2. 체인의 길이. `len()` 함수를 이용한다. 





## 12. step 12

이번 시간: 데모를 진행한다. Flask를 이용해 앱을 실행하고, Postman으로 요청한다. 





### 소스 

```python
	
```

1. 앱을 실행한다. 

   - `app.run()`: host, port - 2개의 인수가 필요하다. 

   - https://flask.palletsprojects.com/en/2.0.x/quickstart/ 에서 살펴보면, 

     네트워크의 사용자를 신뢰할 경우 호스트를 0.0.0.0 으로 추가하여 서버를 공개적으로 사용할 수 있다. 

   ```text
   Externally Visible Server
   
   If you run the server you will notice that the server is only accessible from your own computer, not from any other in the network. This is the default because in debugging mode a user of the application can execute arbitrary Python code on your computer.
   
   If you have the debugger disabled or trust the users on your network, you can make the server publicly available simply by adding --host=0.0.0.0 to the command line:
   
   $ flask run --host=0.0.0.0
   This tells your operating system to listen on all public IPs.
   ```

   - quickstart에 나온 `* Running on http://127.0.0.1:5000/` 에 따라 port는 5000 을 사용한다. 

2. 실행하기 전, 전체 소스를 선택하고 파일 탐색 창에서 알맞은 폴더로 이동한다. 

   작업 폴더에서 코드를 실행시키는 것이 권장 사항이다!

   ![Screen Shot 2023-01-13 at 10.52.03 AM](/Users/salient/Desktop/untitled folder/Screen Shot 2023-01-13 at 10.52.03 AM.png)





### 1. get_chain을 요청 

전체 코드를 실행했을 때 제네시스 블록이 잘 생성되었는지(proof = 1, prev_hash = 0 인지) 확인한다.









### 2. mine_block을 통한 채굴 









