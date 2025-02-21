## 🚀 기능 요구 사항

레벨 2의 팀 프로젝트 미션으로 SNS(Social Networking Service)를 만들고자 하는 팀이 있다. 팀에 속한 크루 중 평소 알고리즘에 관심이 많은 미스터코는 친구 추천 알고리즘을 구현하고자 아래와 같은 규칙을 세웠다.

- 사용자와 함께 아는 친구의 수 = 10점 
- 사용자의 타임 라인에 방문한 횟수 = 1점

사용자 아이디 user와 친구 관계 정보 friends, 사용자 타임 라인 방문 기록 visitors가 매개변수로 주어질 때, 미스터코의 친구 추천 규칙에 따라 점수가 가장 높은 순으로 정렬하여 최대 5명을 return 하도록 solution 메서드를 완성하라. 이때 추천 점수가 0점인 경우 추천하지 않으며, 추천 점수가 같은 경우는 이름순으로 정렬한다.

### 제한사항

- user는 길이가 1 이상 30 이하인 문자열이다.
- friends는 길이가 1 이상 10,000 이하인 리스트/배열이다.
- friends의 각 원소는 길이가 2인 리스트/배열로 [아이디 A, 아이디 B] 순으로 들어있다.
  - A와 B는 친구라는 의미이다.
  - 아이디는 길이가 1 이상 30 이하인 문자열이다.
- visitors는 길이가 0 이상 10,000 이하인 리스트/배열이다.
- 사용자 아이디는 알파벳 소문자로만 이루어져 있다.
- 동일한 친구 관계가 중복해서 주어지지 않는다.
- 추천할 친구가 없는 경우는 주어지지 않는다.

### 실행 결과 예시

| user | friends | visitors | result |
| --- | --- | --- | --- |
| "mrko" | [ ["donut", "andole"], ["donut", "jun"], ["donut", "mrko"], ["shakevan", "andole"], ["shakevan", "jun"], ["shakevan", "mrko"] ] | ["bedi", "bedi", "donut", "bedi", "shakevan"] | ["andole", "jun", "bedi"] |
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#풀이 과정
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
friends에 있는 친구 관계를 이용해 해쉬맵 점수판, 여러 리스트와 메서드들을 만들어 줬습니다.

  + score_board = 점수판(해쉬맵)
    + create_score_board()메서드를 이용

  + my_friend = 내 친구들을 모아놓은 리스트
    + create_my_friend() 메서드를 이용

  + my_friend_friend = 내 친구의 친구들(유저 제외)을 모아놓은 리스트
    + friends에서 내 친구가 포함된(유저는 제외) 배열을 구해줌

  + dont_know_list = 모르는 사람 리스트 
    + 점수판의 키 값이 내 친구 리스트에 있으면 지워줌

이후 점수판에 내 친구의 친구에게는 +10점을, 방문자에 있는 사람들은 +1점을 해주었습니다. 이후 점수판에서 유저의 친구를 삭제, 점수기준 -> 이름 순서로 정렬, 5명이상이라면 5명 순서대로 반환을 해줄 수 있게 해주었습니다.

  
  
