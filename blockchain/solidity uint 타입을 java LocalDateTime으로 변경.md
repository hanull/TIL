## 배경

```solidity
contract {
    struct DID {
        string faceFileUrl;
        string voiceNo;
        uint256 expiryDate;
    }
}
```

컨트랙트에 만료일을 나타내는 expiryDate를 만들어 배포하였다. 단, Solidity에는 날짜 형식의 타입이 없기 때문에 uint256 형식으로 저장해야한다. 

그리고 이 컨트랙트를 java에서 조회하여여현재 날짜(now()) 와 비교하려고 했다. 

하지만, 형식이 맞지 않아서 오류가 발생했다. 


## 이유

solidity의 uint256은 Java에서 BigInteger 형식으로 받게 되고, 이를 현재 시간을 나타내는 LocalDateTime 형식과 비교하기 때문에 에러가 발생한 것이다.

## 해결 방법

```java
BigInteger bigIntegerExpiryTime = (BigInteger) ethereumCallResult.get(2).getValue();
LocalDateTime expiryTime = LocalDateTime.ofInstant(Instant.ofEpochSecond(bigIntegerExpiryTime.longValue()),
        TimeZone.getDefault().toZoneId());
```