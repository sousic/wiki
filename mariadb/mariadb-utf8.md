MariaDB Encoding Type 확인하기
==========================


마지막 수정일
==========
2016-11-16




DB Character 타입 확인하기 쿼리
===========================
show variables like 'c%'


확인이 필요한 문자열 인코딩 설정 타입
============================
    'character_set_database','utf8'
    'character_set_database','utf8'
    'collation_database', 'utf8_general_ci'
    'collation_server', 'utf8_general_ci'

