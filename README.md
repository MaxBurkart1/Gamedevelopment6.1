# Mini-level — Inleveren

**Naam:** Max Burkart  
**Klas:** 4m3  
**Datum:** 26-10-2026  
**Les:** GDV Les 6  

## Wat heb ik gemaakt?
Ik heb een mini-level gemaakt waarin je twee sleutels moet pakken om twee verschillende deuren te openen. Om bij de sleutels te komen, moet je door rode obstakels heen manoeuvreren. Als je een van deze obstakels aanraakt, verdwijnt het obstakel en word je direct terug naar de start geteleporteerd. Dit zorgt voor een uniek mechanisme: hoe vaker je het probeert, hoe makkelijker het level wordt!

## Screenshot / GIF van je level



## Bewegend object
Het object dat beweegt is de grijze bal in het midden, wat de speler is. De speler beweegt met de WASD-toetsen. 

*Verbeterde bewegingscode (de A-toets stuurt je nu netjes naar links en D naar rechts):*

```csharp
void Update() 
{
    Vector3 startpos = transform.position;
    Vector3 positie = transform.position;


    if (Input.GetKey(KeyCode.W))
    {
        positie.y = positie.y + snelheid * Time.deltaTime; 
    }

  
    if (Input.GetKey(KeyCode.S))
    {
        positie.y = positie.y - snelheid * Time.deltaTime; 
    }


    if (Input.GetKey(KeyCode.A))
    {
        positie.x = positie.x - snelheid * Time.deltaTime; 
    }


    if (Input.GetKey(KeyCode.D))
    {
        positie.x = positie.x + snelheid * Time.deltaTime; 
    }

    transform.position = positie;
}
```

## Collider of trigger
Ik heb een `OnTriggerEnter` gebruikt voor de sleutels. Als je een sleutel aanraakt, krijg je een variabele genaamd `haskey`. Ik heb ook een tweede sleutel toegevoegd die de variabele `haskey2` activeert.

Daarnaast gebruik ik een `OnCollisionEnter` voor de deuren. Als je de deur aanraakt zonder dat je de bijbehorende sleutel hebt opgepakt, blokkeert de deur je. Heb je de sleutel wel, dan verdwijnt de deur zodra je hem aanraakt.

```csharp
private void OnTriggerEnter(Collider other) 
{
    if (other.gameObject.CompareTag("Key"))
    {
        haskey = true;
        Destroy(other.gameObject);
    }
    
    if (other.gameObject.CompareTag("Key2"))
    {
        haskey2 = true;
        Destroy(other.gameObject);
    }
}

void OnCollisionEnter(Collision other)
{
    if (other.gameObject.CompareTag("Door") && haskey == true)
    {
        Destroy(other.gameObject);
    }
    
    if (other.gameObject.CompareTag("Door2") && haskey2 == true)
    {
        Destroy(other.gameObject);
    }
}
```

## Logica met if of switch
Ik heb `if`-statements gemaakt voor het bewegen. Als je een specifieke toets indrukt, wordt de code binnen het `if`-statement uitgevoerd waardoor de speler de juiste kant op beweegt.

```csharp
if (Input.GetKey(KeyCode.W))
{
    positie.y = positie.y + snelheid * Time.deltaTime; 
}

if (Input.GetKey(KeyCode.S))
{
    positie.y = positie.y - snelheid * Time.deltaTime; 
}

if (Input.GetKey(KeyCode.A))
{
    positie.x = positie.x - snelheid * Time.deltaTime; 
}

if (Input.GetKey(KeyCode.D))
{
    positie.x = positie.x + snelheid * Time.deltaTime; 
}
```

## Eigen extra idee
Het concept om twee verschillende sleutels te moeten zoeken in plaats van slechts één sleutel om het level uit te spelen.

### Wat ging goed? en waarom?
Het ontwerpen en bouwen van het level zelf waar de speler doorheen moet zien te komen.

### Wat vond je lastig? en waarom?
De code schrijven die controleert of je de sleutel hebt opgepakt voordat de deur verdwijnt. In het begin werkte de connectie tussen de sleutel en de deur namelijk niet meteen.

### Wat zou je een volgende keer anders doen?
Niks, want ik heb deze keer al mijn uiterste best gedaan.