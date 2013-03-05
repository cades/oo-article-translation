[原文出處](http://c2.com/doc/oopsla89/paper.html)

# 物件導向思考的實習課

_Kent Beck, Apple Computer, Inc._  
_Ward Cunningham, Wyatt Software Services, Inc._  
  
_From the OOPSLA'89 Conference Proceedings_    
_October 1-6, 1989, New Orleans, Louisiana_  
_And the special issue of SIGPLAN Notices_  
_Volume 24, Number 10, October 1989_  
  
### 內容
1. 問題
2. 觀點
3. CRC卡
4. 經驗
5. 結論
6. 參考資料
7. 附錄

### 簡介
要向程序式(procedural)編程的程式設計師新手和老手推廣「對物件導向設計，擬人化的觀點是不可或缺的」是很困難的。我們引入CRC卡，它把物件用「類別名、責任與合作對象」的特徵描述，做為一個讓學習者直接體驗物件的方法。我們發現這樣的學習法成功地教導初學設計師物件的概念，以及把複雜的現存設計推廣給老手設計師。

### 1. 問題
教OOP最難的，是讓學習者放棄控制的（在程序式編程是可能的）全域資訊，轉而依靠物件的局部資訊來完成他們的任務。新手設計師被朝向全域思考的退化弄亂：不用錢的全物變數、不必要的指標，以及不恰當的倚賴其它物件的實作。  
  
因為學習物件需要在整個研究方法上轉移，教物件遂簡化成教物件的設計。We focus on design whether we are teaching basic concepts to novices or the subtleties of a complicated design to experienced object programmers.  
  
與其把物件設計教得盡可能像程序式設計，我們發現最有效的「思考物件的慣用法」教學法，就像把學習者浸泡在物件的世界中一樣。為了達到這個目標，我們必須盡可能地丟掉常見的材料，expecting that details such as syntax and programming environment operation will be picked up quickly enough once the fundamentals have been thoroughly understood.  
  
It is in this context that we will describe our perspective on object design, its concrete manifestation, CRC (for Class, Responsibility, and Collaboration) cards, and our experience using these cards to teach both the fundamentals and subtleties of thinking with objects.  
  
### 2. 觀點
不管是什麼樣的語言實作或作業環境，程序式設計可以看做是「有程序，資料流和資料儲存[[1]](#ref1)」的抽象層級。我們希望為物件設計想出一個類似的一組基本原則。我們在三個維度上定了下來，它們分辨出物件在設計中的角色：類別名、責任，以及合作對象。  
  
物件的類別名創造了一個討論設計用的語彙。事實上，許多人都注意到物件設計和語言設計比起程序設計有更多共通點。我們敦促學習者（我們在設計時也花費可觀的時間）去找到對的一組字彙來描述我們的物件，一組在更大的設計環境中能達成內部一致且evocative的字彙。  
  
責任辨識出要解決的問題。解答存在許多版本與精鍊中。一項責任被當做討論可能解答的「握把」。物件的責任被表達成少量的動詞片語，每一個都包含一個主動動詞。這些片語能表達的越多，設計就越有力越精確。再強調一次，找出對的字彙的時間開銷，對設計是很有價值的。  
  
物件設計區別性的特徵之一，就是沒有物件是個孤島。所有物件都與其他物件保持關係，不論是提供自己依賴的服務的，或是被自己控制的。我們用來描述物件的最後一個維度是該物件的合作對象。We name as collaborators objects which will send or be sent messages in the course of satisfying responsibilities. 合作不必要是對稱的關係。以 Smalltalk-80[[2]](#ref2)為例，View和Controller operate as near equals （見下例）；而OrderedCollection用對它的客戶的一點關心甚至是了解提供服務。  
  
在這份論文中我們謹慎地模糊了類別和實體物件之間的區別。因為我們把命名實體物件的方法換掉帶來的穩固結構，使得這樣的不正式性並不像它看起來的令人困惑。This also makes our method for teaching independent of whether a class or prototype-based language is used.  
  
### 3. CRC卡
第二位作者(Ward Cunningham)發明了CRC卡以回應把合作設計抉擇文件化的需求。The cards started as a HyperCard [[3]](#ref3) stack which provided automatic indexing to collaborators, but were moved to their current form to address problems of portability and system independence.  
  
就像我們在把物件的合作文件化時的早期工作[[4]](#ref4)，CRC卡同時明確地表示多個物件。然而，與其僅僅追蹤在發送訊息(message sending)的形式上的合作細節，CRC卡藉由把（潛在的）許多訊息用英文片語表示出來，把設計師的注意力集中在合作的動機之上。  
  
![](http://c2.com/doc/oopsla89/fig1.gif)  
_圖一：一張「類別－責任－合作對象(CRC)」索引卡_
  
在使用它們時，一個物件的一切資訊都寫在一張4英吋乘以6英吋的索引卡上（譯註：等於10.16公分 x 15.24公分, 恰恰是一張明信片的大小）。這種卡片的優點是它很便宜、方便攜帶、容易取得且常見。圖一是一張理想的卡片。類別名稱帶著下劃線放在左上角；其下是責任列表，占卡片左邊的三分之二；而合作對象列表放在右邊的三分之一。

![](http://c2.com/doc/oopsla89/fig2.gif)   
_圖二：CRC卡描述Smalltalk的Model, View和Controller的責任與合作對象。_

圖二秀出一個從Smalltalk-80借來的例子，那個被誤解甚深的model-view-controller使用者介面框架。我們謹慎地只秀出一部分的責任each of these objects assumes for clarity of exposition. 注意到View和Controller的卡片重疊（暗示密切合作），而且放在Model的上方（暗示監督）。我們發現這些以及其他非正式的分群有益於理解設計。例如部分通常放在全體的下方。又，一個個抽象的精鍊可以被收集起來集中成一疊，其中最抽象的卡片放在最上面，代表其餘的卡片。  
  
當一個設計是不完全或者被理解得很糟的時候，能夠快速組織和在物理空間中定位索引卡的能力被證明是很有價值的。我們已經看過設計師一再地refer to a card they intended to write by pointing to where they will put it when completed.  
  
用這些卡片來設計傾向由已知發展到未知，as opposed to top-down or bottom up. 我們已經觀察兩個團隊經由幾乎是相反的順序，一個從驅動程式開始，另一個從高階模型開始，抵達本質上一樣的設計。該問題要求特定一組能力，是兩個團隊在實現該需求的設計時所發現的。  
  
我們建議將設計在執行腳本（execution scenarios）的幫助下駛向完成。我們從僅僅一或兩張明顯的卡片開始，並開始玩「假如」。如果狀況要求一個責任，而這個責任並未被任一個手邊的物件涵蓋時，我們要不就把責任添加到這些物件的其中之一身上，要不就創造一個新的物件來為承擔此負責。如果某一個物件在這過程中變得太雜亂，我們把這張卡片上的資訊複製到一張新的卡片上，尋找更精確有利的方式去描述這些物件在做什麼。如果無法再進一步濃縮資訊，而物件確仍然太複雜，我們建立新物件來假定這些責任中的部分。  
  
我們鼓勵學習者拿起那張他們在執行一個劇本時正在假定角色的卡片。看見一個設計者在描述物件間的合作時，把卡片拿在手裡一邊揮動著它一邊對物件產生強烈認同感，這樣的場景並不罕見。  
  
我們強調創造「符合當下需求而非架空的未來需求」的物件的重要性。這保證設計只含有與設計師直接經驗的一樣多的資訊，並避免過早的複雜性。在團隊中工作在這裡起了幫忙的作用，因為一個擔心的設計師可以藉由提出明確瞄準他懷疑的弱點和遺漏之處的腳本，來影響團隊成員。  
  
### 4. 經驗
我們曾用過CRC卡的情境之一是一門名為「用物件思考」的三小時課程。該課程是設計給有程式設計經驗的電腦專家，但他們的工作不需涉及每天的程式設計。這門課從介紹一個資料流的例子（一間有著教學與管理流程的學校）開始，接著重寫成帶責任與和作者的物件（例如老師、管理員和校長）。課堂隨即兩兩分組然後花一小時設計一個自動銀行業務機裡的物件。選擇這個練習是因為每個人都很熟悉這個應用，而且它已經分解成各種物件來控制裝置、與中央銀行的資料庫溝通、以及控制使用者介面。（附錄有範例解。）該練習之後接著定義用語「類別」、「實體」、「方法」和「訊息」，然後課堂以簡短討論不同物件導向語言的歷史與特色作結。  
  
在這門課教過百餘位學生，我們沒有遇過誰是無法獨自完成練習的，雖然課堂上的一組通常需要一些提示來起步。雖然我們沒有做更進一步的研究，該課程在公司裡被認為是有價值的資源，而且仍然報名踴躍，排到開課一年後。  
  
我們也請技術純熟的物件程式設計師試用CRC卡。我們的個人經驗建議給卡片在軟體工程中一個角色，雖然我們還無法要求一個完整的方法論（有其他人[[5]](#ref5)[[6]](#ref6)有發展得更完整可以利用CRC方法的方法論）我們知道有個例子，完成的卡片被交付給客戶當做（部分的）設計文件。雖然該產出卡片的團隊對設計十分高興，收到卡片的人在情境之外並不能理解卡片的意義。  
  
另一個實驗描繪了由用手觸摸和討論卡片建立起的情境的重要性。我們曾錄影記錄富經驗的設計師解決類似銀行機器的問題。我們的攝影機擺放讓卡片與設計師的手可見，但看不到卡片上的筆跡。影片的觀眾在跟上開發上沒有困難，雸且常常要求影帶暫停來讓他們可以表達意見。當觀眾的解釋需要它指著暫停的螢幕畫面上一張模模糊糊的卡片，就是生效的瞬間(the most telling moments)。  
  
最後，我們曾把CRC卡用在解釋複雜的設計上。幾分鐘的介紹足以讓觀眾準備好來聽一場用卡片呈現的報告。卡片可以事先做好或者當場寫。後者讓一個設計中的複雜性慢慢地揭露，一個與 Dave Thomas' 相關的程序「謊言管理」。卡片被當做輔助說這個計算故事的小道具。卡片讓他的演說可以不必依靠程式語言的語法或慣用語。  
  
### 5. 結論
用我們的觀點作為基礎，我們讓新手和老手程式設計師一個學習經驗，教他們一些關於物件的有價值的事情。CRC卡給予那些沒從未遇過物件的學習者一個對物件質(object-ness)的實際體會，並讓他們準備好來了解某個語言的語彙和細節。CRC卡也為那些已經學過物件機制卻還沒看見他們價值的人，提供了物件有用和令人信服的經驗。  
  
Ragu Raghavan[[7]](#ref7)曾說過轉換到物件，強的程設師更強，但弱的程設師被拋在後頭。in group settings使用這些卡片我們發現即使是較弱的程設師，不需對物件有很深的理解，也能對物件設計有貢獻。我們推測是因為設計更加具體，且物件間的邏輯關係很清晰，更容易去理解、評估，和修改一個設計。  
  
我們對實體上把卡片移來移去的價值感到驚訝。當學習者拿起一個物件，他們看起來對它更有認同感了，也準備好從它的觀點處理剩下的設計。正是實體互動的價值讓我們拒絕使用電腦化的卡片。  
  
It is just this problem-integrating the cards with larger design methodologies and with particular language environments, that we feel holds the most promise for the future. 維持實體互動價值的需求指出我們需要一個大大超越現有的新型態使用者介面和程式設計環境，就像我們今天擁有的系統大大超前過去以工具為導向的環境一般。

### 6. 參考資料

[[1] DeMarco, T.: Structured Analysis and System Specification, Yourdon, 1978.](id:ref1)

[[2] Smalltalk-80 image, Xerox Corp, 1983.](id:ref2)

[[3] HyperCard manual, Apple Computer Inc.](id:ref3)

[[4] Cunningham, W. and Beck, K.: "A Diagram for Object-Oriented Programs," in Proceedings of OOPSLA-86, October 1986.](id:ref4)

[[5] Wirfs-Brock, R. and Wilkerson, B. "Object- Oriented Design: a Responsibility-Driven Approach," submitted to OOPSLA '89.](id:ref5)

[[6] Reenskaug, T.: "A Methodology for the Design and Description of Complex, Object- Oriented Systems," technical report, Center for Industrial Research, Oslo, Norway, November 1988.](id:ref6)

[[7] Raghavan, R.: "Panel: Experiences with Reusability," in the Proceedings of OOPSLA '88, October, 1988.](id:ref7)

