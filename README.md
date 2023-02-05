# athena
Athema System for electrical index

@startuml

skinparam component {
    FontColor          black
    AttributeFontColor black
    FontSize           17
    AttributeFontSize  15
    AttributeFontname  Droid Sans Mono
    BackgroundColor    #6A9EFF
    BorderColor        black
    ArrowColor         #222266
}

title "Athena System"
skinparam componentStyle uml2

cloud {
    actor "User" as user
    component "Pegasus" as pegasus
    queue "queue" as queue
    component "Draco" as draco
    component "Cygnus" as cygnus
    component "Andromeda" as andromeda
    database "database" as database
    component "phoenix" as phoenix

    user .right.> pegasus 
    pegasus .down.> queue : 1. produce fotos
    
    queue .left.> draco : 2. consume fotos
    queue <.left. draco : 3. produce numbers

    queue .right.> cygnus : 4. consume numbers
    
    cygnus .down.> database : 5. store numbers
  
    andromeda .right.> database : 6. consume monthly numbers
    andromeda .up.> pegasus : 7. produce and send report
  
    database .up.> phoenix : 8. poll monthly numbers
    phoenix .up.> pegasus : 9. notify for fotos
  
}

@enduml
