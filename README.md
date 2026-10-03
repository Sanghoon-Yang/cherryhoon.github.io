<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>2026 후쿠오카 여행 플래너 Pro</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; -webkit-tap-highlight-color: transparent; }
    .checked-title { opacity: 0.45; text-decoration: line-through; }
    .no-scrollbar::-webkit-scrollbar { display: none; }
  </style>
</head>
<body class="bg-slate-100 text-slate-800 pb-28">

  <!-- 상단 헤더 -->
  <header class="bg-indigo-600 text-white p-5 rounded-b-3xl shadow-md sticky top-0 z-30">
    <div class="flex justify-between items-center max-w-md mx-auto">
      <div>
        <span class="text-xs bg-indigo-500 px-2.5 py-1 rounded-full font-semibold">2026.11.02 (월) - 11.05 (목)</span>
        <h1 class="text-xl font-bold mt-1.5">✈️ 후쿠오카 3박 4일 가이드</h1>
      </div>
      <div class="text-right text-xs opacity-95">
        <p>1박 유후인 · 2박 텐진</p>
        <p class="mt-0.5 font-semibold text-amber-300">출국: 11/5 17:50</p>
      </div>
    </div>

    <!-- 메인 탭 버튼 -->
    <div class="flex gap-1.5 mt-4 overflow-x-auto no-scrollbar max-w-md mx-auto" id="tabs">
      <button onclick="switchTab('day1')" id="tab-day1" class="tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-white text-indigo-600 shadow-sm whitespace-nowrap">Day 1 (월)</button>
      <button onclick="switchTab('day2')" id="tab-day2" class="tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-indigo-500 text-white whitespace-nowrap">Day 2 (화)</button>
      <button onclick="switchTab('day3')" id="tab-day3" class="tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-indigo-500 text-white whitespace-nowrap">Day 3 (수)</button>
      <button onclick="switchTab('day4')" id="tab-day4" class="tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-indigo-500 text-white whitespace-nowrap">Day 4 (목)</button>
      <button onclick="switchTab('spots')" id="tab-spots" class="tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-amber-400 text-slate-900 whitespace-nowrap">📍 지역별 추천</button>
      <button onclick="switchTab('tips')" id="tab-tips" class="tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-indigo-500 text-white whitespace-nowrap">🚌 교통·팁</button>
    </div>
  </header>

  <!-- 메인 컨텐츠 영역 -->
  <main class="max-w-md mx-auto p-4 space-y-4" id="content-area"></main>

  <script>
    const scheduleData = {
      day1: {
        title: "1일차: 후쿠오카 도착 & 유후인 료칸",
        subtitle: "2026-11-02 (월) | 유후인 숙박",
        items: [
          {
            id: "d1-1", time: "12:00 ~ 14:00", title: "후쿠오카 공항 도착 & 점심 해결",
            desc: "입국심사 후 공항 국내선 식당가 또는 하카타역에서 점심 (기차 탑승 시 에키벤 도시락 추천)",
            map: "후쿠오카 공항",
            recs: [
              { type: "맛집", name: "공항 국내선 라멘 활주로", note: "입국 직후 빠르게 후쿠오카 유명 라멘집 골라 먹기 좋음", query: "후쿠오카 공항 라멘 활주로" },
              { type: "맛집", name: "하카타역 에키벤 (기차 도시락)", note: "JR 유후인노모리 탑승 시 기차 안에서 경치 보며 식사", query: "하카타역 에키벤" },
              { type: "맛집", name: "신신라멘 하카타 데이토스점", note: "하카타 버스터미널/역 출발 전 빠른 식사", query: "신신라멘 하카타" }
            ]
          },
          {
            id: "d1-2", time: "14:08 ~ 16:30", title: "유후인역 이동 (버스 or JR)",
            desc: "고속버스(약 1시간 30분, 산큐패스) 또는 JR 열차(약 2시간 20분, 1호실 1A-D 명당)",
            map: "유후인역",
            recs: [
              { type: "볼거리", name: "유후인역 족욕탕 (아시유)", note: "역 구내에 있는 온천 족욕탕 (기념 타월 포함 소액 유료)", query: "유후인역" },
              { type: "간식", name: "유후인 사이다 & 롤케이크 (B-Speak)", note: "역 앞 거리에서 가볍게 사 먹기 좋은 명물 디저트", query: "B-Speak 유후인" }
            ]
          },
          {
            id: "d1-3", time: "16:30 ~", title: "료칸 체크인 & 가이세키 석식",
            desc: "유후료치쿠(또는 가이세키 료칸) 체크인 → 주변 산책 → 유카타 체험·노천탕·가이세키 석식",
            map: "유후료치쿠",
            recs: [
              { type: "료칸후보", name: "유후인 유후료치쿠 (Yufu Ryochiku)", note: "계획표에 적어두신 가성비·분위기 좋은 료칸", query: "유후료치쿠" },
              { type: "료칸후보", name: "유후인 바이엔 (Yufuin Baien)", note: "넓은 정원 노천탕과 정갈한 분고규 가이세키로 유명", query: "유후인 바이엔" },
              { type: "료칸후보", name: "유후인 산스이칸 (Sansuikan)", note: "유후인역 도보권 + 석식 부페/가이세키 만족도 높음", query: "유후인 산스이칸" }
            ]
          }
        ]
      },
      day2: {
        title: "2일차: 유후인 오전 산책 & 나카스 야경",
        subtitle: "2026-11-03 (화) | 텐진 숙박",
        items: [
          {
            id: "d2-1", time: "09:00", title: "기상 및 유후인역 짐 보관",
            desc: "체크아웃 후 유후인역 코인락커 또는 역 앞 인포메이션 센터에 짐 보관 (캐리어 2개 1,400엔)",
            map: "유후인역",
            recs: [
              { type: "팁", name: "유후인역 앞 치키 서비스 (짐 보관소)", note: "역 나와서 바로 오른쪽 건물, 대형 캐리어 보관 편리", query: "유후인역" }
            ]
          },
          {
            id: "d2-2", time: "09:00 ~ 13:00", title: "유노츠보 거리 · 플로랄 빌리지 · 긴린코 호수",
            desc: "도보 15분 이동하며 아기자기한 상점 구경, 유후인 점심 식사 및 호수 산책",
            map: "유후인 플로랄 빌리지",
            recs: [
              { type: "맛집", name: "유후마부시 신 (긴린코 본점/역전점)", note: "유후인 1순위 명물! 분고규/장어/토종닭 솥밥 (오픈런 추천)", query: "유후마부시 신" },
              { type: "간식", name: "금상 고로케 & 미르히(Milch) 치즈케이크", note: "유노츠보 거리 필수 길거리 간식 2대장 (따뜻한 치즈케이크 강추)", query: "유후인 금상고로케" },
              { type: "볼거리", name: "유후인 플로랄 빌리지 & 동구리노모리", note: "영국 코츠월드 풍 마을과 지브리 굿즈샵", query: "유후인 플로랄 빌리지" },
              { type: "볼거리", name: "긴린코 호수 & 토모소 신사(텐소신사)", note: "호수 위 수중 도리이가 있는 조용한 산책 스팟", query: "긴린코 호수" }
            ]
          },
          {
            id: "d2-3", time: "13:00 ~ 16:00", title: "하카타 경유 텐진 이동 & 호텔 체크인",
            desc: "버스(유후인→하카타역) 하차 후 지하철로 텐진 이동, 텐진 잘 호텔 체크인 및 휴식",
            map: "텐진역",
            recs: [
              { type: "맛집", name: "돈카스 와카바 (텐진 본점)", note: "[계획표 리스트] 저온 조리 하얀 옷 로스카츠·가츠산도 맛집", query: "돈카스 와카바 텐진" },
              { type: "간식", name: "일포르노 델 미뇽 (하카타역 크로와상)", note: "하카타역 환승할 때 줄 서서 사 먹는 미니 크로와상", query: "하카타역 크로와상 미뇽" }
            ]
          },
          {
            id: "d2-4", time: "17:00 ~ 19:30", title: "나카스 야경 · 유람선 · 캐널시티 분수쇼",
            desc: "나카스 이동 후 저녁 식사, 나카스강 야경 & 리버크루즈, 캐널시티 산책",
            map: "캐널시티 하카타",
            recs: [
              { type: "맛집", name: "이치란 라멘 본점 (나카스) / 캐널시티점", note: "[계획표 리스트] 나카스 강변의 상징적인 12층 본점 빌딩", query: "이치란 본점" },
              { type: "맛집", name: "모츠나베 라쿠텐치 / 오오야마 / 이치후지", note: "[계획표 리스트] 후쿠오카 대표 저녁 메뉴 대창전골", query: "모츠나베 이치후지 텐진" },
              { type: "맛집", name: "타카오 텐푸라 (캐널시티 4층)", note: "[계획표 리스트] 갓 튀겨주는 튀김 정식 + 명란젓 무제한!", query: "타카오 텐푸라 캐널시티" },
              { type: "볼거리", name: "나카스 리버 크루즈 & 포장마차(야타이) 거리", note: "30분간 나카스 강변 야경을 도는 유람선 (산큐패스 할인 가능)", query: "나카스 리버 크루즈" }
            ]
          }
        ]
      },
      day3: {
        title: "3일차: 다자이후 텐만구 & 다이묘·텐진 쇼핑",
        subtitle: "2026-11-04 (수) | 텐진 숙박",
        items: [
          {
            id: "d3-1", time: "09:00 ~ 10:30", title: "아침 식사 후 텐진 → 다자이후 이동",
            desc: "니시테츠 후쿠오카(텐진)역에서 다자이후행 전철 탑승 (약 30분 소요)",
            map: "다자이후역",
            recs: [
              { type: "맛집", name: "고메다 커피 / 백금다방 / 하카타 야키소바", note: "텐진 주변 모닝 토스트 세트나 간단한 아침 식사", query: "텐진 모닝 카페" }
            ]
          },
          {
            id: "d3-2", time: "10:30 ~ 14:00", title: "다자이후 텐만구 관광 & 점심 식사",
            desc: "다자이후역 인포메이션에서 가이드맵 수령 → 참배길 구경 → 텐만구 관광 및 점심",
            map: "다자이후 텐만구",
            recs: [
              { type: "간식", name: "카사노야 우메가에모찌 (매화떡)", note: "다자이후 필수 간식! 갓 구운 겉바속촉 팥떡", query: "카사노야 다자이후" },
              { type: "볼거리", name: "스타벅스 다자이후 오모테산도점", note: "건축가 쿠마 켄고가 전통 목조 짜임으로 설계한 명물 스타벅스", query: "스타벅스 다자이후" },
              { type: "맛집", name: "이치란 다자이후 참배길점 (합격 라멘)", note: "오각형 그릇에 나오는 다자이후 한정 이치란 라멘", query: "이치란 다자이후" },
              { type: "볼거리", name: "규슈 국립박물관 / 가마도 신사", note: "텐만구 뒤편 에스컬레이터로 연결되는 박물관 또는 귀멸의칼날 성지 신사", query: "규슈 국립박물관" }
            ]
          },
          {
            id: "d3-3", time: "14:00 ~ 17:00", title: "텐진 복귀 및 호텔 휴식",
            desc: "다자이후에서 텐진으로 돌아와 저녁 쇼핑 전 호텔에서 휴식",
            map: "텐진역",
            recs: [
              { type: "간식", name: "아이보리쉬(Ivorish) 프렌치토스트", note: "다이묘 거리 입구 브런치·디저트 맛집", query: "Ivorish Fukuoka" }
            ]
          },
          {
            id: "d3-4", time: "17:00 ~", title: "다이묘 거리 & 텐진 집중 쇼핑",
            desc: "다이묘 거리(빈티지·스트릿 쇼핑 성지), 텐진 지하상가, 빅카메라, 파르코 백화점 투어",
            map: "후쿠오카 다이묘 거리",
            recs: [
              { type: "볼거리", name: "텐진 파르코 (키디랜드 · 캐릭터샵)", note: "치이카와, 리락쿠마, 포켓몬, 닌텐도 굿즈 등 캐릭터 성지", query: "텐진 파르코" },
              { type: "볼거리", name: "빅카메라 텐진 1·2호관 & 돈키호테 나카스/텐진", note: "가전, 주류(위스키/사케), 드럭스토어 기념품 쇼핑", query: "빅카메라 텐진" },
              { type: "맛집", name: "쿠라스시 하카타 나카스점 / 텐진 주변 스시", note: "[계획표 리스트] 가성비 회전초밥 (비쿠라폰 캡슐 뽑기 재미)", query: "쿠라스시 하카타 나카스" },
              { type: "맛집", name: "신신라멘 텐진 본점 / 야키니쿠 바쿠로", note: "다이묘·텐진 쇼핑 후 저녁 식사로 인기 높은 곳", query: "야키니쿠 바쿠로 다이묘" }
            ]
          }
        ]
      },
      day4: {
        title: "4일차: 캐널시티(커비)·하카타 산책 후 출국",
        subtitle: "2026-11-05 (목) | 15:00 공항 도착 · 17:50 출국",
        items: [
          {
            id: "d4-1", time: "10:00 ~ 13:00", title: "늦은 기상 · 짐 보관 · 아점 식사",
            desc: "호텔에 짐 맡기고 주변에서 여유롭게 브런치 또는 점심 식사",
            map: "텐진역",
            recs: [
              { type: "맛집", name: "돈카스 와카바 / 타카오 텐푸라", note: "2~3일차에 못 갔던 계획표 맛집을 점심 오픈런으로 방문 추천!", query: "돈카스 와카바 텐진" },
              { type: "맛집", name: "우동 타이라 / 다이치노 우동", note: "후쿠오카식 부드러운 면발과 우엉튀김(고보텐) 우동 맛집", query: "다이치노우동 하카타" }
            ]
          },
          {
            id: "d4-2", time: "13:00 ~ 14:40", title: "캐널시티(커비) · 신사 · 하카타역 산책",
            desc: "남은 시간 취향에 맞춰 방문 (캐널시티 커비 굿즈, 구시다 신사, 스미요시 신사, 라쿠스이엔 등)",
            map: "캐널시티 하카타",
            recs: [
              { type: "볼거리", name: "🌟 커비 카페 하카타 & 더 스타 샵 (캐널시티 B1)", note: "[계획표 커비!] 사우스빌딩 B1층. 카페 식사는 사전 예약 필수지만, 옆 굿즈샵(THE STORE)은 예약 없이도 입장·구매 가능!", query: "커비 카페 하카타" },
              { type: "볼거리", name: "구시다 신사 & 가와바타 전통 상점가", note: "캐널시티 바로 옆! 거대한 장식 가마(야마카사)가 있는 하카타 총진수", query: "구시다 신사" },
              { type: "볼거리", name: "스미요시 신사 & 라쿠스이엔 (일본 정원)", note: "조용히 말차 한 잔 마시며 단풍/정원을 감상하기 좋은 힐링 코스", query: "라쿠스이엔" },
              { type: "볼거리", name: "하카타역 아뮤플라자 & 한큐백화점 지하 식품관", note: "공항 가기 직전 명란 바게트(풀풀), 히요코 만쥬, 손수건 등 선물 구매", query: "하카타 한큐백화점" }
            ]
          },
          {
            id: "d4-3", time: "15:00 ~ 17:50", title: "후쿠오카 공항 도착 & 출국 🛫",
            desc: "호텔 짐 찾은 후 공항 이동 (지하철/택시로 15~20분 소요!) → 17:50 출국",
            map: "후쿠오카 공항 국제선",
            recs: [
              { type: "팁", name: "텐진/하카타 → 국제선 택시 이동 추천", note: "짐이 많다면 택시 이용 시 공항 국제선 터미널 앞까지 15~20분(약 2,000~2,500엔)에 바로 도착해 매우 편함", query: "후쿠오카 공항 국제선" }
            ]
          }
        ]
      }
    };

    const areaSpots = {
      "유후인": [
        { cat: "맛집", name: "유후마부시 신", desc: "분고규(소고기)·장어·토종닭 3종 솥밥 맛집 (역전점/긴린코점)", q: "유후마부시 신" },
        { cat: "간식", name: "미르히 (Milch) 도넛·치즈케이크", desc: "따뜻하게 나오는 떠먹는 치즈케이크(케제쿠헨)와 푸딩", q: "유후인 미르히" },
        { cat: "간식", name: "금상 고로케", desc: "유노츠보 거리 대표 간식, 바삭한 바비큐 감자·게살 고로케", q: "유후인 금상고로케" },
        { cat: "볼거리", name: "유후인 플로랄 빌리지 & 긴린코 호수", desc: "동화 속 마을 테마파크와 물안개 피어오르는 호수 산책로", q: "긴린코 호수" },
        { cat: "볼거리", name: "스누피 차야 & 미피 모리노 베이커리", desc: "귀여운 캐릭터 빵과 굿즈를 파는 유노츠보 거리 인기 코스", q: "유후인 미피 베이커리" }
      ],
      "하카타·나카스·캐널": [
        { cat: "맛집⭐", name: "이치란 라멘 본점 (나카스)", desc: "[내 리스트] 나카스 강변의 상징적인 건물, 24시간 운영", q: "이치란 본점" },
        { cat: "맛집⭐", name: "타카오 텐푸라 (캐널시티 4F)", desc: "[내 리스트] 갓 튀겨 내어주는 바삭한 튀김 정식 + 명란젓 무제한", q: "타카오 텐푸라 캐널시티" },
        { cat: "맛집⭐", name: "쿠라스시 하카타 나카스점", desc: "[내 리스트] 돈키호테 나카스점 같은 건물(게이츠몰)에 위치한 대형 회전초밥", q: "쿠라스시 하카타 나카스" },
        { cat: "볼거리⭐", name: "커비 카페 하카타 & 굿즈샵", desc: "[내 리스트] 캐널시티 사우스빌딩 B1F! 커비 한정판 인형·키링·식기 판매", q: "커비 카페 하카타" },
        { cat: "볼거리", name: "구시다 신사 · 스미요시 신사 · 라쿠스이엔", desc: "[내 리스트] 캐널시티~하카타역 사이 도보로 묶어 보기 좋은 전통 신사·정원", q: "라쿠스이엔" }
      ],
      "텐진·다이묘": [
        { cat: "맛집⭐", name: "돈카스 와카바 (텐진 본점)", desc: "[내 리스트] 저온에서 튀겨 육즙이 가득한 특상 로스카츠 & 옥수수 콘카츠", q: "돈카스 와카바 텐진" },
        { cat: "맛집⭐", name: "모츠나베 (이치후지 / 라쿠텐치 / 오오야마)", desc: "[내 리스트] 텐진 주변에 본점/지점이 많아 저녁 맥주와 곁들이기 최고", q: "모츠나베 이치후지 텐진" },
        { cat: "맛집", name: "효탄 스시 / 스시로 텐진", desc: "텐진 중심가 줄 서서 먹는 대표 초밥 맛집", q: "텐진 효탄스시" },
        { cat: "볼거리", name: "다이묘 거리 (스트릿·빈티지 샵)", desc: "[내 리스트] 스투시, 슈프림, 빔즈, 메종키츠네 카페 등 젊은 감성 쇼핑 거리", q: "후쿠오카 다이묘 거리" },
        { cat: "볼거리", name: "텐진 지하상가 & 빅카메라 & 파르코", desc: "[내 리스트] 비 와도 쾌적한 유럽풍 대규모 지하상가 및 캐릭터·가전 쇼핑", q: "텐진 지하상가" }
      ],
      "다자이후": [
        { cat: "볼거리", name: "다자이후 텐만구", desc: "학문의 신을 모신 신사, 붉은 구름다리(타이코바시)와 매화나무 정원", q: "다자이후 텐만구" },
        { cat: "간식", name: "카사노야 우메가에모찌 (매화떡)", desc: "참배길에서 갓 구워주는 따뜻한 찹쌀 팥떡", q: "카사노야 다자이후" },
        { cat: "볼거리", name: "스타벅스 다자이후 오모테산도점", desc: "2,000개의 나무 기둥을 엮어 만든 세계적인 건축 명소 스타벅스", q: "스타벅스 다자이후" },
        { cat: "맛집", name: "다자이후 참배길 점심 (소바·오차즈케·합격라멘)", desc: "매실 소바, 명란 오차즈케, 이치란 합격 라멘 등 참배길 내 식사", q: "다자이후 맛집" }
      ]
    };

    const savedChecks = JSON.parse(localStorage.getItem('fukuoka_v2_checks') || '{}');
    let currentArea = "하카타·나카스·캐널";

    function toggleCheck(id) {
      savedChecks[id] = !savedChecks[id];
      localStorage.setItem('fukuoka_v2_checks', JSON.stringify(savedChecks));
      const el = document.getElementById('title-' + id);
      if (savedChecks[id]) el.classList.add('checked-title');
      else el.classList.remove('checked-title');
    }

    function toggleRecs(id) {
      const box = document.getElementById('recs-' + id);
      const btn = document.getElementById('recbtn-' + id);
      if (box.classList.contains('hidden')) {
        box.classList.remove('hidden');
        btn.innerHTML = '🔼 추천 닫기';
      } else {
        box.classList.add('hidden');
        btn.innerHTML = '💡 주변 맛집·볼거리 열기';
      }
    }

    function renderAreaSpots(areaName) {
      currentArea = areaName;
      switchTab('spots');
    }

    function switchTab(tabKey) {
      document.querySelectorAll('.tab-btn').forEach(btn => {
        if (btn.id === 'tab-spots') {
          btn.className = "tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-amber-400 text-slate-900 whitespace-nowrap";
        } else {
          btn.className = "tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-indigo-500 text-white whitespace-nowrap";
        }
      });
      document.getElementById('tab-' + tabKey).className = "tab-btn flex-1 py-2 px-3 rounded-xl text-xs font-bold bg-white text-indigo-600 shadow-sm whitespace-nowrap";

      const container = document.getElementById('content-area');

      if (tabKey === 'spots') {
        const areas = Object.keys(areaSpots);
        let areaBtns = areas.map(a => `
          <button onclick="renderAreaSpots('${a}')" class="px-3 py-1.5 rounded-full text-xs font-bold transition ${a === currentArea ? 'bg-indigo-600 text-white shadow' : 'bg-white text-slate-600 border'}">${a}</button>
        `).join('');

        let spotCards = areaSpots[currentArea].map(s => `
          <div class="bg-white p-4 rounded-2xl shadow-sm border border-slate-100 flex justify-between items-start gap-3">
            <div>
              <span class="text-[11px] font-bold px-2 py-0.5 rounded ${s.cat.includes('맛집') ? 'bg-rose-50 text-rose-600' : s.cat.includes('간식') ? 'bg-amber-50 text-amber-700' : 'bg-emerald-50 text-emerald-700'}">${s.cat}</span>
              <h3 class="font-bold text-base mt-1 text-slate-800">${s.name}</h3>
              <p class="text-xs text-slate-600 mt-1 leading-relaxed">${s.desc}</p>
            </div>
            <a href="https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(s.q)}" target="_blank" class="text-xs bg-indigo-50 text-indigo-600 px-3 py-2 rounded-xl font-bold whitespace-nowrap shrink-0">📍 지도</a>
          </div>
        `).join('');

        container.innerHTML = `
          <div class="space-y-3">
            <div class="flex flex-wrap gap-1.5">${areaBtns}</div>
            <p class="text-xs text-slate-500 px-1">⭐ 표시는 엑셀 계획표에 직접 적어두신 맛집·장소입니다.</p>
            <div class="space-y-2.5">${spotCards}</div>
          </div>
        `;
        return;
      }

      if (tabKey === 'tips') {
        container.innerHTML = `
          <div class="bg-white p-5 rounded-2xl shadow-sm space-y-3">
            <h2 class="text-base font-bold text-indigo-600">🚌 유후인 이동 방법 비교</h2>
            <div class="bg-amber-50 p-3.5 rounded-xl text-xs space-y-1.5 border border-amber-200">
              <p class="font-bold text-sm text-amber-900">1. 고속버스 (추천 ⭐)</p>
              <p class="text-slate-700">• 소요시간: 약 1시간 30분 (후쿠오카 공항 국제선 바로 탑승 가능!)</p>
              <p class="text-slate-700">• 패스 팁: <b>산큐패스 북큐슈 2일권</b> 구매 시 왕복 버스 + 시내버스까지 해결 (최대한 일찍 좌석 예약 필수)</p>
              <a href="https://www.highwaybus.com/gp/index" target="_blank" class="inline-block mt-1 bg-amber-500 text-white px-3 py-1.5 rounded-lg font-bold">🔗 Highwaybus 예약 사이트</a>
            </div>
            <div class="bg-slate-50 p-3.5 rounded-xl text-xs space-y-1 border border-slate-200">
              <p class="font-bold text-sm text-slate-800">2. JR 열차 (유후인노모리)</p>
              <p class="text-slate-600">• 소요시간: 약 2시간 20분 (하카타역 출발, 탑승 1개월 전 10시 예매 오픈)</p>
              <p class="text-slate-600">• <b>명당 좌석:</b> 1호차 1A~1D (기관실 통창 정면 뷰)</p>
            </div>
          </div>

          <div class="bg-white p-5 rounded-2xl shadow-sm space-y-2">
            <h2 class="text-base font-bold text-indigo-600">🌟 캐널시티 커비 카페 체크 포인트</h2>
            <p class="text-xs text-slate-600 leading-relaxed">
              • 위치: 캐널시티 하카타 <b>사우스빌딩 지하 1층</b><br>
              • <b>커비 카페(식당)</b>는 매월 10일 저녁 6시에 다음 달 예약이 열리며 순식간에 마감됩니다.<br>
              • 단, 바로 옆에 있는 <b>커비 카페 더 스토어(굿즈샵)</b>는 사전 예약 없이도 들어가서 커비 인형·한정 굿즈를 구매할 수 있습니다!
            </p>
          </div>
        `;
        return;
      }

      const day = scheduleData[tabKey];
      let html = `
        <div class="px-1">
          <h2 class="text-lg font-bold text-slate-800">${day.title}</h2>
          <p class="text-xs text-slate-500">${day.subtitle} · 제목 터치 시 완료 체크</p>
        </div>
      `;

      day.items.forEach(item => {
        const isChecked = savedChecks[item.id] ? 'checked-title' : '';
        const mapBtn = item.map ? `<a href="https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(item.map)}" target="_blank" class="text-xs bg-slate-100 text-slate-700 px-2.5 py-1 rounded-lg font-semibold whitespace-nowrap">📍 위치</a>` : '';

        let recsHtml = '';
        if (item.recs && item.recs.length > 0) {
          const recItems = item.recs.map(r => `
            <div class="flex justify-between items-center bg-slate-50 p-2.5 rounded-xl border border-slate-200/70">
              <div class="pr-2">
                <span class="text-[10px] font-bold px-1.5 py-0.5 rounded ${r.type.includes('맛집') ? 'bg-rose-100 text-rose-700' : r.type.includes('간식') ? 'bg-amber-100 text-amber-800' : 'bg-indigo-100 text-indigo-700'}">${r.type}</span>
                <span class="text-xs font-bold text-slate-800 ml-1">${r.name}</span>
                <p class="text-[11px] text-slate-500 mt-0.5">${r.note}</p>
              </div>
              <a href="https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(r.query)}" target="_blank" class="text-[11px] bg-white border border-slate-200 text-indigo-600 px-2.5 py-1.5 rounded-lg font-bold whitespace-nowrap shadow-2xs">구글맵</a>
            </div>
          `).join('');

          recsHtml = `
            <div class="mt-3 pt-2.5 border-t border-slate-100">
              <button id="recbtn-${item.id}" onclick="toggleRecs('${item.id}')" class="w-full text-left text-xs font-bold text-indigo-600 bg-indigo-50/70 hover:bg-indigo-100 px-3 py-2 rounded-xl transition flex justify-between items-center">
                <span>💡 주변 맛집·볼거리 열기 (${item.recs.length}곳)</span>
                <span>▼</span>
              </button>
              <div id="recs-${item.id}" class="hidden mt-2 space-y-2">
                ${recItems}
              </div>
            </div>
          `;
        }

        html += `
          <div class="bg-white p-4 rounded-2xl shadow-sm border border-slate-100">
            <div class="flex justify-between items-start gap-2">
              <div onclick="toggleCheck('${item.id}')" class="cursor-pointer flex-1">
                <span class="text-xs font-bold text-indigo-600 bg-indigo-50 px-2 py-0.5 rounded-md">${item.time}</span>
                <h3 id="title-${item.id}" class="font-bold text-base mt-1.5 text-slate-800 transition ${isChecked}">${item.title}</h3>
              </div>
              ${mapBtn}
            </div>
            <p class="text-xs text-slate-600 mt-1.5 leading-relaxed">${item.desc}</p>
            ${recsHtml}
          </div>
        `;
      });

      container.innerHTML = html;
    }

    switchTab('day1');
  </script>
</body>
</html>
