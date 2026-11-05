# Geo-Sleuth 분석 결과

사진은 튀르키예 네브셰히르주 괴레메의 **Traveller's Cave Hotel & Restaurant** 구내/안뜰에서 촬영된 것으로 판단한다. 사진 속 벽면 상호, 응회암 동굴 건축, 괴레메 지형, 공식 호텔 사진의 옥상 의자와 반복형 아치 조명이 일치한다.

## 위치

- 추정 장소: Traveller's Cave Hotel & Restaurant
- 주소: Aydınlı Mahallesi, Görçeli Sokak No:7, Göreme, Nevşehir, Türkiye
- WGS84 기준점: **38.639500, 34.827365**
- 오차 범위: **반경 40m**
- 좌표의 의미: 호텔 공식 연락처 페이지가 제공하는 Google Maps 건물/부지 핀이다. 정확한 셔터 위치는 확인되지 않았다.
- 촬영 방향: 대략 동쪽~동북동쪽(약 60~90도). 기하 계산으로 확정하지 못한 시각적 추정이다.

Google Maps:

- 기본 지도: https://www.google.com/maps/search/?api=1&query=38.639500%2C34.827365
- 위성 지도: https://www.google.com/maps/@?api=1&map_action=map&center=38.639500%2C34.827365&zoom=19&basemap=satellite
- 인접 Street View: https://www.google.com/maps/@?api=1&map_action=pano&pano=zwNXE5OvMTqzkWgoJ5kMVg&heading=0&pitch=0&fov=90

## 신뢰도

| 수준 | 신뢰도 | 근거 |
|---|---|---|
| 도시: Göreme | 높음 | 고유 숙소 상호와 공식 주소가 일치하며 지형도 부합 |
| 지역/숙소 부지 | 높음 | 공식 페이지, OSM, 공식 갤러리의 독립 자료가 수렴 |
| 도로: Görçeli Sokak | 중간 | 공식 주소와 10.58m 인접 Street View로 확인 |
| 건물/부지 | 중간 | 공식 핀과 갤러리 특징이 일치하지만 사진 속 정확한 외벽을 Street View에서 직접 보지 못함 |
| 정확한 카메라점 | 낮음 | EXIF 원본과 측량 가능한 원본 이미지가 없음 |

## 근거

1. 사진 벽면에 `Travellers Cave Hotel & Restaurant`가 선명하게 보인다. 이 읽기는 수동 판독이며, 원본 파일이 없어 OCR로 재검증하지 못했다.
2. 호텔 공식 연락처 페이지가 같은 상호를 **38.639500, 34.827365**, Görçeli Sokak No:7에 배치한다.
3. 현지 범위의 OSM `tourism=hotel` 36곳을 한꺼번에 후보로 올린 뒤 비교했으며, `Traveller's Cave` 노드가 **38.639787, 34.827224**에 있다. 공식 핀과 34.18m 차이다.
4. 공식 갤러리에서 사진의 벽 위에 보이는 밝은 색 의자와 반복되는 장식 아치 조명, 응회암 숙소 구조가 확인된다.
5. 가장 가까운 Google Street View 파노라마는 **38.6394688, 34.8272500**으로 공식 핀에서 10.58m 떨어져 있고, 괴레메의 능선 도로와 요정 굴뚝 지형을 확인한다.
6. 줌 19 위성 영상은 공식 핀 주변의 능선 가장자리 도로와 동굴 호텔 밀집 구조를 확인한다. 지형 고도는 약 1,137m다.

근거 합성 이미지는 `evidence.jpg`이며, 위에서부터 공식 호텔 갤러리, 인접 Street View, 줌 19 위성 영상이다. 원본 채팅 이미지는 실행 환경에 마운트되지 않아 합성 이미지에 포함하지 못했다.

## 실행 결과와 제한

- `doctor.py --network`: 대부분 통과했지만 검사 시점 Overpass 연결은 타임아웃이었다. 이후 OSM 호텔 질의는 성공했다.
- `poi.py`: 정확 상호 검색 결과가 0건이어서 공식 사이트와 OSM 직접 질의로 전환했다.
- `board.py`: 36개 현지 호텔 전체를 후보 보드에 등록했고, 최종 점검은 통과했다. K1 수동 텍스트 판독은 원본 크롭 파일이 없어 경고로 남았다.
- 실행 불가: `intake.py`, EXIF, 원본 OCR, Baidu/Yandex 역이미지 업로드, 원본 대상 `match.py`.
- 추가 실패: 후속 예배시설 OSM 질의는 모든 Overpass 미러가 끊겨 실행되지 않았다. 이에 촬영 방향은 근사치로만 제시한다.

실행 명령은 `commands.txt`, 후보 보드는 `board.json`, Windows GUI용 후보 파일은 `candidates.json`, 전체 기계 판독 결과는 `result.json`에 기록했다.
