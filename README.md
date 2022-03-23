# jjyygo
Go engin impl with different languages.

## play sequence

```mermaid
sequenceDiagram
PlayerBlack->>Board: create
Board->>Board: init
PlayerWhite->>Board: join
Board->>Board: even & start
loop play
  PlayerBlack->>Board: move/pass/resign
  Board->>Board: check
  PlayerWhite->>Board: move/pass/resign
  Board->>Board: check
end
Note right of Board: both pass or any resign, loop end
Board->>Board: judge
Board->>Board: end
```

## check flow
```mermaid
flowchart LR
S((start)) --> checkIllegal{is illegal?}
checkIllegal --> |Yes|E((end))
checkIllegal --> |No|changeState[change state]
changeState --> needTake{need take?}
needTake --> |No|E
needTake --> |Yes|take{take}
take --> E
```
## check illegal
```mermaid
flowchart LR
S((start))--> isEmpty{is empty?}
isEmpty --> |No| Illegal((illegal))
isEmpty --> |Yes| isLastKo{is last ko?}
isLastKo --> |Yes| Illegal
isLastKo --> |No| isDie{is die?}
isDie --> |Yes| canTake{can take?}
canTake --> |No| Illegal
canTake --> |Yes| take[take]
take --> legal
isDie --> |No| legal((legal))
```
