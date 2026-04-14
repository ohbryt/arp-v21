# ARP v21 모듈 상태표

## 개요
이 표는 ARP v21의 각 모듈의 실제 구현 상태를 명시합니다.  
**중요**: 이 프로젝트는 연구용 데모이며, 실제 생산 환경에서 사용할 수 없습니다.

## 모듈 상태 분류

| 상태 | 설명 | 예시 |
|------|------|------|
| ✅ Implemented | 완전히 구현됨 | 실제 모델, API 연동 완료 |
| ⚠️ Partial | 부분 구현 | 일부 기능만 작동, 의존성 문제 |
| ❌ Mock Only | 데모용 가짜 구현 | SHA256 기반 결정적 휴리스틱, 실제 모델 없음 |
| ❌ Missing | 구현되지 않음 | 파일 자체 없음 |
| ❌ Planned | 계획됨 | 아직 시작되지 않음 |

## 상세 모듈 목록

### 🔬 AI/ML 모듈

| 모듈 | 상태 | 설명 | 실행 방법 | 주의사항 |
|------|------|------|----------|----------|
| **Latent Diffusion Model** | ❌ Mock Only | SHA256 기반 안정적 점수 생성 | `python3 arp_v21_orchestrator.py --disease alzheimer` | 실제 diffusion 모델 없음, deterministic heuristic |
| **TFBindFormer Integration** | ❌ Mock Only | SHA256 기반 안정적 점수 생성 | `python3 arp_v21_orchestrator.py --disease alzheimer` | 실제 ESM-2/Foldseek 모델 없음, deterministic heuristic |
| **Neuroprotective Plants** | ⚠️ Heuristic | 커리에이션된 8개 화합물 | `python3 neuroprotective_plants_integration.py` | 지식베이스 유효, provenance 필드 추가됨 |

### 🧪 파이프라인 모듈

| 모듈 | 상태 | 설명 | 실행 방법 | 주의사항 |
|------|------|------|----------|----------|
| **ARP v21 Orchestrator** | ✅ Available | Mock 오케스트레이션 | `python3 arp_v21_orchestrator.py --disease alzheimer --output results/` | manifest/report 출력 지원 |
| **Database Integration** | ❌ Not Working | API 키 필요 | 외부 의존성 문제 | ChEMBL, DrugBank 등 접근 불가 |
| **3D Structure Analysis** | ❌ Not Implemented | 구현 안 됨 | 없음 | AlphaFold/FlashBind 없음 |
| **ADMET Prediction** | ❌ Not Implemented | 구현 안 됨 | 없음 | ADMETlab API 연동 없음 |

### 📊 재현성 상태

| 모듈 | Deterministic | Seed 필요 | 비고 |
|------|---------------|-----------|------|
| **Latent Diffusion** | ✅ Yes | No | SHA256 기반, 입력 문자열만으로 결정적 |
| **TFBindFormer** | ✅ Yes | No | SHA256 기반, 입력 문자열만으로 결정적 |
| **Neuroprotective** | ✅ Yes | No | 커리레이션 데이터, 항상 결정적 |
| **Orchestrator** | ⚠️ Partial | Optional | 일부 numpy operations에 seed 적용 |

### 📋 Known Issues

1. **Real mode 미구현**: 모든 ML 모듈에서 real inference 불가
2. **External APIs**: Database, ADMET, 구조 분석 API 연동 안 됨
3. **Placeholder DOIs**: 일부 참조가 실제 논문이 아님
4. **Limited Disease Coverage**: alzheimer, sarcopenia, masld만 지원

## 실행 가능한 명령

### 현재 실행 가능 (데모용)
```bash
# ✅ 오케스트레이터로 실행 (권장)
python3 arp_v21_orchestrator.py --disease alzheimer --mode mock --output results/

# ✅ 개별 모듈 실행
python3 latent_diffusion_integration.py -d alzheimer -o test_results/
python3 neuroprotective_plants_integration.py -d alzheimer -o test_results/

# ✅ 재현 가능한 실행
python3 arp_v21_orchestrator.py --disease alzheimer --mode mock --seed 42 --output results/
```

### 실행 불가 (의존성 문제)
```bash
# ❌ 불가 - 엔트리포인트 없음 (이전 버전)
python3 arp_v20_full_integration.py

# ❌ 불가 - API 키 필요
python3 database_integration.py --disease alzheimer

# ❌ 불가 - 모델 파일 없음
python3 structure_analysis.py --compound "CC(=O)Oc1ccc..."
```

## 개선 로드맵

### 단기 목표 (1-2주)
- [x] 엔트리포인트 생성 (`arp_v21_orchestrator.py`)
- [x] Mock mode 명시적 분리
- [x] SHA256 기반 deterministic scoring
- [x] 재현성 metadata 추가
- [ ] 실제 모델 API 연동 시작

### 중기 목표 (1-2개월)
- [ ] 외부 API (ChEMBL, ADMETlab) 연동
- [ ] 데이터베이스 접근성 확보
- [ ] 더 많은 질병 지원 추가
- [ ] 테스트 케이스 보강

### 장기 목표 (3-6개월)
- [ ] 실제 ML 모델 통합 (TFBindFormer, Latent Diffusion)
- [ ] 성능 벤치마크 수립
- [ ] 과학적 검증 완료

---

*생성일: 2026-04-14*
*최종 업데이트: 2026-04-14*
*상태: Research Prototype - Not Production Ready*