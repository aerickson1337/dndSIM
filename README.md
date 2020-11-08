# dndML
combat simulator that uses machine learning and graphs to do combat simulations

# high level overview todo

# path to simulating fights, basic calculation requirements
Vacuum calculation inputs e.g.
- intended fight duration = rounds
- monster effective hp = party mean DPR * rounds
- monster target DPR = total party hp / rounds
    - attacks should try to not exceed party mean hp in damage, 
    to avoid one shots. do this through multiple small attacks or aoe abilities.

# Advanced calculations needed
- bonus action attacks / special attacks
- status effects and disables
- healing
- downed -> death 
- healing from downed / death
- battlefield decision making
- spells / aoe
- target choice

# Considerations needed for advanced calculations and simulating them
- bonus action attacks / special attacks
in a simulation this shouldn't be too hard to work with, is more difficult to deal with in a flat calculation DPR change since fight will be warped by length in that instance.
- status effects / disables
also should be easier to calculate during simulations since they scale with fight length as long as abilities are tracked properly.
- healing / downed healing
healing on a turn can be abstracted to a DPR reduction on that round if the heal is large enough, considerations for downed healing aka 5e'ing should be accounted for by the simulations if the abusability of the rule is encoded properly.
- battlefield decision making
using a graph with edges of different lengths make this easier to do than trying to simulate with a grid and calculations on it. E.g. a mage casts fireball at a specific location. Traversing the edges of the target location can be used to determine if target is within the AoE without needing to draw a grid. This also lends itself to calculating positions, e.g. movement distance, being able to attack, range etc all while abstracting the grid (and more importantly the calculations) itself.
- spells / aoe
Can be calculated using edge length from above graph descrption
- target choice
battle field layout and a way to determine overall threat to victory vs squishyness level. 

