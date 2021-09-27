# H Index
## 지문
H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과1에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.

제한사항
과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
논문별 인용 횟수는 0회 이상 10,000회 이하입니다.
입출력 예
citations	return
[3, 0, 6, 1, 5]	3
입출력 예 설명
이 과학자가 발표한 논문의 수는 5편이고, 그중 3편의 논문은 3회 이상 인용되었습니다. 그리고 나머지 2편의 논문은 3회 이하 인용되었기 때문에 이 과학자의 H-Index는 3입니다.
## 정리
1. h번 이상 인용이 된 논문의 편 수가 h 이상이고, 나머지 논문이 h편 이하인 값이 H-Index이다.
2. 이 H-Index의 최대값을 구해라.
## 소스코드
```javascript
function solution(citations) {
    const max = Math.max.apply(null, citations);
    const result = [];
    for (let h = 0; h <= max; h += 1) {
        const upper = [...citations].filter((citation) => citation >= h);
        if ((h <= upper.length) && (h >= (citations.length - upper.length))) result.push(h);
    }
    const arr = result.sort((a, b) => b - a );
    return arr[0] || 0;
}
```
## 시도 방법
1. 인용 횟수 중 가장 큰 값을 구한다.
2. 해당 횟수만큼 반복문을 돌려서 h를 1씩 증가시키며 인용 횟수가 h 이상인 논문을 찾는다.
3. 인용 횟수가 h 이상인 논문이 h편 이상 있고, 나머지 논문들이 h편 이하라면 해당 h를 배열에 넣는다.
4. 결과 배열을 정렬하여 첫번째 아이템을 불러온다.
## 최초 소요시간
약 2시간
