# Learning-Project-Game-Simulation
int heroHP = 10;
int monsterHP = 10;

Random roll = new Random();
Random critChance = new Random();
Random healChance = new Random();

do
{
int attack = 0;
int heal = 0;
    if (monsterHP > 0)
        {
            int critHit = critChance.Next(1, 16);
            monsterHP -= (critHit == 15 ? (attack = roll.Next(1, 11) + 5) : (attack = roll.Next(1, 11)));
            Console.WriteLine(critHit == 15 ? $"Hero Crit for {attack} damage! Monster has {monsterHP} health left!": $"Hero did {attack} damage! Monster has {monsterHP} HP left!");
            if (monsterHP <= 0) break; 
        }
    if (heroHP > 0)
        {
            int critHit = critChance.Next(1, 16);
            heroHP -= (critHit == 15 ? (attack = roll.Next(1, 11) + 5) : (attack = roll.Next(1, 11)));
            Console.WriteLine(critHit == 15 ? $"Monster crit for {attack} damage! Hero has {heroHP} health left!": $"Monster did {attack} damage! Hero has {heroHP} HP left!");
            if (heroHP <= 0) break;
        }
    if (heroHP < 10)
    {
        heal = healChance.Next(1, 5);
        heroHP += (heal == 4 ? (4) : 0);
        if (heroHP > 10) {heroHP = 10;}
        if (heal == 4) {Console.WriteLine($"Hero healed for 4 health! Hero now has {heroHP} HP!");}
    }
    if (monsterHP < 10)
    {
        heal = healChance.Next(1, 4);
        monsterHP += (heal == 3 ? (4): 0);
        if (monsterHP > 10) {monsterHP = 10;}
        if (heal == 3) {Console.WriteLine($"Monster healed for 4 health! Monster now has {monsterHP} HP!");}
    }
} while (heroHP > 0 && monsterHP > 0);

 Console.WriteLine(heroHP > monsterHP ? "Hero wins!" : "Monster wins!");
