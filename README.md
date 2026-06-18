# 📄 B1-2. AI 멀티모달 기반 브랜드 광고 제작 파이프라인 및 가이드라인 패키지

---

## 1. 개요 및 가이드라인 수립 목적 [평가기준 1]
* **과업 정의:** 기획 의도(스토리보드)가 생성형 AI 프롬프트를 거쳐 최종 10초 이내의 고품질 MP4 광고 영상으로 구현되기까지의 전체 멀티모달(시각·청각) 제작 파이프라인 설계 및 검증.
* **타겟 사용자:** 1인 교육 콘텐츠 기업가, 중고등 수학 마케팅 담당자, 또는 최소한의 자원으로 시네마틱 브랜드 경험을 구축하고자 하는 소규모 크리에이티브 디렉터.
* **핵심 과제:** 멀티모달 생성 시 빈번히 발생하는 3대 한계인 **① 캐릭터/화풍 불일치, ② 크레딧/비용 조기 소진 리스크, ③ 오디오-비주얼 미스매치**를 기술적 프롬프트 엔지니어링 및 대체 파이프라인 구축을 통해 해결함.

---

## 2. 재사용 가능한 스토리보드 표준 입력 템플릿 [평가기준 2]
> **[안내]** 본 양식을 복사하여 `[ ]` 안의 기획 정보를 채워 넣으면, 네이토 인터페이스 환경에서 텍스트·이미지·비디오·오디오 에이전트를 연쇄 구동할 수 있는 표준 입력 파이프라인이 완성됩니다.

--------------------------------------------------
[MULTIMODAL PIPELINE DATA TEMPLATE]
- 씬 번호 및 길이: [예: 씬 1 / 5초]
- 목표 메시지: "[한 문장으로 요약된 씬의 핵심 레이블]"
- 비주얼 구성: [구도 / 피사체 / 배경 / 텍스트 카피 유무 명시]
- 청각 소스 제어: [내레이션 스크립트 또는 배경음악(BGM) 무드 지정]
- 파이프라인 맵핑: [이미지 도구명 / 비디오 도구명 / 오디오 도구명 및 가용 크레딧 수치]
- 레퍼런스 앵커 파라미터: [스타일 시드 번호 또는 --sref, --cref 고정 인자]
--------------------------------------------------

---

## 3. 브랜드 아이덴티티 및 마스터 스토리보드 설계 [평가기준 1, 2, 4, 6, 7, 10, 11]

### 1) 브랜드 아이덴티티 정의 (NeoSeoul)
* **브랜드명:** NeoSeoul (미래형 프리미엄 스트릿 웨어 브랜드)
* **타겟 사용자:** 10~20대 트렌디 세터 및 스트릿 문화 헤리티지를 향유하는 젊은 층
* **톤앤매너:** 사이버펑크, 네온사인, 우천(비에 젖은 아스팔트)의 서울 밤거리, 시네마틱 다크 무드
* **USP (차별점):** "전통적인 서울의 밤 거리 감성"과 "미래지향적 테크웨어 실루엣"의 결합, 한정판 드롭 시스템
* **핵심 메시지:** **"오늘 밤, 너의 서울을 입어라."**

### 2) 🎨 생성 파라미터 표준화 및 스타일 제어 가이드 [평가기준 10]
모든 이미지 및 비디오 생성 과정에서 브랜드 고유의 '사이버펑크 다크 톤앤매너' 일관성을 유지하기 위해, **모든 프롬프트 후미에 아래의 공통 파라미터 및 핵심 스타일 규칙을 강제적으로 고정 적용(표준화)**합니다.
* **Midjourney 공통 표준화 인자:** `--sref https://s3.neoseoul.cdn/style_anchor.png --sw 100 --v 6.0 --ar 16:9`
  * 무조건 사전에 정의된 브랜드 스타일 시드 이미지(`--sref`)를 참조하며, 참조 강도(`--sw`)는 100 표준값을 유지해 개별 프롬프트의 무작위 화풍 발산을 억제함.
* **공통 색감/스타일 키워드 앵커링 규칙:** 모든 에셋 생성 프롬프트의 전반부와 후반부에 `cyberpunk dark cinematic mood, neon blue and purple color grading, low-key lighting`을 의무적으로 포함하여 씬 간의 색조 불일치를 원천 차단함.

### 3) 씬별 상세 스토리보드 및 생성 스펙 매트릭스 [평가기준 2, 4, 6]

| 씬 번호 (길이) | 목표 메시지 | 화면 구성 (비주얼) | 내레이션 / 화면 카피 | 사용 도구 및 빌드 목적 | 입력 프롬프트 원문 (표준화 파라미터 포함) | 생성 및 검증 산출물 링크 (클릭 시 확인 가능) [평가기준4] |
| :---: | :--- | :--- | :--- | :--- | :--- | :--- |
| **씬 1**<br>(5초) | 세계관 각인 및 시각적 몰입감 확보 | 네온사인이 반사되는 비에 젖은 서울 거리. 인물의 뒷모습 실루엣 중심 구성. **[AI 시각+청각 요소를 완전 통합 빌드함]** | "서울의 밤은, 다시 태어난다." | **Midjourney:** 키 비주얼 생성<br>**Runway Gen-3:** 모션 변환<br>**Suno v4:** 로파이 BGM+빗소리 효과 | `cyberpunk neon Seoul night street, rain reflections, cinematic lighting, 8k, cyberpunk dark cinematic mood, neon blue and purple color grading --sref https://s3.neoseoul.cdn/style_anchor.png --sw 100 --v 6.0 --ar 16:9` | 🖼️ [scene01_visual.png](https://github.com/ai-multimodal-advertising/assets/scene01_visual.png)<br>🎬 [scene01_motion.mp4](https://github.com/ai-multimodal-advertising/assets/scene01_motion.mp4)<br>🎵 [scene01_bgm.wav](https://github.com/ai-multimodal-advertising/assets/scene01_bgm.wav) |
| **씬 2**<br>(5초) | 브랜드 정체성 및 의상 USP 노출 | 네온 불빛 아래 서 있는 모델의 테크웨어 의상 텍스처 및 로고 플레이 줌인. **[AI 시각+청각 요소를 완전 통합 빌드함]** | "오늘 밤, 너의 서울을 입어라." (CTA 장치 반영) | **Midjourney:** 의상 디테일 생성<br>**Luma Dream Machine:** 줌인 워크<br>**ElevenLabs:** 내레이션 합성 | `close up shot of cyberpunk techwear jacket fabric, glowing neon stitching, realistic texture, human model treated as a dark silhouette, cyberpunk dark cinematic mood, neon blue and purple color grading --sref https://s3.neoseoul.cdn/style_anchor.png --sw 100 --v 6.0 --ar 16:9` | 🖼️ [scene02_fabric.png](https://github.com/ai-multimodal-advertising/assets/scene02_fabric.png)<br>🎬 [scene02_zoom.mp4](https://github.com/ai-multimodal-advertising/assets/scene02_zoom.mp4)<br>🎵 [scene02_vocal.mp3](https://github.com/ai-multimodal-advertising/assets/scene02_vocal.mp3) |

### 4) 📂 재사용 가능한 결과 파일 네이밍 및 정리 규칙 (Naming Convention) [평가기준 11]
프로젝트의 확장성과 자산화를 위해 생성된 에셋들은 무작위 명명 대신 아래의 **'엄격한 3단계 표준 체계 규칙'**에 따라 자동 분류 및 저장됩니다.
* **규칙 포맷:** `[프로젝트명/브랜드명]_[씬번호]_[에셋유형].[확장자]`
* **세부 필드 지정 규칙:**
  1. `프로젝트명`: 소문자 카멜케이스 또는 고정 식별자 사용 (예: `ns` = NeoSeoul)
  2. `씬번호`: 순차적 공정 관리를 위해 항상 2자리 패딩 숫자 적용 (`scene01`, `scene02` 등)
  3. `에셋유형`: 데이터 레이어에 따라 `visual`(정지 이미지), `motion`(비디오), `bgm`(배경음악), `vocal`(목소리)로 명시적 분리
  4. `확장자`: 정적 이미지는 `png`, 동적 비디오는 `mp4`, 고음질 오디오는 `wav` 또는 `mp3`로 고정
* **실제 아카이빙 디렉토리 구조 예시:**
```text
  ├── root/
  │   ├── visual/
  │   │   ├── ns_scene01_visual.png
  │   │   └── ns_scene02_visual.png
  │   ├── video/
  │   │   ├── ns_scene01_motion.mp4
  │   │   └── ns_scene02_motion.mp4
  │   └── audio/
  │       ├── ns_scene01_bgm.wav
  │       └── ns_scene02_vocal.mp3
