# Learning-Project-Game-Simulation


int heroHealth = 20;    
int monsterHealth = 20; 

Random roll = new Random(); 
Random critChance = new Random();   

do
{
    int heroBaseDamage = roll.Next(1, 6);   
    int monsterBaseDamage = roll.Next(1, 6);    
    int critHit = critChance.Next(1, 16);   
    int heroCritDamage = heroBaseDamage * 2;    
    int monsterCritDamage = monsterBaseDamage * 2;  

    if (monsterHealth > 0)
    {
        if (critHit == 15)
            {
                monsterHealth = monsterHealth -= heroCritDamage;
                Console.WriteLine(monsterHealth > 0 ? $"Hero crit and did {heroCritDamage} damage! Monster has {monsterHealth} HP left!" : $"Hero crit and did {heroCritDamage} damage! Monster has {monsterHealth} HP and is dead!");
            }
        else
        {
                monsterHealth = monsterHealth -= heroBaseDamage;
                Console.WriteLine(monsterHealth > 0 ? $"Hero did {heroBaseDamage} damage! Monster has {monsterHealth} HP left!" : $"Hero did {heroBaseDamage} damage! Monster has {monsterHealth} HP and is dead!");
        }
        if (monsterHealth <= 0) break;
    }

    if (heroHealth > 0)
    {
        if (critHit == 15)
        {
            heroHealth = heroHealth -= monsterCritDamage;
            Console.WriteLine(heroHealth > 0 ? $"Monster Crit and did {monsterCritDamage} damage! Hero has {heroHealth} HP left!" : $"Monster crit and did {monsterCritDamage} damage! Hero has {heroHealth} and is dead!");
        }
        else
        {
            heroHealth = (heroHealth -= monsterBaseDamage);
            Console.WriteLine(heroHealth > 0 ? $"Monster did {monsterBaseDamage} damage! Hero has {heroHealth} HP left!": $"Monster did {monsterBaseDamage} damage! Hero has {heroHealth} HP and is dead!");
        }
        if (heroHealth <= 0) break;
    }

} while ((heroHealth > 0) && (monsterHealth > 0));  

Console.WriteLine(heroHealth > monsterHealth ? "Hero wins!" : "Monster wins!");
