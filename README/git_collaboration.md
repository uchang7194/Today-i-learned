## git collaboration

1. 콜라보 초대

- 초대하는 사람: repository -> settings -> collaborator -> user name / full name / email address -> 초대
- 초대받을 사람: email(git에 가입되어 있는) -> view invitation 클릭 -> 참여 

2. 여러사람이 merge를 할 수 있지만 프로젝트의 내용이 바뀌거나 없어질 위험성이 큼.

3. 콜라보 과정 중 conflict가 일어날 경우
```
[A, B 브랜치가 같은 파일을 수정할 경우]
(중복되지 않는 파일을 수정해서 올릴 경우에는 conflict가 날 일이 없음.)

                     ┏━━━━[A]━>━>━>━[A]   
                     ┃        ┏━━━━━━┛         (수정)  
Local ━━━━━━━━━━[  dev  ]━━━━━━━━━━━━━━━━━━━━━[dev+A+B]━━━━━━━━━━━━━━━━━━━━ 
                 ▲ ┃ ┃        ┃                  ▲  ┃
    ┏━━━━━━━━━━━━┛ ┃ ┃        ┃                  ┃  ┃  
   (1)     ┏━━━━━━━┛ ┃        ┃                  ┃  ┃
    ┃      ┃         ┗━━━━[B]━>━>━[B]            ┃  ┃
[master]   ┃                  ┃    ┗━━━━━━━━┓   (5) ┗━━━━━━━(6)━━━━━━━┓
          (2)                (3)           (4)   ┃                    ┃          
           ┃                  ┃             ┃    ┃                    ┃  
           ▼                  ▼             ▼    ▼                    ▼      
Remote ━━[dev]━━━━━━━━━━━━━[dev+A]━━━━━━[  dev+A+B  ]━━━━━━━━━━━━[  dev+A+B  ]
                                         (conflict)                 (MERGE)
```
- (1): local의 master branch에서 dev branch를 생성
- (2): local의 dev branch를 remote에 push
- (3): dev의 A브랜치를 생성하고 커밋(3번) 후 remote의 dev브랜치에 merge
- (4): dev의 B브랜치를 생성하고 커밋(2번) 후 remote의 dev브랜치에 merge(`conflict`)
- (5): `conflict`를 해결하기 위해 local의 dev브랜치에 remote의 dev브랜치를 pull하고 `conflict`가 난 부분을 수정
- (6): local의 dev의 수정된 부분을 remote의 dev에 push하면 merge가 됨.