# 資料分析

## 主成分分析（PCA）


本節透過主成分分析（Principal Component Analysis, PCA）對 30 餘個旅次行為變數進行降維，萃取可代表出行行為差異的主要構面，後續將以其作為使用者分群依據。

### Factor loading

| Feature                       |    PC1    |    PC2    |    PC3    |    PC4    |    PC5    |
| ----------------------------- | :-------: | :-------: | :-------: | :-------: | :-------: |
| travel_days                   | 0.074848  | 0.282796  | -0.119480 | -0.278332 | 0.024753  |
| total_trips                   | 0.071285  | 0.296926  | -0.150977 | -0.268482 | -0.095833 |
| avg_trips_per_day             | 0.027357  | 0.141389  | -0.147019 | -0.052192 | -0.414660 |
| symmetrical_days              | -0.027288 | 0.293980  | -0.183776 | -0.228639 | -0.163773 |
| symmetry_ratio                | -0.027732 | 0.159816  | -0.159616 | -0.115679 | -0.247469 |
| avg_travel_time               | 0.000264  | 0.162018  | -0.290944 | 0.335231  | 0.168572  |
| std_travel_time               | 0.227504  | -0.025653 | -0.149048 | 0.198276  | -0.136633 |
| weekday_trip_ratio            | -0.044541 | 0.168333  | -0.035165 | -0.225991 | 0.441857  |
| weekend_trip_ratio            | 0.044541  | -0.168332 | 0.035157  | 0.225989  | -0.441855 |
| peak_hour_ratio               | -0.053868 | 0.061551  | -0.005550 | -0.183756 | 0.114912  |
| total_distance                | 0.035383  | 0.297475  | -0.273886 | 0.035607  | 0.038432  |
| avg_distance                  | -0.003092 | 0.165678  | -0.289710 | 0.345842  | 0.168331  |
| max_distance                  | 0.135675  | 0.133928  | -0.280228 | 0.306150  | 0.052734  |
| min_distance                  | -0.152118 | 0.084086  | -0.124452 | 0.261218  | 0.247421  |
| std_distance                  | 0.218126  | -0.019389 | -0.158374 | 0.213428  | -0.126825 |
| first_boarding_entropy        | 0.288537  | -0.077371 | -0.022348 | -0.059241 | 0.012784  |
| last_boarding_entropy         | 0.278198  | 0.034244  | -0.069781 | -0.154541 | 0.025303  |
| avg_boarding_entropy          | 0.306537  | -0.024388 | -0.049358 | -0.114682 | 0.020469  |
| first_boarding_place_entropy  | 0.225090  | -0.164092 | 0.047021  | 0.045524  | 0.183025  |
| first_alighting_place_entropy | 0.260636  | -0.156758 | -0.006790 | 0.049579  | 0.012067  |
| last_boarding_place_entropy   | 0.268824  | -0.102454 | -0.020367 | 0.017393  | -0.003434 |
| last_alighting_place_entropy  | 0.209180  | -0.125000 | 0.030430  | -0.008440 | 0.225620  |
| unique_first_boarding_place   | 0.256534  | -0.068382 | 0.025942  | -0.052357 | 0.149767  |
| unique_first_alighting_place  | 0.289524  | -0.022920 | -0.055341 | -0.084783 | -0.051393 |
| unique_last_boarding_place    | 0.285742  | 0.049618  | -0.069275 | -0.112814 | -0.070003 |
| unique_last_alighting_place   | 0.234281  | -0.024910 | -0.003030 | -0.106229 | 0.181134  |
| total_transfer                | 0.107915  | 0.281155  | 0.308880  | 0.120038  | -0.002115 |
| bus_to_mrt                    | 0.103389  | 0.258713  | 0.293466  | 0.104329  | 0.000615  |
| mrt_to_bus                    | 0.091850  | 0.280267  | 0.271741  | 0.112220  | -0.005077 |
| weekday_transfer              | 0.096391  | 0.283460  | 0.301454  | 0.110430  | 0.022430  |
| weekend_transfer              | 0.115217  | 0.113141  | 0.181912  | 0.109590  | -0.142955 |
| avg_transfer                  | 0.096428  | 0.244692  | 0.308819  | 0.156826  | 0.002471  |

### 使用者旅行行為構面 

本研究透過主成分分析（Principal Component Analysis, PCA）對使用者的旅次行為變數進行降維，以萃取出能代表公共運輸使用者旅次特性差異之核心構面，並進一步用於使用者集群分析。根據分析結果，前五個主成分（PC1 至 PC5）共解釋了約70%的資料變異，其各自所代表之行為構面與內涵解釋詳述如下。

PC1 - 出行規律性（24.1%）主要捕捉使用者在出行時間與地點上的規律性，代表使用者是否具有規律且可預測的出行行為。具體而言，此主成分的關鍵變數包括平均的上車時間熵、首趟行程的下車地點數、首趟行程的上車時間熵、末趟行程的上車地點數，以及末趟行程的上車時間熵。上述特徵皆直接反映使用者在時間與空間兩個維度的規律程度，熵值愈低則規律性愈高，顯示使用者的通勤行為愈固定；相反，熵值高者表示其出行的時間和地點相對較為隨機且變動。

PC2 - 使用強度與對稱性（18%）則以使用強度與行程對稱性為核心，表達使用者搭乘公共運輸系統的整體強度及其行程規律性。此構面的重要變數包括總搭乘距離、總使用次數、對稱行程天數、工作日轉乘次數及總使用天數。上述變數反映使用者整體對公共運輸依賴的程度以及出行模式的穩定性，對稱行程天數尤其能夠揭示固定通勤行程的規律性。

PC3 - 轉乘行為（12.9%）側重於轉乘行為，描繪使用者對於多模式或多路線公共運輸系統的利用狀況。主要變數涵蓋總轉乘次數、平均轉乘次數、工作日轉乘次數、公車轉捷運次數及平均旅行時間。此主成分顯示使用者對公共運輸網絡的整合性利用程度，轉乘行為越頻繁者通常表示對公共運輸系統的綜合使用更廣泛。

PC4 - 搭乘時間與距離（10.2%）涵蓋使用者在旅次距離與時間的平均特性，反映出個體公共運輸旅程的典型規模與時空範圍。主要特徵包含平均搭乘距離、平均旅行時間、最大搭乘距離、總使用天數與總使用次數。此維度顯示使用者旅次距離與時間的特徵，進一步區分出偏好長距離或短距離旅行之不同族群。

PC5 - 平假日使用情形（6.3%）則著重於使用者平日與假日的旅次分布特性，反映出使用者在不同類型日子的出行行為差異。核心特徵包括工作日旅次比率、假日旅次比率、平均每日使用次數、對稱行程比例與最小搭乘距離。此主成分能夠凸顯使用者是否有明顯的平假日差異，進一步辨識出偏好於工作日使用之通勤族群或偏好假日使用的休閒族群。

綜上所述，透過主成分分析萃取之五大主成分，清楚地顯示MaaS使用者於公共運輸旅次行為在規律性、使用強度與對稱性、轉乘特性、旅次長度及平假日使用差異等重要維度，有助於進一步輸入無監督機器學習模型進行更細緻之使用者族群特性分群。


## 使用者分群結果

### 各群集中位數特性描述（旅次行為變數）

本研究透過使用者

### 群集特性解釋與分類（通勤 vs. 非通勤）

#### 通勤族群 (C1 ~ C4)

C1 (長距離通勤族群)：C1群集之使用者使用天數中位數21天，工作日旅次比例96%，對稱比例中位數為1，說明主要皆於工作日進行公共運輸使用，且每日皆進行往返的旅次，屬於高度規律的通勤通學族群。本群集使用者的搭乘時間固定，主要集中在上下班尖峰時段，週末幾乎不使用公共運輸；此族群平均行程距離中位數約16公里，平均使用時間約43分鐘，且距離與時間的變異很小，說明該族群的起迄點距離較遠，需要透過公共運輸進行長距離之通勤行為；時間熵(0.1 ~ 0.22) 為通勤族群中最低，顯示其在公共運輸使用時段上具有明顯的時空規律性、通勤路線穩定、距離遠以及上下車站點高度固定 (起訖站點使用數量少、空間熵接近0)，反映出此群使用者之遠距離規律通勤行為。

C2 (高轉乘通勤族群)：C2群組之使用者同樣以通勤行為為主 (中位出行天數22天，對稱行程比例約95%)，其具有通勤族群中最明顯的轉乘行為特性。本群集使用者之公共運輸主要使用特性為公車及捷運間的轉乘，總轉乘次數之中位數為33次，工作日轉乘中位數31次，週末1次，說明本群集使用者主要於工作日依賴公車及及捷運間的組合使用完成通勤目的。整體而言，C4屬於多段多模式的通勤族群，需要透過轉乘來完成通勤路程。單次乘車時間較短 (平均時間之中位數約22分鐘)，平均單程距離約8公里，搭乘距離範圍於2～12公里之間，顯示通勤距離為中等距離且路線可能存在多種組合。此群集工作日使用比例為92%，說明多以工作日使用為主 ，部分行程發生在非尖峰或週末時段，時間熵 (0.23 ~ 0.38) 及空間熵 (0.27 ~ 0.6) 相較其他通勤族群高，常用起訖點為2~4個，說明本群使用者擁有多個常用的公共運輸站點，較沒有固定的起訖使用站點。

C3 (短距離通勤族群)：C3群組的使用者為短距離通勤族，出行高度規律 (中位出行天數21天，對稱行程比例100%)。此群組亦主要於工作日使用公共運輸 (佔比96%)，且多集中於上下班尖峰時刻 (尖峰時段佔74%)，週末極少使用。平均搭乘時間及距離為通勤族群中最短，平均使用時間之中位數為15分鐘，平均搭乘距離中位數為5公里；距離分布集中在3～7公里之間，顯示本群集使用者之旅次起訖點距離較近。時間熵介於 0.12 ~ 0.27 ，空間熵介於 0 ~ 0.33 ，說明本群集使用者在時空上的通勤規律性高，僅次於長距離通勤族群；本群集使用者無轉乘通勤行為，綜合以上特性可以說明本群集使用者具有短距離推規律通勤的行為特性。

C4 (多目的通勤族群)：C4群組的使用者以通勤為主，但同時展現出較多樣的出行活動。其出行頻率在各群中最高 (中位數出行天數23天)，大部分日子都有往返 (對稱比例約94%)，但也有少數日僅單程，週末搭乘比例達15%。單次乘車平均約26分鐘，平均單程距離約9.4公里，距離範圍從1.7公里的短程到14.7公里的長程皆有，行程時間和距離的變異為通勤族群中最大。此群組主要在平日搭乘 (85%)，但尖峰時段僅佔52%，顯示除了上下班通勤外，亦有不少在非尖峰時段的出行。時間熵介於 0.31 ~ 0.45，空間熵介於 0.32 ~ 0.65 皆為通勤族群中最高，說明本群集時空規律性上相較其他通勤族群中較不規律，另外每位使用者具有多個常用起訖站點 (2~5)，並考量其總旅次數較高，且亦具有明顯的對稱行程特性，並且在搭乘時間及距離上的變異性較高，說明本群集使用者於固定通勤學目的地外，亦有其他的旅次目的地，因此會有這些旅次特性。綜合以上旅次特性，總體說明C4族群屬於通勤並有多元活動目的之族群，一方面有規律通勤習慣，另一方面也頻繁利用公共運輸滿足非通勤的出行需求。
##### 通勤族群綜述

通勤族群的共同特徵是出行頻率高且規律，幾乎每天皆透過公共運輸進行通勤行為。這些群組於平日使用比例極高，週末很少搭乘，顯示以工作日之通勤通學為主要目的。對稱行程比例均接近1，意即大部分使用日都包含了家及工作地點之往返旅次，可以視為典型的通勤模式。通勤族群的尖峰時段搭乘比例較高，行程時間通常固定在早晚高峰，日常作息穩定。時空之規律性上，通勤族群皆具有較低的時間及空間熵，與通勤通學之使用者具有固定時間上班及上學之特性吻合。整體而言，此族群展現出高度規律的公共運輸使用行為，反映每日通勤需求，是為 MaaS 系統中使用行為最穩定之使用族群。

#### 非通勤族群 (C5 ~ C8)

C5：C5族群的使用者為中等使用頻率的多元出行族群，出行天數之中位數為 13 天，期間總搭乘22次 (每日平均約1.7趟)。對稱行程比例為0.6，說明在本群集使用者沒有固定的家工作旅次，在行程上的對稱性不高，推測可能屬於私人運具及公共運輸混合使用之使用者；本群集中平均搭乘時間之中位數約18.5分鐘，搭稱時間之變異數較大 (標準差10分鐘)；平均單程距離約6.5公里，搭乘距離介於 1.3 ~ 13.7 公里，顯示此群集中使用者之搭乘時間及距離具有明顯的差異。大多搭乘發生在平日 (約75%)，週末佔25%；尖峰時段乘車僅約40%，多數搭乘時間避開了上下班高峰。該群集之時間熵於 0.5 上下，地點熵皆大於 0.7 ，表現出本群集使用者的搭乘時間分散且無固定起訖點，屬於低時空規律性之特性。轉乘行為偶見但不頻繁，中位數期間僅發生約1次轉乘，綜合本群集使用者以上公共運輸旅次特性，可以去推測本群集之屬於公共運輸及私人運具之使用者，本群使用者並非皆以公共運輸作為日常通勤學使用，而是透過公共運輸及私人運具之混合使用以滿足其出行需求，推測可能主要為分布在市區之學生族群，部分時間以公共運輸完成通學目的，部分時間透過家長接送等方式完成旅次目的。

C6：C6族群使用者屬於間歇性平日搭乘者，中位數出行天數為9天，期間總搭乘13次 (每日平均約1.4趟)。9天中僅1天具有對稱行為，其餘多為單程搭乘。單次乘車耗時平均約14分鐘，平均距離約4.8公里，行程時長與距離皆偏短且變異不大 (距離介於2.2～7.6公里)。使用行為主要集中在平日 (佔90%，週末僅10%)，尖峰時段搭乘約佔一半，顯示部分行程在上下班高峰，其餘則在非尖峰時段。於時空規律性部分，本群集使用者時間熵皆於0.3 上下，地點熵於0.75上下，每位使用者平均涉及2~3個不同的上下車地點組合無單一固定路線，說明使用者本群集使用者時間規律性較高但空間規律性低。可以推測在本群集使用者中，使用者具有規律的上下課或上下班作息，但並不會直接回家，具有其他目的地，進而導致使用站點分布及數量較高，此外，該群組幾乎不需要轉乘，大多數行程可由單一路線直達。基於以上特性推測本群集使用者可能也多屬於學生族群，因為其使用多於平日、旅次距離及時間較短且較少轉乘行為之特性，相較於C5族群，本族群有更多旅次目的透過私人運具滿足。

C7：C7的使用者之使用天數中位數為4天，總旅次中位數為7次，假日使用比例為 0.6，屬於週末出行為主的使用者族群。平均搭乘時間中位數約24分鐘，標準差約12分鐘；距離平均約8.6公里，搭乘距離介於2.8 ~ 14.6公里，顯示該群組出行距離有遠有近。在時空規律性，時間熵於0.3上下，屬於規律的出行時間；空間熵介於0.72 ~ 0.96，說明本群集具有高度不規律之行程起訖點，尖峰時段出行比例僅約33%，多數使用者之行程均避免尖峰時段。綜合以上使用者公共運輸使用特性之描述，可以理解本族群屬於假日透過公共運輸進行休閒娛樂等多種目的之使用者。

C8：C8群組的使用者屬於極低頻的公共運輸使用者。中位數出行天數僅1天，期間總共搭乘2次，顯示該群許多使用者可能只有一次的乘車行為。當日並未形成往返對稱 (對稱比例為0)，意即只發生了單向行程 (可能僅有去程，未於同日搭乘返回)。單次乘車耗時約15分鐘，距離約5.3公里，總行程距離約12.5公里，屬一次性中短途出行。所有搭乘發生在工作日，且其中一半在尖峰時段，但由於樣本極少，因此此比例僅供參考。且因僅有單日資料，無法去計算該族群使用者之時空規律性，導致本族群之時間與空間熵皆為0，可將本群使用者視為一次性使用者。

##### 非通勤族群綜述

於非通勤族群中，各集群的共通點是公共運輸使用頻率低但模式多樣，缺乏規律性。相對於通勤族群，非通勤族群並非以公共運輸系統作為主要移動工具，而是偶爾使用公共運輸，作為日常出行行為的輔助。許多使用日只有單向行程而非往返，因此對稱出行比例普遍較低。這些群組更常在週末或非尖峰時段出行，平日搭乘比例相對較低，說明在出行目的上以休閒、非通勤通學之需求為大宗。時間和空間規律性上，非通勤族群的熵值明顯較高，表示上下車時間和地點分布較廣，每次出行可能有不同的路線與目的地。整體而言，非通勤族群呈現零散而靈活的搭乘習慣，主要利用 MaaS 系統去滿足通勤以外出行需求。

### 效果量檢定

- (Kruskal-Wallis、Cliff’s delta)

### 集群結果討論

透過K-means++將高雄市MaaS系統 - MeNGo 使用者分為八個不同特性之使用者集群，其中分出兩大類使用者族群，分別為通勤與非通勤族群，並於其中體現出各自不同的公共運輸使用樣態，說明在MaaS使用者們在公共運輸使用模式上的多樣性，





## 各群集之空間與個人特徵分布


為進一步探討群集差異是否與個體屬性（如卡別）或站點周邊環境特性有關，本節彙整各群在捷運站點分布、使用者身分及運具使用比例之實際情形，以提供後續模型分析之基礎觀察。

### 捷運站點分布

### 卡別比例
![[Pasted image 20250619101851.png]]

### 運具使用比例

基於此分類結果，本研究為進一步探討在通勤族群內部是否存在不同的通勤行為機制，本研究聚焦於通勤族群，即C3 ~ C6 群集，欲了解影響其群集屬性的潛在因素。考量公共運輸使用行為容易受到站點周邊設施與接駁資源影響，遂選取捷運站周邊之公共運輸接駁系統（如公車與共享自行車站點數）及興趣點（POI，包括學校、醫院、商場等）作為解釋變數，並以群集代碼為應變項，建立多項羅吉特模式（Multinomial Logit Model, MNL），以探索各項空間與設施特徵是否為影響使用者通勤行為差異的重要因子。

## 通勤族群多項羅吉特模式分析（MNL）


接續前述分群與空間特徵結果，為驗證站點周邊環境是否影響通勤族群之歸屬，本節針對通勤導向之群集（Cluster 1 至 Cluster 4）建立多項羅吉特模式（Multinomial Logit Model, MNL），以群集編號作為應變項，探討站點周邊公車與自行車接駁設施密度、各類興趣點數量、卡別等捷運站點及使用者個人特徵是否於各群集間具有潛在差異。

C1 (長距離通勤族群)

%% C1 群體呈現典型的長距離通勤者特徵：單程通勤距離最長（中位數約16.2公里），單程時間亦最久（約43分鐘）。他們幾乎每天皆往返相同的起訖站，通勤路線高度固定（首末站多樣性指數接近0）。旅行具有完全的對稱性（對稱出行日比例為100%），絕大多數出行發生於平日（週末出行僅約4%），尖峰時段出行比重約佔一半。模式選擇上，此群體以純捷運通勤為主，約61%的通勤旅次僅搭乘捷運直達，極少數情況下才會額外接駁公車或公共自行車（兩者比例皆約一成左右）。卡別分佈方面，C3 群體是各群中成人卡比率最高的一群（成人卡佔53%，高於學生卡的47%） %%

多項羅吉特模型結果進一步印證了上述特性。相較於其他群體，C1 群體乘客的起訖站周圍可利用的公車路線數與公共自行車站點數較少：每增加1條站點周圍公車路線，乘客屬於 C2、C1、C2 群體的勝算相對於 C1分別顯著提高約10%、7%和4%，顯示 C1 通勤者的上車地點普遍缺乏公車路網支援；同樣地，每增加1處 YouBike 場站也會使乘客屬於 C2–C2 群的機率提高14–28%，意味著 C1 群體常在缺乏公共自行車服務的地區上車（例如郊區非核心地帶）。因此，可以推測C1 通勤者可能仰賴私人交通工具（如汽機車）接駁至捷運站，再搭乘捷運進行長程通勤，而較少使用公車或公共自行車作為接駁工具。模型亦顯示當捷運站周邊大型商場密度較高時，更傾向出現C1 群體；另外若周邊醫院數量多也較可能屬於C1。這現象可能是因為部分長距離通勤族會前往郊區終點站附近的大型醫院（例如岡山高醫、小港醫院等）或都會型購物中心，就業場所或通勤終點與上述POI重疊的比例較高所致。綜上，C1 群體代表了一群通勤模式單一、距離遠且路線固定的上班族，他們多為成人，上下班高度規律且依賴捷運本身完成通勤。

C2 群體（高轉乘族群）

%% C2 群體的通勤者明顯帶有多段轉乘的特性。從行為指標來看，此群體在觀察期間的總轉乘次數中位數高達33次；每日平均約發生1.5次轉乘事件（幾乎每趟通勤都需要接駁）。轉乘主要發生在公車與捷運間：例如上班時從住家搭公車接駁至捷運站，下班再從捷運接駁公車回家，符合其公車接駁依賴族的定位。模式選擇圖亦顯示，C2 群體幾乎每一次通勤都會結合公車；約有54%的旅次是「捷運+公車」，另有46%同時使用了公車與公共自行車兩種接駁【9†】。相對而言，純捷運直達的情形在此群幾乎不存在（比例近乎0）。其通勤距離中等（單程約8公里）且時間適中（約22分鐘）。尖峰時段比重約49%，週末出行率約8%——與長距離的 C1 群體接近，說明他們平日時段略有彈性、週末偶有出行。路線多樣性方面，C2 群體不像 C1 那樣單一路徑：其起訖站的選擇較為分散，平均首站和末站的熵值顯著高於 C1（例如可能有2個常用起點、3個不同下車地點），顯示此群體的通勤目的地不止一處，偶爾在不同地點上下車。人口構成上，C2 群體以學生為主（學生卡佔73%【12†】），成人比例相對較低。 %%

C2 群體在模型中的表現符合其高度仰賴轉乘環境的特質。首先在公車路線數對屬於 C2 的勝算提升幅度最大（RRR≈1.10），高於對C3和C4的影響。換言之，相較於長距離通勤的 C1 族群，C2 乘客的住家周圍往往有更密集的公車路網可供選擇，方便其透過多條路線換乘。這與他們需要依靠公車接駁的情形相符，也解釋了為何 C2 在平日離峰或週末仍有一定出行：公車提供了靈活的接駁可能性。其次，起訖端周圍的 YouBike 設站數對 C2 也有顯著正向影響（上車端 RRR≈1.28，下車端 RRR≈1.13）。這表示 C2 群體相較於C1，更常透過具有公共自行車服務之捷運站點作為旅次起訖點，可能象徵他們的通勤起點多位於市區、交通樞紐等具多元運具供應的地帶。%% 然而，大型公共自行車站點的樁位數對 C2 的影響呈現負相關——也就是說，在 YouBike 營運量特別大的樞紐附近上車的乘客較不屬於 C2 群體，暗示 C2 通勤者雖仰賴公車與自行車接駁，但主要出發自一般社區型站點，而非大型轉運中心。 %% 最後，POI變數方面，C2 群體的下車端明顯偏向於學校數量較多的區域（RRR≈1.07），符合其學生族群占比較高的特徵；相對地，他們對於醫院類場站的分布沒有明顯傾向（RRR≈0.91，不顯著），顯示此群體通勤目的地較少在醫療院所附近，而更可能是在學校或一般商業區域。總體而言，C2 群體可視為高轉乘依賴的通勤族，他們多為學生或年輕族群，來往地點較多且分散，充分運用公車與自行車等多種方式接駁捷運。

C3 群體（短距離高規律族群）

%% C3 群體的通勤模式可稱為短距離、高規律。他們單程通勤距離最短（約5.2公里）且時間極短（約15分鐘），通勤路程幾乎都是捷運線網中的少數幾站之間。尖峰通勤比例高達約74%，為各群之冠；週末極少搭乘捷運（週末旅次佔比僅4%）。通勤日幾乎每天都包含往返雙程（對稱率100%），路線選擇相對固定但不若 C1 絕對單一：例如本群體典型乘客可能有一個主要目的地（如學校或公司）以及一個次要常去地點，對應首末站多樣性指數略高於0（首段下車地點熵=0.258）。模式組合方面，C3 群體以純捷運通勤者為主流（約53%旅次無其他接駁）【9†】；同時，本群也是除C2外最常使用公共自行車接駁的一群：約28%的通勤包含捷運+YouBike 的組合【9†】。公車在此群體中相對少見，只有不到一成的旅次涉及公車接駁【9†】，且從刷卡轉乘資料看出他們的公車-捷運轉乘次數中位數為0。人口組成上，C3 雖以學生為主（學生卡約70%）【12†】，但成人比例（30%）亦高於 C2 群體，暗示這個短距離通勤族群可能同時涵蓋住校學生和在市區近距離通勤的社會人士。 %%

模型結果揭示了C3 群體在通勤環境上的幾個關鍵特徵。首先，C3 通勤者的上車端周圍往往設有大型公共自行車站：上車處每增加一個公共自行車租借站點（例如大型 YouBike 樞紐站），乘客屬於 C3 群體的機率顯著提高。這意味著此群體常從捷運/公交交會的主要樞紐出發，可能騎乘公共自行車進入捷運系統——例如從設有大型自行車租賃站的捷運站周邊騎車前往該站搭乘捷運。相對地，擁有大型 YouBike 樞紐的起點對 C2（高轉乘族群）的影響為負，因此大型樞紐騎乘自行車接駁的通勤方式更能代表短距離的 C3 群體特性。其次，下車端的公共自行車供應對 C3 集團的區隔力也非常強，於模式結果顯示，若捷運站點每增加1處 公共自行車站點，乘客屬於 C3的機率相對C1提高約41%。這與其模式組合相符，因此推測多數 C3 群集使用者於捷運出站後會利用公共自行車完成最後一哩路的接駁，例如從捷運站騎至目的地。第三，在 POI 部分，C3 群體顯著迴避醫院及大型商場等設施密集的通勤目的地（醫院周邊RRR≈0.48，商場RRR≈0.85）。反之，當目的地鄰近其他類別的場所（如圖書館、文化中心、藝術園區等）時，更容易屬於 C3。這可能反映出該群體中許多學生通勤者的活動範圍：短距離通勤除了上課/上班之外，也可能是前往圖書館自習或市中心文化場所活動，因此其通勤目的地周邊常出現這類場所。綜合而言，C3 群體代表那些通勤距離短但頻率高的捷運使用者——他們大多數日子都按固定路線通勤，偏好步行或騎乘 YouBike 接駁捷運，極少使用公車。

C4 群體（中距離多元通勤族群）

%% C4 群體的通勤行為以多樣性和彈性為主要特點。其通勤距離屬中等（單程約9.4公里）且時間適中（約26分鐘），但個體間差異較大（距離和時間標準差最高）。這表示 C4 成員中有些人的通勤路程接近長距離群，也有些相當短程，整體分布分散。尖峰時段佔比約52%，僅略高於一半；再考慮到平日出行率僅85%、週末出行高達15%的情況，可推斷C4 群體不僅在傳統上下班時段搭乘捷運，還包含相當多非尖峰或假日的出行需求。每日通勤並非總是成對出現（對稱率94%），顯示他們有時僅單向搭乘捷運（另一路徑可能改以他法出行或當日不返程）。此外，C4 群體擁有全群體中最多樣化的起迄站選擇：其首末站熵值及不同站點數皆為最高，如典型乘客可能有2個常用起點、4個不同目的地下車站，及多達5個不同返程上車站點。這反映C4 群體的通勤目的高度多元，不局限於單一地點——可能平日有主副兩個工作場所，或經常變換下班後前往的地點（如進修、社交活動等）。其模式使用分配同樣多樣：純捷運直達僅佔32%【9†】；其餘近七成旅次中，捷運會結合公車及/或 YouBike 接駁。其中約26%為「捷運+YouBike」，14%為「捷運+公車」，另有28%更複雜，涉及公車與自行車兩端並用【9†】。值得一提的是，儘管C4 旅次中公車出現率合計達42%，但從轉乘紀錄看至少半數成員很少真正轉乘公車（轉乘中位數0次）。這意味著 C4 內部存在異質：部分人在某些日子大量使用公車接駁（尤其體現在旅次組合比例上），但整體而言公車並非此群體每日通勤的剛性需求；相反地，YouBike 則是較普遍的選擇（因為即使不轉公車，C4 群體仍有超過四分之一旅次搭配自行車）。人口結構方面，C4 群體學生與社會人士皆有（學生卡約60%，成人卡40%）【12†】，是除了 C1 外成人比例最高的一群。 %%

C4 群體的多元通勤行為也反映在模型參數上。首先，C4 乘客的居住地與工作地附近通常具備一定的公交與自行車服務，但影響幅度介於 C2/C3 和 C1 之間。在上車端，每增1條公車路線，屬於 C4 的勝算相對 C1 增加約4%（達統計顯著但效應較小）；每增1處 YouBike 設點則提高約14%。下車端亦類似：公車站數量對 C4 並無顯著作用（相較之下只對 C3 有顯著影響），而自行車站點數增加則顯著提高該使用者屬於 C4 集群之機率（RRR≈1.27）。換言之，C4 通勤者主要出現於大眾運輸與其他接駁運具皆具一定可及性的站點，但他們對特定接駁方式並不如 C2 或 C3 那般主要依賴公車及公共自行車，本群集使用者可能根據不同日子的需要，於步行、自行車與公車等方式中靈活切換。其次，C4 群體在 POI 變數上的趨勢與 C3 有些相似但程度較緩。此群體的通勤目的地明顯遠離大型醫院（RRR≈0.57）與商場（RRR≈0.88）；相對地，目的地附近出現「其他」類場所時，屬於 C4 的可能性提升（RRR≈1.46）。儘管C4 中也有40%為上班族，但上述結果暗示其通勤動機部分帶有與學生族群相似的傾向，例如經常前往文化、藝文等休閒場所，或者工作地點遠離大型商業中心等。總括而言，C4 可被視為中等距離且通勤安排彈性的一群捷運使用者：他們結合各種交通方式以滿足多變的行程需求，通勤範圍和時間較其他群體更廣，體現出都會區現代通勤者工作生活混雜、多點移動的特性。


## 結果與討論


