## Memory Virtualizatoin Basic (Address Space)

### 목표

`base-bound register` 기반으로 가상 메모리 (Address space)가 실제 메모리 (Physical Memory) 에 올라갈 때,
운영체제가 어떤 방식으로 동작을 수행하는지 이해한다.

### 요구 사항

- 프로그램은 `Operating System (Kernel)`, `Process (Address Space)` 의 두 객체의 동작으로 이루어진다. 각 클래스의 네이밍은 같은 의미 내에서 자유롭게 지정한다.

> physical memory의 경우, **슬롯 단위로 나뉘어져 있다고 가정**한다.
> 따라서, 어떤 주소 공간을 physical memory에 적재할 때, alignment를 맞춘다고 가정한다.

#### Operating System (Kernel)

- [ ] field

  > - `base register`, `bound-register` : **현재 실행 하고 있는** 프로세스에 관한 정보
  > - `PCB (process control block)` : 메모리에 올라와 있는 프로세스들
  >   - `pid`, `base register`, `bound register`
  > - `empty space info` : physical memory 의 빈 공간을 저장하고 있는 리스트
  >   - 현재 사용중이지 않은 physical memory의 slot의 index를 저장한다.
  >   - 어떤 Process가 시스템에 추가되거나, 삭제될 때 해당 리스트는 업데이트 된다.
  > - `Physical memory` : 현재 관리하고 있는 physical memory의 상태를 의미한다. (후술)

- [ ] method

  > - `addProcess` : 프로세스를 메모리에 적재한다.
  > - `deleteProcess` : 프로세스가 종료되고, 사용하고 있던 메모리를 해제한다.
  > - `allocateMemory` : 프로세스에 메모리를 할당해준다.
  >   - 이 때, 할당 방식의 경우 `best-fit`, `worst-fit`, `first-fit` 의 경우를 나누어서 구현한다.
  > - `contextSwitch` : 현재 실행되고 있는 프로세스의 정보를 변경한다.
  > - `scanPhysicalMemory` : physical memory의 상태를 확인하고, `empty space info` 를 업데이트 한다.

- **Physical memory**

  > 실제 물리 메모리 그 자체라기 보단, 운영체제가 관리하고 있는 물리 메모리 상태를 의미한다.

  - [ ] field

    > - `slot size` : physical memory의 한 슬롯의 사이즈를 의미한다.
    > - `total memory size` : 총 메모리 크기를 의미한다.
    > - `slot status array` : 현재 슬롯의 상태 (할당 되었음 (`true`), 할당되지 않았음 (`false`))
    > - `empty space size` : 빈 공간의 크기를 의미한다. **여기에서는 내부 단편화는 고려하지 않는다.**

#### Process (Address Space)

- [ ] field

  > - `pid`
  > - `total size`

### 보너스 요구 사항

- [ ] `Process (Address Space)`를 `code`, `data`, `heap`, `stack` 영역으로 나누어 구현해보세요.
