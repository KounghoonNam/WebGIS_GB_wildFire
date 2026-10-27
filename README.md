# 경북 산불 레이더 재생 트윈 (WebGIS_GB_wildFire)

2025년 3월 22~28일 경북 초대형 산불을 5~10분 단위로 다시 보는 웹 지도입니다.

**바로 보기:** https://kounghoonnam.github.io/WebGIS_GB_wildFire/

## 화면 구성
- 기상청 면봉산 S밴드 레이더: 연기 기둥 높이(15 dBZ 에코 꼭대기)와 S3 저층 연기 기둥 핵
- 문화유산 경보: 경북 국가유산 1,650건(산불 경로 236건 구분)의 S3 경보, 화재 도달, 선행시간
- GK2A(2 km, 1시간)와 VIIRS(375 m) 화재 탐지, AWS 1시간 평균 바람
- Landsat dNBR 연소 심도, 최종 연소 범위, 남한 음영기복도와 고도 색, 경북 시군 경계

## S3 경보 기준
유산 반경 5 km 안에서 고도 1~2 km에 30 dBZ 이상, 상관계수 0.8 미만이고 15 dBZ 에코 꼭대기가 해발 3 km 이상인 반사도 핵이 연속 2개 볼륨에 나타나면 켜지고, 마지막 신호 뒤 6시간 유지됩니다. 지형 에코 칸과 비 에코 볼륨은 제외합니다.

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
