# Open_SoftWare_GradeServer
##2015 오픈소프트 개발자 대회 출품작 -GradeServer

### GradeServer란?
프로그래밍 공부를 위해 알고리즘 문제를 제공하는 사이트들을 많이 이용하실 겁니다. 바로 그런 알고리즘 채점 사이트를 간단하게 개설 할 수 있도록 만든 것이 저희의 GradeServer입니다.

현재 프로그래밍을 교육하고 있는 많은 교육기관에서 학생들에게 알고리즘 문제를 과제로 내주고 싶어도 채점의 여러움으로 하지 못하는 경우가 많습니다. 그렇다고 해서 많은 사람들이 사용하는 일반 알고리즘 채점 사이트들을 이용하기에는 불편함이 적지 않습니다.

저희 GradeServer는 문제들을 해결할 수 있도록 교육기관에서 간단하게 직접 서버를 운영할 수 있도록 도와줄 것이며, 그것의 저희의 목표입니다.


### 사용 전 유의사항
현재 make 파일은 파이썬으로 만들어졌으며, redhat계열의 리눅스에서만 사용이 가능합니다. 조만간 ubuntu계열의 리눅스 환경에서도 사용이 가능하도록 하겠습니다.


### 제약 사항
GradeServer를 실행하기 전 redis와 DB를 먼저 실행해야 합니다.

DB의 경우 mysql과 MariaDB만 지원하고 있으며, DB는 character set을 utf8로 먼저 설정해 주시는게 좋습니다.

redis의 port번호는 기본값인 6379로 해야합니다. 이는 추후 설정 파일을 추가하여 원하는 port번호를 설정 가능하도록 하겠습니다.


### 사용방법
1. 사용자 계정에 대하여 sudo 접근 비밀번호를 해제한다.
   (sudo visudo를 수정)
2. repository에 있는 모든 파일을 다운 받는다..
3. sudo 권한으로 make파일을 실행합니다. make 파일을 python으로 만들어졌으며, python make.py로 실행한다.
   docker image파일 생성까지 진행하기 때문에 상당시간 소요될 수 있음.
4. 설치가 완료되면 sudo 권한으로 runserver를 실행한다. 실행 시 DB 사용자 이름과 비밀번호를 순서대로 함께 입력한다.
   ex) python runserver.py serverId pw1234
5. celeryServer폴더에 들어가 일반 사용자 권한으로 celery서버를 실행한다.
   (celery -A celeryServer worker -l info --concurrency=1)
6. 서버는 Ctrl+C를 눌러 종료한다.


### 권장 시스템 사양
운영체제 : centOS(추후 ubuntu 지원) - Windows에선 사용 불가.

최소사양 : CPU 2.0GHz 3core, RAM 2GB, HDD 8GB

권장사양 : CPU 2.7GHz 4core, RAM 3GB, HDD 10GB 이상
