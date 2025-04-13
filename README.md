# tcp-port-test
with httpx client

감정분석 서비스의 비동기 처리에 따른 port exhaustion문제 해결을 위한 테스트 레포

openai 라이브러리는 default는 timeout 600, connection = 5 \n
httpx.Timeout(timeout=600, connect=5.0)

connection pool limit은 1000개, 100개, 5초 expiry \n
httpx.Limits(max_connections=1000, max_keepalive_connections=100)

EC2 Linux Default Ephemeral Port는 기본값, 32768~61000
time_wait은 2msl(1~2분)...

공부한 내용 : keep-alive 헤더는 hop by hop 적용인데 만약 방화벽이 프록시 역할을 수행한다면 헤더 값을 처리할 수 있나?

즉 클라이언트 - 방화벽 간의 connection 헤더가 아닌 proxy - connection 타입으로 보내야 기대한 대로 작동할 수 있는지..?
