# Mechanics

## Combat Statistics
- If your AV is 19, the lowest AC that you can hit is -1 with a 5% chance.
- If your AC is 11, the highest AV that can hit you is 30 with a 5% chance.
- If a PC and NPC 1v1 with 1HP and 19AV 11AC, PC has a 57% chance to win. (or more precisely, 56.686%)
    - These are not amazing odds for fighting, if you consider that your character must survive essentially an unlimited amount of fights.
    - YABEC does not do anything about these odds, meaning death is always near and a very real threat. However, death in YABEC is purely an inconvenience, which incentivizes careful styles of play. The following combat reworks are meant to keep fighting risky and exciting, but not unreasonable so to encourage a more aggressive style of play.
    - Oh by the way here's the math.
### Math
```
1: 1/36
2: 2/36
3: 3/36
4: 4/36
5: 5/36
6: 6/36
```
- 7/12 chance (58.3%) for PC to go first
```
19AV -> 11AC: 8 or higher wins (65%)
11AC <- 19AV: 9 or higher loses (60%)
If nobody wins, the game resets identically

In 100 games:
65 games PC wins immediately
35 games NPC has a chance to win
and in 60% of those 35 games (21 games) NPC wins

The rest of the 14 games go back to the original odds, and therefore can be ignored
so in 65/(100-14) games (65/86 = 0.7558) PC wins
and in 21/(100-14) games (21/86 = 0.2442) NPC wins
```
- 5/12 chance (41.7%) for NPC to go first
```
11AC <- 19AV: 9 or higher loses (60%)
19AV -> 11AC: 8 or higher wins (65%)
If nobody wins, the game resets identically

In 100 games:
60 games NPC wins immediately
40 games PC has a chance to win
and in 65% of those 40 games (26 games) PC wins

The rest of the 14 games go back to the original odds, and therefore can be ignored
so in 60/(100-14) games (60/86 = 0.6977) NPC wins
and in 26/(100-14) games (26/86 = 0.3023) PC wins
```
- If PC goes first (~60% chance), roughly 75% chance they win
- If PC goes second (~40% chance), roughly 70% chance they lose
```
0.6*0.75 = 0.45
0.4*0.3 = 0.12
0.45 + 0.12 = 0.57
```

## Initiative
- There are three ways to initiate combat: random, surprise, and duel.
    - A random encounter works like YABEC: both sides roll, and whichever side rolls the highest number goes first. After both sides have concluded all their actions, both roll again.
    - Surprise encouters are granted if one side gets the jump on the other. The side that surprised the other gets a free round of attacks on the other, after which combat proceeds as random.
    - A duel occurs if both sides agree to a duel. In a duel, the person who offered the duel always goes first, and turns alternate in that order without further rolls.

## Morale
- When half (rounded down) of the enemies on the other side die, they will be forced to check their morale. Morale is a 50/50, where failure means either an attempt to flee or surrender.

## Party Scaling
- Enemies will always have the same AV, AC, and HD (hit die, essentially the floor and ceiling of their HP), but their health and number will differ depending on the size of the party attacking them.
- ***P*** represents the number of people in the party, and encounter tables may use this value.
- Example: if an encounter says that you encounter `1 + 0-1*P` enemies, then one enemy will be in the encounter, and for each PC in the party there is a 50% chance that another enemy will be in that encounter.

## AV damage scaling
- Damage increases/decreases from having a low or high AV have been removed.

## Attributes and Abilities
- Enemies have certain tendencies during battle, or skills granted to them by their training or equipment.
- If an ability cannot be found in the ability list, it is probably a class specific ability.

### Attribute List:
- `Alpha:` All enemies of the same race and alignment, including this one, become `Valiant`. When the last `Alpha` enemy falls, all other enemies instantly fail morale.
- `Cowardly:` This enemy will independently fail a morale checks.
- `Cruel:` This enemy will always attack a bloodied opponent if there is one.
- `Dextrous:` This enemy rolls advantage on all Stunts.
- `Inexperienced:` This enemy will never attack a bloodied opponent.
- `Slow:` This enemy has a charge attack. On the turn before it unleashes this attack, it will set its sights on an opponent, and if that opponent is still in range by the next turn, they will be hit.
- `Valiant:` This enemy will independently succeed any morale checks.
- `Merciful:` This enemy will never attack a near-death opponent.
- `Minion:` This enemy will be considered defeated when its master is defeated.

### Ability List
- `Spiky Body (dN):` Upon a successful melee attack, there is a 50% chance to take 1dN of damage due to the enemy's spiky exterior. This cannot put you near death.
- `Charm Creature:`
- `Poisonous Touch (dN):` Upon hitting someone, have them make a physical save. If failed, they are mundanely poisoned, taking 1dN damage per dungeon turn and whenever do an attack or Stunt until they are cured.
- `Command Vermin:` Charm HD/Lv small rodents and pests within 50 feet to do your bidding next round. If used in an area without rodents or pests, this does nothing.
- `Swarm:` If 3 enemies with the `Swarm` ability attack the same enemy, they gain +1 damage and -2 AV.
