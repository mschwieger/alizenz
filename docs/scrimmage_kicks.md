# Scrimmage Kicks

## Diagramme

### Teamballbesitz während eines Scrimmage Kick Downs

- kein Schnickschnack
- keine Violation
- Team B am Ende des Downs im Ballbesitz

```mermaid
sequenceDiagram
    participant PREDEAD as BALL DEAD
    participant SNAP
    participant KICK
    participant NZ as KICK ÜBERQUERT NZ
    participant KICKENDE
    participant BALLDEAD as BALL DEAD
    PREDEAD ->> NZ: TEAM A
    NZ ->> BALLDEAD: TEAM B
```


### Phasen eines Scrimmage Kick Downs

```mermaid
sequenceDiagram
    participant PREDEAD as BALL DEAD
    participant SNAP
    participant KICK
    participant NZ as KICK ÜBERQUERT NZ
    participant KICKENDE
    participant BALL DEAD
    PREDEAD->>SNAP: PRE-SNAP
    SNAP->>KICK: PRE-KICK
    KICK->>KICKENDE: POST-KICK
    NZ->>KICKENDE: POST-POSSESSION
    par Team B
    note over KICKENDE: B erlangt Ballbesitz
    KICKENDE->>BALL DEAD: RETURN
    note over KICKENDE,BALL DEAD: FAIR CATCH = LAUF für 0 Sek und 0 m
    and Team A
    note over KICKENDE: A erlangt Ballbesitz 
    KICKENDE->>BALL DEAD: Ball sofort dead   
    end
```
### Status des Balles während Scrimmage Kick Downs

```mermaid
sequenceDiagram
    participant PREDEAD as BALL DEAD
    participant SNAP
    participant KICK
    participant NZ as KICK ÜBERQUERT NZ
    participant KICKENDE
    
    participant BALL DEAD
    PREDEAD->>SNAP: DEAD
    SNAP->>KICK: LAUF
    KICK->>KICKENDE: KICK

    par Team B
    KICKENDE->>BALL DEAD: LAUF
    note over KICKENDE,BALL DEAD: RETURN
    note over KICKENDE,BALL DEAD: FAIR CATCH = RETURN für 0 Sek und 0 m
    and Team A
    KICKENDE->>BALL DEAD: A erlangt Ballbesitz 
    note over KICKENDE,BALL DEAD: Ball sofort dead   
    end

```

### Team A Fouls

``` mermaid
sequenceDiagram
    participant PREDEAD as BALL DEAD
    participant SNAP
    participant KICK
    participant NZ as BALL ÜBERQUERT NZ
    participant KICKENDE
    participant BALLDEAD as BALL DEAD
    par
    note over PREDEAD,SNAP: Team A Presnap Fouls
    PREDEAD ->> SNAP: Succeeding Spot 
    and
    note over SNAP: Team A Fouls beim SNAP
    SNAP->>BALLDEAD: Können auf Team B's Dead Ball enforced werden.
    and
    note over SNAP,KICKENDE: Team A Fouls vor Kickende
    SNAP->>BALLDEAD: Können auf Team B's Dead Ball enforced werden.
    and
    note over NZ,KICKENDE: BFK ist Spotfoul
    end
```

### zu viel in einer Grafik


``` mermaid
sequenceDiagram 
    Dead->>+Snap: 
    Snap->>Lauf A: 
    Lauf A->>Kick: mit Kick wird Lauf zum Teil des SK Spiels
    Kick->>Kickende: überquert neutrale Zone 
    Kickende->>Lauf B: es muss kein Lauf folgen
    rect rgb(200, 150, 255)
    note over Dead,Snap: Fouls vor dem  Snap
    note over Snap: Fouls beim Snap
    end
    note over Snap,Kick: Team A Fouls können auf B's Dead Ball übertragen werden
    note over Snap,Kick: Team B Fouls - Previous Spot 
    note over Snap,Kickende: Scrimmage Kick Spiel
    note over Kick,Kickende: PSK Fenster
    note over Snap,Kick: Teamballbesitz A
    note over Kick,Lauf B: Teamballbesitz B
```

