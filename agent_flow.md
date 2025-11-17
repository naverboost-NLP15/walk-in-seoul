```mermaid
sequenceDiagram autonumber actor User as 👤 사용자 participant App as 📱 모바일 앱 participant GPS as 🛰️ GPS/위치 서비스 participant MapAPI as ☁️ 지도/관광 API participant TTS as 🔊 TTS 엔진

User-->App: 앱 실행
activate App

Note over App, GPS: 1. 위치 파악 단계
App-->GPS: 현재 위치 요청
GPS--->App: 좌표 반환 (Lat, Lon)

Note over App, MapAPI: 2. 정보 탐색 단계
App-->MapAPI: 좌표 기반 주변 관광지 검색 요청
MapAPI--->App: 관광지 리스트(JSON) 반환

Note over App: 3. 정보 가공 단계
App-->App: 설명 텍스트 요약 및 정리

Note over App, TTS: 4. 서비스 제공 단계
par 동시 실행
    App-->User: 텍스트 및 사진 정보 표시 (UI)
and
    App-->TTS: 텍스트 ➔ 음성 변환 요청
    TTS--->App: 오디오 파일 스트림
    App-->User: 음성 안내 재생 (Speaker)
end

deactivate App

```
