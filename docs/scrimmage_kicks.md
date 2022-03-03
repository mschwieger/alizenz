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
    note over SNAP,KICKENDE: Team A Fouls vor Kickende
    SNAP->>BALLDEAD: Können auf Team B's Dead Ball enforced werden
    KICKENDE-->>SNAP: oder Previous Spot
    and
    note right of NZ: BFK ist Spotfoul
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

## Post Scrimmage Kick Enforcement

#### Artikel 3. Postscrimmage Kick Enforcement

a) Gemäß den Postscrimmage Kick Enforcement Regeln werden Team B-Fouls, die die unter Regel 10-2-3b aufgeführten Bedingungen erfüllen, behandelt, als wäre Team B zum Zeitpunkt, als das Foul verursacht wurde, in Ballbesitz gewesen, obwohl der Team Ballbesitz gemäß Regel 2-4-1b-3 nicht gewechselt hat.
b) Postscrimmage Kick Enforcement trifft nur auf Team B-Fouls während eines Scrimmage Kicks und nur unter den nachfolgend aufgeführten Bedingungen zu:
    1. DerKickwirdnichtwährendeinesTry,eineserfolgreichenFieldgoals oder in einer Extraperiode durchgeführt (A.R. 10-2-3-IV).
    2. Der Ball überquert die neutrale Zone.
    3. Das Foul ereignet sich, bevor der Kick endet (A.R. 10-2-3-I, -II und -V).
    4. Team B wird als nächstes den Ball ins Spiel bringen. 
Wenn diese Bedingungen alle zutreffen, wird die Strafe nach dem Drei-und-Eins-Prinzip durchgeführt. Team B wird als das Team in Ballbesitz betrachtet mit dem       Postscrimmage Kick Spot als Basic Spot (Regel 10-2-2-c). Siehe Regel 2-25-11 für den Postscrimmage Kick Spot (A.R. 10-2-3-I-VII).
