---
copyright:
  years: 2016,2018
lastupdated: "2018-06-12"
---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 아키텍처 
{: #architecture}

## 복제

{{site.data.keyword.composeForPostgreSQL_full}} 서비스에는 데이터 멤버가 두 개(리더와 팔로워 멤버) 있는 클러스터가 포함되어 있습니다. 데이터는 두 데이터 멤버 전체에서 복제되며 해당 디스크 공간은 영역의 가용성 영역에 분산됩니다. 고가용성은 Patroni를 사용하여 관리합니다. 여기에서는 세 개의 etcd 조정자가 클러스터 상태를 유지보수하 복제를 관리하며 장애 복구를 처리합니다. 한 데이터 멤버에 연결할 수 없게 되어도 클러스터는 계속 정상적으로 작동합니다.

## 디스크 암호화

모든 {{site.data.keyword.composeForPostgreSQL}} 서비스의 암호화는 사용되지 않습니다. 데이터는 볼륨 레벨 암호화가 사용된 서버에 있습니다. 

{{site.data.keyword.composeForPostgreSQL}}은 관리 서비스이므로 {{site.data.keyword.cloud}} Compose 운영자가 데이터를 볼 수 있습니다. 디스크 암호화 외에도, 데이터베이스에 저장하기 전에 개인 정보를 암호화하거나, 데이터베이스 자체에서 암호화를 사용하는 기능 또는 확장기능을 사용하는 것이 좋습니다. 해당 메소드는 사용성이나 성능에 영향을 미칠 수 있지만 암호화를 통해 개인 정보를 보호하는 것이 좋습니다.

## Auto-Scaling

리소스는 PostgreSQL 데이터베이스의 총 디스크 스토리지 사용을 기반으로 자동으로 스케일링됩니다. 메모리는 1:4로 프로비저닝된 디스크 공간의 비율을 기반으로 합니다. 해당 리소스는 단위로 번들됩니다.

Auto-Scaling은 데이터베이스의 중단기 상태동향에 대응하도록 설계되었습니다. 매시간 서비스를 확인하고 디스크 공간이 부족하면 더 많은 단위가 배치에 할당됩니다. 

Auto-Scaling에서는 디스크/메모리 사용량이 줄어든 배치의 스케일은 줄이지 않습니다. 데이터베이스에 프로비저닝된 리소스는 나중에 필요한 경우를 대비하여 그대로 남아 있거나 배치의 스케일을 수동으로 축소할 때까지 그대로 남아 있습니다.
{: .tip}

## 역할

모든 PostgreSQL 서비스는 "관리자" 역할로 프로비저닝합니다. 기타 역할과 권한은 psql을 통해 추가하고 관리할 수 있습니다. 이 서비스의 "수퍼유저" 역할은 없습니다.

## 데이터베이스 확장기능

psql을 사용하여 PostgreSQL 확장기능을 나열, 설치 및 관리할 수 있습니다.

제공된 "관리자" 역할을 사용하여 CREATE 및 ALTER 명령을 실행해야 합니다.{: .tip}

### 확장기능 나열

pg_available_extensions를 사용하여 지원되는 확장기능의 전체 목록을 가져오십시오.
`SELECT name FROM pg_available_extensions;`

### 확장기능 설치

CREATE 확장기능을 사용하여 확장기능을 설치하십시오.
`CREATE extension <name> ;`

### 확장기능 업데이트

ALTER EXTENSION을 사용하여 새 버전의 확장기능을 설치하십시오.
`ALTER EXTENSION <name> UPDATE TO <version>;`
