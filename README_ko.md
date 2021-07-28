# 와.. 챗봇 API

[English](README.md)

[한국어](README_ko.md)

## Before Usage

본 챗봇은 개발자(yymin1022)와 지인들이 평소에 주로 하는 대화 ~~헛소리~~ 를 대신 해주는 봇을 개발하고자 기획되었습니다. 챗봇의 언행이 일반인이 이해하기에는 다소 난해할 수 ~~어질어질할 수~~ 있으니 활용에 참고해주시기 바랍니다.

## Install

```
git clone https://github.com/yymin1022/Wa_API.git
chmod +x Wa_API/*.sh
./setupServer.sh
```

---

## Requirements

```Ubuntu 20.04 LTS amd64``` 에서 테스트 되었습니다.

다른 플랫폼에서 이용하고자 할 경우 수정이 필요할 수 있습니다.

```setupServer.sh``` 를 이용해 설치할 경우, 아래 Requirements들은 자동으로 설치 및 설정됩니다.

```
sudo apt install apache2 libapache2-mod-wsgi-py3 python3 python3-pip python3-flask
sudo python3 -m pip install flask requests
```

---

## Run

```setupServer.sh``` 를 이용해 설치할 경우, Apach2 서비스가 자동으로 등록됩니다.

아래 명령을 이용해 서비스를 시작시킬 수 있습니다.

```
service apache2 start
/etc/init.d/apache2 start
```

---

## How To Use

```http://localhost:port``` 로 POST Restful 데이터셋을 전송합니다.

서버에 API 요청을 하는 경우 포맷은 다음과 같습니다.

```
{
    "msg": "와..",
    "room": "채팅방 1",
    "sender": "yymin1022"
}
```

|Variable|Data Type|Data Content|
|---|---|---|
|msg|String|메시지 내용|
|room|String|채팅방 이름|
|sender|String|채팅 발화자|

---

서버의 API 반환 결과값은 다음과 같습니다.

```
{
    "RESULT": {
        "RESULT_CODE": 0,
        "RESULT_MSG": "RESULT OK"
        },
    "DATA": {
        "msg":"갑부;;",
        "room":"채팅방 1",
        "sender":"yymin1022"
        }
}
```

|Variable|Data Type|Data Content|
|---|---|---|
|RESULT_CODE|String|API 처리 결과 코드|
|RESULT_MSG|String|API 처리 결과 메시지|
|msg|String|메시지 내용|
|room|String|채팅방 이름|
|sender|String|채팅 발화자|

|API 처리 결과 코드||
|---|---|
|0|정상 처리|
|100|와..봇이 지원하지 않는 메시지|
|200|기타 오류(RESULT_MSG 참고)|

---

## API Instruction

아래 예시는 응답 가능한 메시지의 일부입니다.

모든 메시지 내용은 ```message.py``` 에서 확인하실 수 있습니다.

|Message Content|Reply|
|---|---|
|꺼라|전기세 아깝다ㅡㅡ;;|
|ㄹㅇㅋㅋ|ㄹㅇㅋㅋ|
|멈춰|멈춰!!|
|무야호|그만큼 신나신다는거지~|
|아..|글쿤.. / 그래요.. 등 8종|
|와..|갑부;; / 기만;; / ㄹㅇ;; 등 7종|
|와!|샌즈! 아시는구나! 이거 겁.나.어.렵.습.니.다.|
|응애|응애 나 애기 등 3종|
|이런..|안됐군요.. 등 2종|
|자라|전기세 아깝다ㅡㅡ;;|
|자야지|구라ㅡㅡ;;|
|^^7|^^7|

## Example

[CAU Meal Bot on Telegram](https://github.com/yymin1022/CAU_Meal_Bot_Telegram)

## Want Contribute?

봇 제작에 참여하고자 하시는 경우, ```message.py``` 를 참고해 코드를 작성하시고, ```Pull Request```를 올려주시면 주기적으로 확인하여 올바른지 검토한 뒤 ```Merge``` 해드립니다!