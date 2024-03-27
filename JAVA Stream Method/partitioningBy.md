### partitioningBy?
---
**partitioningBy** 메서드는 자바 8부터 도입된 스트림(Stream) API의 기능 중 하나로, 요소들을 지정한 조건에 따라 두 그룹으로 분할합니다. 조건에 맞는 요소들과 그렇지 않은 요소들을 각각 리스트로 반환하여 처리할 수 있습니다

**장점**
**partitioningBy** 메서드를 사용하면 데이터를 두 그룹으로 쉽게 분할할 수 있어 다양한 상황에서 유용합니다. 예를 들어, 참/거짓 또는 짝수/홀수와 같이 두 가지로 분류할 때 매우 편리하게 사용할 수 있습니다.

_코드 예제

```
@Getter  
@AllArgsConstructor  
public static class MemberResponse {  
    private String name;  
    private Integer no;  
}  
  
@Test  
void partitionByMemberNo() {  
    List<MemberResponse> members = createMembers(100);  
    Map<Boolean, List<MemberResponse>> memberMap = partitionBy(members, 20);  
  
    assertThat(memberMap.get(true).size()).isEqualTo(80);  
}  
  
private List<MemberResponse> createMembers(int count) {  
    return IntStream.rangeClosed(1, count)  
            .mapToObj(i -> new MemberResponse("name" + i, i))  
            .collect(Collectors.toList());  
}  
  
private Map<Boolean, List<MemberResponse>> partitionBy(List<MemberResponse> members, Integer no) {  
    return members.stream()  
            .collect(Collectors.partitioningBy(member -> member.getNo() > no));  
}
```

`partitionBy` 메서드는 전달받은 회원 리스트를 스트림으로 변환한 후, 각 회원의 번호가 인자로 전달된 no보다 큰지 여부에 따라 두 그룹으로 분할합니다. 이때, 번호가 인자로 전달된 no보다 큰 경우는 `true` 그룹으로, 그렇지 않은 경우는 `false` 그룹으로 분류됩니다





