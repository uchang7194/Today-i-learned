#Aria
 ### tabindex 
 > 강제로 탭 focus를 받거나 받지 않게끔 해준다.
 - 주로 시각적인 디자인 때문에 폼 요소나 링크 요소가 논리적이지 않게 만들어야 하는 경우 사용한다.

 ### tablist [role] 
 > tablist 라는 역할을 부여한다.
 ```html
 <ul class="tablist" role="tablist">
 <!--
  .
  .
  .
 -->
 </ul>
 ```
 ### tab [role] 
 > 탭 패널의 제목을 포함하고, 활성화 될 때 탭 패널을 활성화한다.
 ```html
 <ul class="tablist" role="tablist">
    <li id="tab1" class="tab" role="tab" ...> Princes</li>
    <li id="tab1" class="tab" role="tab" ...> Features</li>
 </ul>
 ```
 ### tabpanel [role]
 > 탭의 관련 내용을 포함한다.
 ```html
 <div id = "panel1" class = "pannel" role = "tabpanel">
    <h3> 가격 </h3> 
    가격 목록
 </div> 
 ```
 ### aria-controls
 > 현재 요소에 의해 제어되는 요소 목록을 설정하거나 검색한다.<br>
 ID와 매칭시켜야 한다.
 ```html
 <ul class="tablist" role="tablist">         
    <li id="tab1" class="tab" aria-controls="panel1" role="tab" ...>Prices</li>         
    <li id="tab2" class="tab" aria-controls="panel2" role="tab" ..>Features </li>         
 </ul>      
    
 <div id="panel1" class="panel" aria-labelledby="tab1" role="tabpanel" ..>       
    <h3 ..>Prices</h3>                   
    List of prices      
 </div> 

 <div id="panel2" class="panel" aria-labelledby="tab2" role="tabpanel" ..>        
    <h3 ..>Features</h3>      
    List of product features....          
 </div>  
 ```