# Coding Challenge - Hotel Transsilvanien

Imagine you're a hotel manager of a Hotel with an X amount of rooms.
Some rooms are occupied and others are free or reserved, but either dirty or clean.
Represented as following JSON:
```
[
    {
        "roomNumber":1,
        "isOccupied":true,
        "occupiedUntil":987,
        "isReserved":true,
        "hasToBeCleaned":true,
        "cleaningDuration":418
    },...
]
```

## Create a Solution that will read the current state of the hotel and instruct your cleaning crew so that they clean the hotel.
 * Do not clean rooms as long as they are occupied.
 * Reserved rooms that need cleaning has to be cleaned first, so the next guess don't have to wait for his room any longer.
 * Consider that some rooms will be free again after some time and these rooms maybe has to be cleaned as well.
    - If the residents will not leave, occupiedUntil = -1
    - If that room is also reserved it has to be cleaned earlier.

 #### Winner is which manager who can clean the given hotel the fastest and cost-efficient.
