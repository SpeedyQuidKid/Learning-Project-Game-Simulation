# Learning-Project-Game-Simulation
int hero = 10;  
int monster = 10;   

Random critHit = new Random();  
Random roll = new Random();     

do      
{   
int attack = 0;     
        if (monster > 0)     
            {   
                int critDamage = critHit.Next(1, 15);   
                attack = (critDamage == 3 ? (roll.Next(1, 11) * 2) : (roll.Next(1, 11)));   
                if (critDamage == 3) {Console.WriteLine("Hero crit!");}     
                monster -= attack;  
                Console.WriteLine(monster > 0 ? $"Hero did {attack} damage! Monster has {monster} HP left!" : $"Hero did {attack} damage and monster is dead! {monster}");  
            }       
        if (monster <= 0) break;       
        if (hero > 0)   
            {   
                int critDamage = critHit.Next(1, 15);   
                attack = (critDamage == 2 ? (roll.Next(1, 11) * 2) : (roll.Next(1, 11)));   
                   if (critDamage == 2) {Console.WriteLine("Monster crit!");}  
                hero -= attack;     
                Console.WriteLine(hero > 0 ? $"Monster did {attack} damage! Hero has {hero} HP left!" : $"Monster did {attack} damage and hero is dead! {hero}");   
        }    
        if (hero <= 0) break;   
} while (hero > 0 && monster > 0);  

Console.WriteLine(hero > monster ? "Hero wins!" : "Monster wins!"); 
