# 2023 학부 RA활동 - 장철희

이 레포지토리는 클라우드 보안 연구실(CCLAB)에서 학부 연구생으로 활동하며 학습하고 연구한 내용을 정리한 것입니다.

## 목차
### [1. Docker](./Docker.md)
- 컨테이너 기술의 기본 개념
- Docker 아키텍처와 내부 동작 원리
- 컨테이너 보안 메커니즘

### [2. containerd](./containerd.md)
- 컨테이너 런타임의 이해
- containerd 아키텍처
- OCI 표준과의 관계

### [3. Kubernetes](./Kubernetes.md)
- 컨테이너 오케스트레이션
- 쿠버네티스 보안 구성요소

### [4. Seccomp & eBPF](./seccomp.md)
- 시스템 콜 필터링
- eBPF 기반 모니터링 및 보안

### [+) eBPF summit](./eBPFsummit.md)
- eBPF 기술 동향
- 최신 활용 사례

## eBPF 개발 가이드

### 개발 프로세스
eBPF 프로그램은 기본적으로 C 언어로 작성되며, 다음과 같은 단계로 개발됩니다:
1. 컴파일
2. 로드
3. 유저 애플리케이션과 통신

### 주요 개발 도구

#### libbpf
- C 언어 기반 eBPF 프로그램 개발 라이브러리
- [libbpf GitHub](https://github.com/libbpf/libbpf)
- 초기 개발시 libbpf 레포지토리의 bootstrap 예제 참고 권장

#### BCC (BPF Compiler Collection)
- Python 인터페이스를 통한 eBPF 프로그램 관리
- [iovisor/bcc](https://github.com/iovisor/bcc/tree/master)

#### eunomia-bpf
- eBPF 프로그램 개발 간소화 도구
- [튜토리얼](https://eunomia.dev/tutorials/0-introduce/)

## 추가 참고자료

### eBPF 맵 & 커널 문서
- [Prototype Kernel/docs-eBPF Maps](https://prototype-kernel.readthedocs.io/en/latest/bpf/ebpf_maps.html)
  - eBPF 맵 사용법에 대한 간략한 가이드
- [Linux Kernel - bpf](https://docs.kernel.org/bpf/index.html)
- [LSM BPF Programs](https://docs.kernel.org/bpf/prog_lsm.html)
  - BPF의 심층적 이해를 위한 공식 커널 문서

### 실제 구현 사례
- [KubeArmor-bpf](https://github.com/kubearmor/KubeArmor/tree/main/KubeArmor/BPF)
  - 실제 프로덕션 환경의 eBPF 구현 예시
  - 레퍼런스 코드로 활용 가능

## 학습 로드맵
1. 목차의 내용을 순차적으로 학습
2. Linux Kernel BPF 문서를 통한 심화 학습
3. 실제 프로젝트 분석 (KubeArmor 등)
4. eBPF 프로그램 개발 실습