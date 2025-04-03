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
1. 一天中第一次行程的上車時間熵：first_boarding_entropy
2. 一天中最後一次行程的上車時間熵：last_boarding_entropy
3. 平均的上車時間熵：avg_boarding_entropy

### 空間熵特徵
1. 一天中第一次行程的上車地點熵：first_boarding_place_entropy
2. 一天中第一次行程的下車地點熵：first_alighting_place_entropy
3. 一天中最後一次行程的上車地點熵：last_boarding_place_entropy
4. 一天中最後一次行程的下車地點熵：last_alighting_place_entropy

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
