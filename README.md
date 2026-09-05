# linux-practice

> Ubuntu Linux 환경에서의 기초 명령어 습득부터 디렉터리·파일 제어, DNS 네트워크 구조, 텍스트 파이프라인, 셸 스크립트 작성, 디스크 마운트, 사용자 및 그룹 관리, 프로세스 제어까지의 실습 및 이론을 기록하는 저장소입니다.

---

## 1. 사용 환경 (Environment)

* **OS**: Ubuntu Linux
* **Hypervisor**: VMware Workstation

---

## 2. 학습 목차 및 내용 요약 (Learning Index)

| 일차 | 주제 | 주요 학습 내용 및 명령어 | 경로 (Path) |
| :---: | :--- | :--- | :--- |
| **Day 01** | Linux 기초 명령어 및 시스템 제어 | 파일 탐색(`ls`, `pwd`, `cd`), 시스템 종료 및 재부팅(`init`, `shutdown`, `reboot`, `poweroff`) | [`basic/day01_linux.md`](./basic/day01_linux.md) |
| **Day 02** | 디렉터리 및 파일 제어 | 폴더 및 파일 생성·삭제(`mkdir`, `touch`, `rm`), 텍스트 편집(`nano`), 화면 정리(`clear`) | [`file/day02_file_linux.md`](./file/day02_file_linux.md) |
| **Day 03** | 네트워크 기초 (DNS와 네임 서버) | 도메인-IP 변환 원리, Hosts 파일 참조 우선순위, DNS 캐시 및 계층적 조회 과정 | [`network/day03_DNS_basics.md`](./network/day03_DNS_basics.md) |
| **Day 04** | 텍스트 파일 처리 및 파이프라인 | 텍스트 출력 및 탐색(`cat`, `head`, `tail`, `more`, `less`), 파이프(`\|`) 및 리다이렉션(`>`) | [`text/day04_text_commands.md`](./text/day04_text_commands.md) |
| **Day 05** | 셸 스크립트 작성 및 실행 권한 | 스크립트 기본 구조(`#!/bin/sh`), 환경 변수(`$USER`, `$HOME`), 실행 권한 부여(`chmod +x`) | [`shell_script/day05_user_info.md`](./shell_script/day05_user_info.md) |
| **Day 06** | 디스크 관리 및 마운트 기초 | 장치 마운트 원리(`mount`, `umount`), 용량 확인(`df -h`), 계정 관리(`useradd`), 명령어 별칭(`alias`) | [`basic/day06_basic_disk.md`](./basic/day06_basic_disk.md) |
| **Day 06** | 프로세스 제어 및 작업 관리 | 프로세스 조회(`ps aux`, `pstree`), 백그라운드 전환(`jobs`, `bg`, `fg`), 강제 종료(`kill -9`) | [`process/day06_process_management.md`](./process/day06_process_management.md) |
| **Day 07** | 사용자 및 그룹 관리 | 사용자 계정 관리(`adduser`, `passwd`, `usermod`, `userdel`), 그룹 관리(`groups`, `groupadd`, `groupmod`, `groupdel`, `gpasswd`), 사용자 및 그룹 정보 파일(`/etc/passwd`, `/etc/shadow`, `/etc/group`), 파일 허가권과 소유권  파일 정보 확인(`ls -l`), 권한 구조(`r`, `w`, `x`), 허가권 변경(`chmod`), 소유자 변경(`chown`), 그룹 변경(`chgrp`) | [`user_permission/day07_user_and_group_management.md`](./user_permission/day07_user_and_group_management.md) [`user_permission/day07_file_permissions_ownership.md`](./user_permission/day07_file_permissions_ownership.md) |
| **Day 08** | Linux 사용자 권한, 파일 구조 및 기본 명령어 | 관리자 권한(`sudo`, `su`, `sudo -i`), 파일 종류, Ubuntu 디렉터리 구조, 절대·상대 경로, 숨김 파일, 기본 명령어(`mkdir`, `rmdir`, `ls`, `man`) | [`basic/day08_files_paths_commands.md`](./basic/day08_files_paths_commands.md) |
| **DAY 09** | Linux 패키지 및 파일 관리 | 패키지 관리(`apt`, `dpkg`), 명령어 경로 확인(`which`), 파일 복사·이동·삭제(`cp`, `mv`, `rm`), 압축 및 해제(`zip`, `unzip`) | [`file/day05_package-and-file-management.md`](./file/day09_package_and_file_management.md) |

---

## 3. 저장소 폴더 구조 (Directory Structure)

```text
linux-practice/
├── basic/              # Linux 기초 명령어, 사용자 계정 및 디스크/마운트 관리
│   ├── day01_linux.md
│   └── day08-linux-files-paths-commands.md
├── file/               # 파일 및 디렉터리 생성·삭제·수정 명령어
├── network/            # DNS, 네임 서버 및 네트워크 기초 개념
├── process/            # 프로세스 상태 조회, 백그라운드 작업 및 시그널 제어
├── project/            # Linux 관련 실습 프로젝트 및 응용
├── shell_script/       # 셸 스크립트 작성 및 실행 권한 설정
├── text/               # 텍스트 출력, 검색 및 파이프라인 연산자 활용
├── user_permission/    # 사용자 권한 및 소유권 관리
├── Learning-Log.md     # 1~8일차 전체 학습 종합 분석 및 문제 해결 일지
└── README.md           # 저장소 개요 및 학습 목차
```

---

## 4. 목표 및 향후 계획 (Goals & Roadmap)

* **단기 목표**: Linux 환경에서 서버를 직접 구축하고, 지속적으로 운영하며 외부로 배포하는 전 과정을 익힙니다.

* **중장기 목표**:
  * **배포 자동화**: 소스 코드의 수정 및 적용 과정을 자동화하여 효율적으로 서버에 반영하는 환경을 구성합니다.
  * **가상화 기술 적용**: 다양한 서비스 환경을 독립적으로 구성하고 효율적으로 관리할 수 있도록 가상화 기술을 학습하고 적용합니다.

---

## 5. 상세 학습 일지 안내 (Learning Log)

일차별 상세 개념 원리, 실습 코드 해석, 막혔던 점과 해결 내용, 그리고 종합 회고는 **[`Learning-Log.md`](./Learning-Log.md)** 파일에 정리되어 있습니다.