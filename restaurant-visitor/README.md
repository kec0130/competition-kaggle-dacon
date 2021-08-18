# Kaggle - Recruit Restaurant Visitor Forecasting

- 해커톤 기간: 2021년 8월 4일 ~ 6일
- 대회 링크: https://www.kaggle.com/c/recruit-restaurant-visitor-forecasting/overview

## Overview

- Evaluation: RMSLE
- Data Source: hpg, air (파일명에 접두어로 붙어있음)
- Time Period
  - train: 2016 ~ 2017. 4월
  - test: 2017. 4월 마지막주 ~ 5월 (일본 휴일 '골든 위크' 기간 포함, 비영업일은 scoring에서 제외)

## Data Description

- air_reserve.csv : air 시스템 예약 내역
  - `air_store_id` : air 시스템에 등록된 id
  - `visit_datetime` : 예약 시간
  - `reserve_datetime` : 예약을 create한 시간
  - `reserve_visitors` : 예약 인원
- hpg_reserve.csv : hpg 시스템 예약 내역
  - `hpg_store_id`
  - `visit_datetime`
  - `reserve_datetime`
  - `reserve_visitors`
- air_store_info.csv : air 시스템에 등록된 매장 정보
  - `air_store_id`
  - `air_genre_name`
  - `air_area_name`
  - `latitude` : 매장이 위치한 *지역*의 위도
  - `longitude` : 매장이 위치한 *지역*의 경도
- hpg_store_info.csv : hpg 시스템에 등록된 매장 정보
  - `hpg_store_id`
  - `hpg_genre_name`
  - `hpg_area_name`
  - `latitude`
  - `longitude`
- store_id_relation.csv : 양쪽 모두에 등록된 매장의 id
  - `hpg_store_id`
  - `air_store_id`
- air_visit_data.csv : air 매장 일자별 방문객 수
  - `air_store_id`
  - `visit_date`
  - `visitors`
- date_info.csv
  - `calendar_date`
  - `day_of_week`
  - `holiday_flg` : 일본 휴일 해당 여부
- sample_submission.csv
  - `id` : `air_store_id`\_`visit_date` 조합
  - `visitors` : 해당 매장, 해당 일자의 방문객 수(예측 대상)

> 정리

store id와 date로 visitors 예측

- store: air_store_info.csv, hpg_store_info.csv, store_id_relation.csv
- date: air_reserve.csv, hpg_reserve.csv, air_visit_data.csv, date_info.csv
- columns: `store_id`, `visit_date`, `day_of_week`, `holiday_flg`, `genre_name`, `area_name`, `latitude`, `longitude`, `visitors`
