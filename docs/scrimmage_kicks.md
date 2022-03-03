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

## Beispiele

### Redding Study Guide 11-87

A's Punt überquert die Neutrale Zone. A34 begeht eine Touching Violation. B23 recovert den Ball und läuft bis an B's 35, wo er fumbelt. Während dieses Laufes schlug B92 einen Gegenspieler an B's 32. A42 recovert den Ball und läft damit,  
(a) bis an B's 5, wo er getackelt wird.  
(b) bis in B's Endzone für einen Touchdown.  

#### a - Lauf endet an B's 5
```mermaid
sequenceDiagram
    participant KICK
    participant NZ as BALL ÜBERQUERT NZ
    participant KICKENDE
    participant BFUMBLE as B Fumble @ B's 35
    participant BALLDEAD as B's 5
    KICK->>KICKENDE: Punt
    note right of NZ: Illegal Touching "TV"
    KICKENDE->>BFUMBLE: B Lauf
    note right of KICKENDE: B92 schlägt A15 an B's 32
    BFUMBLE->>BALLDEAD: A Lauf
```

#### b - Lauf endet in B's Endzone

```mermaid
sequenceDiagram
    participant KICK
    participant NZ as BALL ÜBERQUERT NZ
    participant KICKENDE
    participant BFUMBLE as B Fumble @ B's 35
    participant BALLDEAD as B's Endzone
    KICK->>KICKENDE: Punt
    note right of NZ: Illegal Touching "TV"
    KICKENDE->>BFUMBLE: B Lauf
    note right of KICKENDE: B92 schlägt A15 an B's 32
    BFUMBLE->>BALLDEAD: A Lauf
```


##### Regelung:  
Unter (a) kann Team A den Ball nicht bekoomen. Lehnt A die Strafe für das persönliche Foul ab, bekommt Team B den Ball am Punkt der Touching Violation. Nimmt A die Strafe an, wird die Touching Violation aufgehoben. Die Strafdurchführung gibt jedoch B den Ball, weil B zum Zeitpunkt des Fouls in Ballbesitz war. Die Strafe wird nach dem 3-und-1 Prinzip vom Punkt des Fouls durchgeführt, da das Foul hinter dem Basic Spot (Ende von B's Lauf) stattfand.  
Unter (b) belibt der Touchdown bestehen. Die Stafe für Team B's Foul wird beim Try oder anschließenden Succeeding Spot geahndet.

#### Redding Study Guide 11-88

A's Punt überquert die Neutrale Zone. A34 begeht eine Touching Violation. B23 recovert den Ball und läuft bis an B's 35, wo er fumbelt. Während dieses Laufes hielt  B92 einen Gegenspieler. A42 recovert den Ball und läft damit,  
(a) bis an B's 5, wo er getackelt wird.  
(b) bis in B's Endzone für einen Touchdown.  

#### Diagramm
```mermaid
sequenceDiagram
    participant KICK
    participant NZ as BALL ÜBERQUERT NZ
    participant KICKENDE
    participant BFUMBLE as B Fumble @ B's 35
    participant BALLDEAD as B's 5
    participant BENDZONE
    KICK->>KICKENDE: Punt
    note right of NZ: Illegal Touching "TV"
    KICKENDE->>BFUMBLE: B Lauf
    note right of KICKENDE: B92 hält einen Gegenspieler
    BFUMBLE->>BALLDEAD: (a) A Lauf endet im Spielfeld
    BFUMBLE->>BENDZONE: (b) A Lauf endet in B's Endzone
```


##### Regelung:  
Unter (a) ist die Regelung dieselbe wie oben unter 11-87. A kann den Ball nicht behalten. Team B bekommt den Ball entweder durch die Touching Violation (wenn Strafe abgelehnt) oder nach Durchführung der Strafe für das eigene Foul ...
Unter (b) **zählt der Touchdown in diesem Fall nicht**, da es während des Downs eine Touching Violation gab und diese die Strafdurchführung möglich ermöglicht. Die Strafe wird nicht durch die Regel aufgehoben. Team A kann wählen Team B den Ball entweder am Punkt der Touching Violation zu geben oder an dem Punkt an den der Ball durch die Strafdurchführung kommt.
