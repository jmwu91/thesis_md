# 方法論
本研究透過使用MeNGo系統在2023年11月的所有使用者之刷卡資料進行使用者的特徵分析，共計取得....。

## 主成分分析(PCA)

## K-means++

## 使用者行為變數

### 基本旅運統計行為特徵
1. 總使用天數：travel_days
2. 總使用次數：total_trips
3. 平均每日使用次數：avg_trips_per_day

### 對稱行程特徵
1. 對稱行程天數：symmetrical_days
2. 對稱行程比例：symmetry_ratio

### 使用時間特徵
1. 平均旅行時間：avg_travel_time
2. 旅行時間標準差：std_travel_time
3. 工作日旅次比率：weekday_trip_ratio
4. 假日旅次比率：weekend_trip_ratio
5. 尖峰時間使用比率：peak_hour_ratio

### 距離特徵
1. 總搭乘距離：total_distance
2. 平均搭乘距離：avg_distance
3. 最大搭乘距離：max_distance
4. 最小搭乘距離：min_distance
5. 搭乘距離標準差：std_distance

### 時間熵特徵
- 首趟行程的上車時間熵：first_boarding_entropy
	- $E_{\text{time, first}} = \frac{ -\sum_{i=0}^{23} P_{\text{first}, i} \log_2(P_{\text{first}, i}) }{ \log_2(24) }$
- 末趟行程的上車時間熵：last_boarding_entropy
	- $E_{\text{time, last}} = \frac{ -\sum_{i=0}^{23} P_{\text{last}, i} \log_2(P_{\text{last}, i}) }{ \log_2(24) }$
- 平均的上車時間熵：avg_boarding_entropy
	- $E_{\text{time, avg}} = \frac{1}{2} \left( E_{\text{time, first}} + E_{\text{time, last}} \right)$
		- $P_{first,i​}$：每天首趟出發時間落在第 $i$ 個小時（0到23）的機率。例如，若某人每天早上6點出發的機率是0.8，則 $P_{first,6}=0.8$。
		- $P_{last,i​}$：每天末趟出發時間落在第 $i$ 個小時（0到23）的機率。例如，若某人每天晚上10點出發的機率是0.7，則 $P_{last,22}=0.7$。
		- $log_2​(24)$：正規化因子，用來將熵的值標準化到0到1的範圍內，因為一天有24個小時，$log_2​(24)$ 是最大的可能熵值。


### 空間熵特徵
- 首趟行程的上車地點熵：first_boarding_place_entropy
- 首趟行程的下車地點熵：first_alighting_place_entropy
- 末趟行程的上車地點熵：last_boarding_place_entropy
- 末趟行程的下車地點熵：last_alighting_place_entropy


$$E_{\text{place}} = 
\begin{cases} 
0 & \text{if } n_{\text{unique}} \leq 1 \\ 
\frac{ -\sum_{a=1}^{n_{\text{unique}}} P_a \log_2(P_a) }{ \log_2(n_{\text{unique}}) } & \text{if } n_{\text{unique}} > 1 
\end{cases}$$


### 轉乘特徵
1. 總轉乘次數：total_transfer
2. 公車轉捷運次數：bus_to_mrt
3. 捷運轉公車次數：mrt_to_bus 
4. 工作日轉乘次數：weekday_transfer 
5. 假日轉乘次數：weekend_transfer
6. 平均轉乘次數：avg_transfer

### 活動站點特徵
1. 一天中第一次行程的上車地點個數：unique_first_boarding_place
2.  一天中第一次行程的下車地點個數：unique_first_alighting_place
3.  一天中最後一次行程的上車地點個數：unique_last_boarding_place
4. 一天中最後一次行程的下車地點個數：unique_last_alighting_place
