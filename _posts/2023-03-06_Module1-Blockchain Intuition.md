---
layout: single 
title: "Module1 - Blockchain Intuition"
categories: 블로그
tags: [blockchain]
toc: true
toc_sticky: true
toc_label: 목차
---


# Helpful URLs

1. Additional Resources 

https://www.superdatascience.com/pages/blockchain

2. Some Podcasts 

https://www.superdatascience.com/podcast/podcast-rise-of-blockchain

3. Mango QnA bot 

https://www.superdatascience.com/pages/welcome-to-faqbot



# Welcome to Blockchain! 

1. 블록체인을 직관적으로 확실히 이해하기 
2. 일반적인 블록체인을 밑바닥부터 만드는 법 배우기 



# Module1 - Blockchain Intuition

### 00. Plan of Attack 

- 관련 기술과 비교했을 때, 블록체인은 그렇게 복잡하지 않음 
- 매우 다양한 구성요소가 있어 복잡해보임
- 블록체인의 구성 요소를 올바른 차례로 줄세우는 게 중요함! 





### 01. What is Blockchain?

1. History

   - Stuart Haber & W.Scott Stornetta: "How to time-stamp a digital document"(1991) 
   - Satoshi Nakamoto

2. Wikipedia

   - A blockchain is a continuously growing list of records, called blocks, which are linked and secured using cryptography. 

3. 블록의 구성요소

   - Data 
   - Prev.Hash 
   - Hash (블록(데이터)의 지문과도 같음)

4. 정리 

   ![What Is Blockchain | Money](https://img.money.com/2022/06/What-Is-Blockchain-Infographic.jpg)

   - 블록체인: 해시값들을 통해 블록들이 암호화 링크로 연결되어 있음

   - Genesis Block(제네시스 블록): 블록체인에서의 첫 번째 블록 
     - 블록체인이 초기화된 후, 이 블록이 언제나 첫 번째이기 때문에 절대적으로 이 블록만이 첫 번째 블록 (불변)
   - 데이터에 변화가 있으면, 해시값도 변함 
   - 1, 2, 3 중 어떤 블록이라도 조작시: 해시는 변하고, 체인은 유효하지 않게 됨

5. 관련된 용어들 

   - Hash Cryptography (해시 암호화)
   - Immutable Ledger (불변의 서류)
   - Distributed P2P Network (분산 P2P 네트워크)
   - Mining (채굴)
   - Consensus Protocol (합의 프로토콜)





### 02. Understanding SHA256 HASH 

1. SHA256 Hash 사용 개요
   - 각 사람마다 고유의 지문이 있듯이, 각 디지털 문서에 어떤 종류의 지문을 만들어 각 서류를 식별할 수 있게 한다.
   - (6천만분의 1의 확률로 같은 지문을 가질 가능성..)
   - 미국국가안보국(NSA)에서 개발됨 
   - 세계적으로 어플리케이션 비밀번호 저장, 디지털 문서 검사, 블록체인 등에서 사용됨 
   - 알고리즘 코드가 공유되어 있음

2. SHA256 Hash 란?
   - SHA: `Secure Hash Algorithm`(안전한 해시 알고리즘)의 약자
   - 256: 메모리를 차지하는 비트 수 
   - 해시의 길이는 언제나 64자이며, 숫자와 문자 모두 올 수 있음 (16진법)
   - 해시의 문자는 각각 4비트를 차지하므로, 총 64*4(256) 비트를 차지함
   - 어떤 디지털 자료(텍스트, 오디오, 실행파일, 비디오, 운영체제 등)에도 사용 가능
   - SHA516, SHA3 등 다른 해시 알고리즘들도 존재한다. 만들기도 가능! 

3. 어떻게 작동하는가?
   - https://tools.superdatascience.com/blockchain/hash/
   - 같은 데이터를 입력하면 언제나 같은 해시값을 얻는다. 마치 같은 사람의 지문을 확인할 때마다 지문이 같듯이.. 
   - 쇄도 효과: 작은 symbol 하나만 변경해도 해시값이 바뀜
4. 해시 알고리즘의 특징 
   1) 단방향이어야 한다. 
      - 뒤로 갈 수 없음 (해시에서 문서로 갈 수 없음. 지문을 가졌다고 사람으로 복원 불가.)
   2) 결정적이어야 한다. 
      - 동일한 문서는 동일한 해시값을 가진다. 
   3) 연산이 빨라야 한다. 
   4) 쇄도 효과 (**Avalanche Effect**)
      - 동일한 문서에 아주 작은 변병을 가했을 때(1비트의 변화라도 있으면) 해시값은 완전히 변한다. 
      - 알고리즘 소스 상 하나의 변화가 몇 가지의 변화를 유발하여 더 많은 변화를 유발함(눈사태와 같음)
   5) 충돌 저항성 
      - 디지털 데이터의 양은 무한하고, 해시값은 유한하다. 
      - 아주 드물게 같은 해시값을 가질 수 있으나, 아무런 영향은 없을 것이다. 
      - 알고리즘이 인위적인 충돌에 저항할 수 있어야 한다(서로 다른 문서를 같은 해시값을 갖게 하는(인위적인 충돌) 조작이 있을 수 있음)





### 03. Immutable Ledger 

1. 부동산을 통한 예시

   집을 사고 싶다면.. 

   - 은행에 있는 돈으로 집을 산다
   - 정확히는 "부동산 권리 증서"를 산다 
   - 집을 산 후 국가 등에 등록하여 '내 소유' 임을 증명한다

2. Traditional Ledger 

   - 디지털 서류의 시대지만, 제 3 국가 등에서는 아직 종이 서류를 이용한다. 
   - 예시) 집 문서를 누군가가 훼손한다면, 더 이상 내 집이 아니게 된다.. 

3. 소유권을 블록체인에 저장했다면.. 

   - 집을 팔거나 살 때마다 새 블록이 추가된다.

   - 이 중에서 하나의 블록을 의도적으로 변경한다면.. 
     - 해시값이 변경되고(암호화 링크가 더이상 작동하지 않는다)
     - 그 뒤로 이어지는 모든 블록은 유효하지 않게 된다. 
     - 이어지는 모든 전체 항목을 수정해야 한다. 

   - 따라서 블록체인으로 저장되면 어려워진다. 
   - 모든 서류들은 블록체인에 적용할 수 있다.



Additional Reading: 

http://medium.com/@cryptoeconomics/the-blockchain-economy-a-beginners-guide-to-institutional-cryptoeconomics-64bf2f2beec4





### 04. Distributed P2P Network 

1. 수많은 컴퓨터들이 상호 연결 되어있고, 블록체인은 모든 컴퓨터로 복사된다.(네트워크를 통해서 모든 컴퓨터들이 상호 연결된다.)
2. 네트워크를 통해 끊임없이 동기화된다.  
3. 중간의 블록이 인위적으로 수정되더라도, 상호 연결된 컴퓨터들이 가진 블록체인들과의 비교로 인해 기존 값으로 복구된다. 



Additional Reading:

https://medium.com/@VitalikButerin/the-meaning-of-decentralization-a0c92b76a274





### 05. How Mining works: The Nonce 

1. 블록 예시

| Block: #3                                                    |
| ------------------------------------------------------------ |
| **Nonce:** 23                                                |
| **Data:**<br />Kirill -> Hadelin 500 hadcoins<br />Kirill -> Ebay 100 hadcoins<br />Hadelin -> Joe 70 hadcoins |
| **Prev.Hash:** 0000DF2E57FB432A                              |
| **Hash:** 82B5C4156AE315F7                                   |

- 한 블록 안에 단일 트랜잭션이 아닌, 다중 트랜잭션을 저장할 수 있음

- Prev.Hash: 블록 간 암호화 링크를 활성화시키는 방식 
- Hash: 블록 번호, Nonce, 데이터, 이전 해시를 해싱 알고리즘에 넣어 도출된 해시

- Nonce: (Number that use only once) 채굴에서 가장 중요한 영역 

2. How Mining Works?(1)
   - 채굴: nonce 필드를 바꾸는 작업을 수행하는 것 
   - nonce를 변경해서 해시값을 조정할 수 있다. (Block Num, Data, Prev Hash 등은 변경할 수 없기에.. Data는 변조를 방지해야해서 안 됨(블록체인의 의의에서 벗어남))
   - nonce 값은 자유롭게 변경할 수 있기에, 해시값을 변경할 수 있음 

3. 가능한 모든 해시들을 줄 세워놓고, 해당 맵에 해시들을 예측하면 아래와 같다.

![Screen Shot 2023-01-02 at 4.48.45 PM](/Users/salient/Desktop/untitled folder/Screen Shot 2023-01-02 at 4.48.45 PM.png)

4. 채굴 방법 

   - 블록체인 시스템이나 알고리즘이 대상을 설정하는 것 (채굴자들이 특정한 해시를 달성하도록 설정한 대상이 존재함)

     ![Screen Shot 2023-01-02 at 4.55.10 PM](/Users/salient/Desktop/untitled folder/Screen Shot 2023-01-02 at 4.55.10 PM.png)이 때, target보다 값이 큰 해시는 고려 대상이 아님. 즉, 블록에 대해 찾은 해시가 target보다 더 작을 때에만 해당 사항이다. 

   - 즉, 예시 그림에선 맨 아래 있는 해시만이 블록을 생성할 수 있음 

   - 블록을 만들 수 있는 해시를 발견했으면 채굴자가 된다. 

   - Tip: Express Target with leading Zeros (ex.'0000')

     - 맵에서 더 아래로 내려갈수록 0이 많아지므로, leading Zeros를 생각하여 해시를 도출한다. 

   - Golden Nonce에 진입하기![Golden Nonce!](/Users/salient/Desktop/untitled folder/Screen Shot 2023-01-02 at 5.05.49 PM.png)

     - 채굴자가 하는 일: nonce를 변경하여 대상 아래에 포함될 수 있는 해시(Golden Nonce에 해당하는 해시)를 지속적으로 찾는다.
     - 찾고 난 후: 블록체인에 블록을 추가할 수 있게 되고, 보상을 받게 된다. 

   - Nonce에 대해 어떤 해시값을 얻게될지 모른다. (순서가 있지 않고 무작위임)

5. 결론: 채굴이란, target hash 아래에 있는 해시를 구할 때까지 nonce를 지속적으로 변경하는 것. 이를 찾는 사람이 블록을 하나 추가하고, 그 다음 블록을 찾기 위해 같은 작업을 반복한다.





### 07. Byzantine Fault Tolerance 

1. 비잔틴 내결함성
   - 전달된 정보에 대한 다수결의 알고리즘으로, 장군들은 전달된 정보에 기반해 의사결정을 내린다.
   - 최대한 내결함성을 높여야 한다.  
2. 블록체인이나 탈중앙화된 시스템에서의 적용
   - 시스템을 공격하려는 사람이 있을 경우, 이 장군들이 고안해낸 알고리즘과 같이 합의 프로토콜을 만들어야 한다. 
   - ex) 비행기 구성 요소(한 개나 두 개의 결함으로 전체 비행기가 추락하면 안 된다.), 핵발전소, 로켓 등.. 
3. 합의 프로토콜과 연관된다. 



Additional Reading:

1. The Byzantine Generals Problem

​	-Leslie Lamport, Robert Shostak, Marchall Pease (1982)

2. https://medium.com/loom-network/understanding-blockchain-fundamentals-part-1-byzantine-fault-tolerance-245f46fe8419





### 08. Consensus Protocol: Defense Against Attackers

1. 블록체인을 위한 합의 프로토콜로 2가지 문제를 해결해야 한다.

   1. 공격자(Attackers)로부터 네트워크를 보호해야 함

      - 체인의 중간 어딘가를 공격하는 경우(x)

        : 각 단일 노드에서 모든 블록을 변경해야 하기 때문에 불가능함

      - 체인의 끝에 고의적으로 새로운 블록을 추가하려고 하는 경우(o)

   2. 블록체인의 경쟁 체인 문제를 해결해야 함

      - 대형 블록체인의 경우, 전 세계적으로 분산되어 있어 특히 서로 멀리 떨어진 노드 사이에 지연 발생 가능. 또한 서로 멀리 떨어진 두 노드가 동시에 채굴에 성공할 수도 있음. 
      - 채굴에 성공하더라도, 그 정보가 멀리 있는 곳까지 도달하는 속도보다 멀리 있는 곳에서 채굴하는 속도가 빠른 경우. 

2. Consensus Protocols 방법들 

   ![Consensus Algorithm Blockchain: An Important Factor For The Project Success  - Global Blockchain and Software Development | SotaTek](https://www.sotatek.com/wp-content/uploads/2022/04/A-brief-comparision-between-2-types-of-consensus-algorithm-blockchain.jpg)

   1. Proof of Work(Pow): 작업 증명
      - Satoshi Nakamoto가 논문에서 처음으로 제안한 것
      - 비트코인, 이더리움 (지분 증명으로 이전할 계획은 있음..)
   2. Proof of Stake (PoS): 지분 증명 
   3. Others..

3. Proof of Work(Pow): 작업 증명 개요 

   1. 전체 채굴 상황이 종료된 경우 
      - 채굴자는 golden nonce에 도달하기 위해 수백만, 수십억번을 반복한다. 시간이 오래 걸린다. 채굴 장비, 전기료 등에 많은 투자를 해야 함. 
      - 찾은 해시는 `작업 증명`. 즉, 암호화 문제를 해결하기 위해 이 모든 작업을 수행했다는 증명. 
   2. 채굴자가 새로운 블록을 추가한 경우 
      - 네트워크나 블록체인이 채굴에 대해 코인으로 보상한다. 
      - 해당 블록에 포함된 트랜잭션에 관한 수수료를 받는다(금전적인 인센티브: 공정하게 채굴하도록 장려.)
        - 채굴자는 기각된 블록을 추가하거나, 암호화 퍼즐을 풀어 올바른 해시를 찾아서 추가한다. 
        - 악의적으로 트랜잭션을 추가한다면 보상을 받을 수 없다. (네트워크는 블록이 추가되고 네트워크로 전파되기 전에 각 단일 노드에서 엄격하게 확인한다.)
        - Cryptographic puzzles(암호화 퍼즐): Hard to solve, Easy to verify(채굴과 입증은 다르다!)





### 09. Consensus Protocol: Proof of Work(PoW)

만약 채굴자 2명이 거의 동시에 한 블록을 채굴한다면.. 

![Screen Shot 2023-01-04 at 5.44.16 PM](/Users/salient/Desktop/untitled folder/Screen Shot 2023-01-04 at 5.44.16 PM.png)

1. 모두 악의가 없는 정상 블록이라는 가정하에, 노란색 블록이 네트워크를 통해 더 빨리 전파된다.

2. 충돌 메세지가 전달되는 경우, 비잔틴 내결함성이 필요하다.(합의 프로토콜) 

   - 블록체인의 합의 프로토콜이란? 50%~51% 이상의 해싱 파워를 가진 체인이 이기는 것. 

3. 블록체인의 노드가 하는 일: 

   1. 경쟁 체인이 있는 경우(지금 상황에선, 노란색과 보라색 체인) 다른 블록이 추가될 때까지 기다린다. 

      - 블록이 추가되면, 어떤 체인이 더 긴지 알 수 있음.

   2. 블록을 먼저 추가한 체인이 이긴다. 

      - 가장 긴 체인이 왕. 블록이 가장 많은 체인이 이기고, 다른 체인을 교체한다. 

      - 즉, 가장 높은 해싱 파워를 가진 네트워크에서 가장 긴 체인을 생성한다. 

        - 해싱파워: 1초당 각각의 컴퓨터에서 얼마나 많은 해시를 확인할 수 있는지를 모두 합한 것  

        - ex) 이 경우, 각각의 컴퓨터가 동일한 해싱파워를 가졌다고 가정하면, 노란색 부분이 보라색 부분보다 2배 많은 해싱 파워를 가짐. 

          즉, 다음 블록을 찾을 확률이 2배 더 높음. 

4. 충돌 해결

   ![Screen Shot 2023-01-04 at 5.53.05 PM](/Users/salient/Desktop/Screen Shot 2023-01-04 at 5.53.05 PM.png)

   - Orphaned Block (고아 블록): 보라색 블록
     - 채굴에 대해 보상하지 않음(트랜잭션도 유효하지 않음)



Additional Reading:

https://www.mail-archive.com/cryptography@metzdowd.com/msg09997.html

(Satoshi Nakamoto -> Hal Finney, Charles Jackson, Ray Dillinger, James Donald)





### 10. Blockchain Demo

1. 블록 만들기
   - https://tools.superdatascience.com/blockchain/block  
2. 블록체인 만들기
   - https://tools.superdatascience.com/blockchain/blockchain 
   - 원래의 블록체인에선, 내용이 바뀌면 해시가 바뀌고 뒤따르는 Prev.hash 값이 유효하지 않게 된다.
   - 이 시스템에선, 알아서 Prev.hash 값을 이전 해시값으로 변환해준다. (오해하지 말 것!)

3. Distributed Blockchain
   - https://tools.superdatascience.com/blockchain/distributed
   - Distributed P2P Network 를 확인할 수 있다. 
   - 분산되어 있으면, 악의적으로 수정(공격)하기에 어려워진다. 모든 블록을 동시에 공격해야 하기 때문.
4. Tokens (How blockchain works as money)
   - https://tools.superdatascience.com/blockchain/tokens
   - 3과 내용은 같으며, 트랜잭션이 추가됨. 

5. Coinbase (Where actual money originate)
   - https://tools.superdatascience.com/blockchain/coinbase
   - 비트코인에서 블록을 채굴하면 코인 베이스가 된다. 
   - Coinbase: 채굴자가 얻은 금액이 표시됨 
   - 돈이 실제로 시스템에 투입되게 함 
