# 경북 산불 디지털 트윈 (WebGIS_GB_wildFire)

경북 산불과 문화유산을 위한 웹 디지털 트윈입니다. 실시간 감시 모드는 기상청 면봉산 레이더, GK2A 산불 탐지, AWS 바람을 10분마다 받아 문화유산 경보 단계와 1시간에서 3시간 확산 예측을 계산하고, 재현 모드는 2025년 3월 22일부터 28일까지의 산불을 5분 또는 10분 단위로 다시 보여 줍니다.

**바로 보기:** https://kounghoonnam.github.io/WebGIS_GB_wildFire/

## 화면 구성
- 2D 지도와 3D 지형(오른쪽 위 3D 버튼): 3D에서는 레이더 볼륨 전체를 1 km x 1 km x 500 m 칸으로 쌓아 연기 기둥의 층별 구조를 보여 주고(날짜별 파일 vol/, 필요할 때만 내려받음), S3 저층 핵(해발 1.0-2.0 km)과 문화유산 경보 단계를 입체로 보여 줍니다.
- 기상청 면봉산 S밴드 레이더: 연기 기둥 높이(15 dBZ 에코 꼭대기)와 S3 저층 연기 기둥 핵
- 문화유산 경보: 경북 국가유산 1,650건(산불 경로 236건 구분)의 S3 경보, 화재 도달, 선행시간
- GK2A(2 km, 1시간)와 VIIRS(375 m) 화재 탐지, AWS 1시간 평균 바람
- Landsat dNBR 연소 심도, 최종 연소 범위, 남한 음영기복도와 고도 색, 경북 시군 경계

## 실시간 연결
연구용 PC가 10분마다 기상청 API허브에서 자료를 받아 판정하고, 결과 요약만 이 저장소의 `data` 브랜치(`live/state.json`)에 올립니다. 산불이 없을 때 레이더는 1시간마다 받습니다. API 키는 공개하지 않습니다.

## 경보 단계
- 긴급: 화재 도달(GK2A 화소 2.5 km 안, 30분 이상 간격 2회) 또는 1시간 안 도달 예측
- 경보: S3 신호(최근 6시간) 또는 설정한 예측 시간 안 도달
- 주의: 6시간 안 도달 예측

## 확산 예측(모의)
활성 화점마다 가장 가까운 AWS 바람으로 바람 방향 타원을 그립니다. 머리 확산 속도는 0.85 × 풍속(km/h)으로 2025년 3월 25일 관측에 맞췄고, 타원 비는 Alexander(1985) 식입니다. 지형과 연료는 반영하지 않습니다.

## S3 경보 기준
유산 반경 5 km 안에서 고도 1.0–2.0 km에 30 dBZ 이상, 상관계수 0.8 미만이고 15 dBZ 에코 꼭대기가 해발 3 km 이상인 반사도 핵이 연속 2개 볼륨에 나타나면 켜지고, 마지막 신호 뒤 6시간 유지됩니다. 지형 에코 칸과 비 에코 볼륨은 제외합니다.

## 한계
- 2025년 3월 사건 하나로 정한 연구용 기준이며 운영 경보로 검증되지 않았습니다.
- 화재 도달은 GK2A 2 km·1시간 자료 기준이라 건물에 불이 닿은 시각이 아닙니다.
- AWS 바람은 1시간 평균이며 순간최대풍속(돌풍)보다 약합니다.
- 피해 보도 유산은 언론 보도 기준입니다.

## 자료
기상청(면봉산 레이더 원시 자료, AWS·ASOS, GK2A), NASA FIRMS(VIIRS), USGS Landsat, 국가유산청 국가유산 공개 자료, 국토지리정보원 10 m DEM, Copernicus GLO-90 DEM.

---
Replay twin of the 2025 Gyeongbuk megafire (South Korea, 22-28 March 2025): KMA Myeonbongsan radar plume signals (S3 low-level plume cores) as early-warning indicators for heritage sites, with GK2A/VIIRS fire detections, AWS winds and Landsat dNBR. Single self-contained HTML file (`index.html`), runs offline in any modern browser.

Korean Fire Protection Association (KFPA), Kounghoon Nam.
