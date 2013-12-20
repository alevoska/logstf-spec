Logs.tf Additional Stats
========================

Damage with target, including headshot and airshot
--------
    [[attacker]] triggered "damage" against [[victim]] (damage "0") (realdamage "0") (weapon "shotgun_soldier") (healing "15") (crit "crit|mini") (airshot "1") (headshot "1")

Notice that *realdamage*, *healing*, *crit*, *headshot* and *airshot* are not always present.

When *realdamage* is missing, then *damage* = *realdamage*

*crit* can take the values: crit, mini

Charge with medigun type
--------
    [[player]] triggered "chargedeployed" (medigun "medigun|kritzkrieg|quickfix|vaccinator|unknown")

*medigun* can take the values: medigun, kritzkrieg, quickfix, vaccinator, unknown

Medkit pickup with real healing amount
--------
    [[player]] picked up item "medkit_x" (healing "0")


Medic stats
--------

**These log lines are already implemented in the MedicStats plugin:**

    [[player]] triggered "first_heal_after_spawn" (time "3.4")

Is triggered when the medic heals for the first time after spawning. It is _not_ triggered at the beginning of the round.

    [[player]] triggered "chargeready"

Is triggered when the medic has 100% charge.

    [[player]] triggered "medic_death_ex" (uberpct "98")

Is triggered when the medic dies. Note that the normal `medic_death` is still triggered.

    [[player]] triggered "empty_uber"

Is triggered when the medic spawns, and also after the medic's charge has been used and is at 0%. Can be used to calculate the time it takes to build uber (the time between `empty_uber` and `chargeready`).


    [[player]] triggered "chargeended" (duration "%.1f")

Is triggered when the medic's charge has ended (went from 100% to 0%). It is not triggered if the medic is killed while using uber. The `duration` indicates how long the uber lasted.

    [[player]] triggered "lost_uber_advantage" (time "12")

Is triggered when the medic had an uber advantage of at least 10 seconds. The `time` parameter tells how much of an advantage they had.


***Note: I am planning on adding `medigun` property to all of the above***


----------

----------

----------
**The ones below are not finalized yet:**



Weapon stats
--------
    [[player]] triggered "weaponstats" (weapon "weapon") (shots "0") (hits "0") (kills "0") (damage "0")

Timing for dumping these stats is implementation-specific.

[Old SuperLogs implementation of weaponstats][1]

  [1]: https://bitbucket.org/psychonic/hlstatsxce-extras/src/41700689e004d6f9c5fdad9a08431b6ba03958aa/SuperLogs/scripting/superlogs-tf2.sp?at=trunk#cl-1345