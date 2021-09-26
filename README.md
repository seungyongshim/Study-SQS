## SQS와 다른 서비스 조합
Amazon SQS 메시지 대기열 서비스를 Redshift, DynamoDB, RDS, EC2, ECS, Lambda 및 S3 등 다른 AWS 서비스와 함께 사용하면 분산 애플리케이션의 안정성과 확장성을 더욱 향상할 수 있습니다. 몇 가지 일반 설계 패턴은 다음과 같습니다.
- 작업 대기열: 동일한 양의 작업 일부를 동시에 처리하지 못할 수 있는 분산 애플리케이션의 구성 요소를 분리합니다.
- 버퍼 및 일괄 작업: 아키텍처에 확장성과 안정성을 더하고, 메시지를 손실하거나 지연 시간을 늘리지 않고 일시적인 볼륨 스파이크를 원활하게 처리합니다.
- 요청 분산: 요청을 전송하여 대화식 요청 경로에서 속도가 느린 작업을 제거합니다.
- 팬아웃: SQS를 Simple Notification Service(SNS)와 결합하여 메시지의 동일한 사본을 여러 대기열에 병렬로 전송합니다.
- 우선순위: 별도의 대기열을 사용하여 작업의 우선순위를 지정합니다.
- 확장성: 메시지 대기열에서 프로세스를 분리하므로, 다른 프로세스를 추가하기만 하면 손쉽게 메시지 송신이나 수신 속도를 높일 수 있습니다. 
- 복원력: 시스템 일부에 장애가 발생하더라도 전체 시스템에는 영향을 주지 않습니다. 메시지 대기열에서 시스템의 구성 요소를 분리하므로 대기열에서 메시지를 읽어오는 프로세스가 실패한 경우에도, 시스템이 복구되면 처리되도록 메시지를 대기열에 추가할 수 있습니다.

## 1. 자습서
- [분산 애플리케이션 간에 메시지 전송](https://aws.amazon.com/ko/getting-started/hands-on/send-messages-distributed-applications/)
- [팬아웃 이벤트 알림 전송](https://aws.amazon.com/ko/getting-started/hands-on/send-fanout-event-notifications/)

## 2. 개발자 가이드
- https://docs.aws.amazon.com/sns/latest/dg/welcome.html

## 3. kafka와 차이점
- Queue는 단일 목적을 가진 소비자를 위해 존재
   - RabbitMQ와 유사
- 여러 Queue에 Fanout해야 하는 경우 AWS SNS을 사용
   - RabbitMQ의 Exchange와 유사

