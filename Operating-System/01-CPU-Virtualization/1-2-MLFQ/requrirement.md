## Multi Level Feedback Queue

### 목표

CPU 스케줄링 알고리즘 중 Multi Level Feedback Queue를 구현하고,
Multi Level Feedback Queue 를 최적화하기 위한 방법에 대해서 생각한다.

### 요구 사항

- [ ] MLFQ 알고리즘을 구현한다.
- [ ] 구현된 알고리즘의 성능을 다음 지표에 따라 분석한다.
  > `turnaround time`, `response time`, `fairness`

#### 보너스 요구 사항

- [ ] MLFQ 에서 Fairness 문제를 해결하기 위하여 `Priority Boost` 동작을 구현한다.
- [ ] MLFQ 의 time slice 기반 방식의 문제점이 무엇이 있는지 생각해보고, 이를 해결하기 위한 방법을 구현한다.
- [ ] 각 큐들의 우선순위에 따라 다른 time slice 값을 가지도록 한다.
