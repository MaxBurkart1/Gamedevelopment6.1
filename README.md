# Mini-level — Inleveren

**Naam:** Max Burkart
**Klas:** 4m3
**Datum:** 26-10-2026
**Les:** GDV Les 6

## Wat heb ik gemaakt?
Ik heb een mini leveltje gemaakt waar je twee sleutels moet pakken om twee deuren te openen. Alleen om te kunnen komen naar die sleutels moet je door rode obstacles heen. Als je een van deze obstacles aanraakt gaat de obstacle weg en word je terug naar start geteleport. Dus hoe meer je probeert hoe makkelijker de level word.

## Screenshot / GIF van je level
 

## Bewegend object
De object die beweegt is de grijze bal in het midden wat namelijk de player is. Hij beweegt met WASD.

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
positie.x = positie.x + snelheid * Time.deltaTime; 
}

if (Input.GetKey(KeyCode.D))
{
positie.x = positie.x - snelheid * Time.deltaTime; 
}

transform.position = positie;
}

## Collider of trigger
Ik heb een OnTriggerEnter gebruikt waarbij als je een sleutel aanraakt dan krijg je een variable genaamd “haskey”. Ik heb ook een tweede sleutel met “haskey2”
Daarna heb ik een OnCollisionEnter voor de deur waar als je het aanraakt zonder de sleutel aangeraakt te hebben blokkeert het je. Maar als je de sleutel aan heb geraakt de gaat de deur weg op aanraking.

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
    

 ## Logica met if of switch
Ik heb if statements gemaakt voor het bewegen waar als je een knopje klikt gaat een code gebeuren met de if statement waarmee je beweegt.

// Plak hier het stuk code met jouw if- of switch-logica.
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
positie.x = positie.x + snelheid * Time.deltaTime; 
}

if (Input.GetKey(KeyCode.D))
{
positie.x = positie.x - snelheid * Time.deltaTime; 
}


 ## Eigen extra idee
Ik weet niet of dit telt maar de concept van een tweede sleutel hebben vanplaats van 1 sleutel is nieuw.

### Wat ging goed? en waarom?
Het maken van de level zelf waar je doorheen moet zien te komen

### Wat vond je lastig? en waarom?
De code maken van dat als ik een sleutel aanraak en dan de deur dat de deur dan weg gaat dat werkte nooit.

### Wat zou je een volgende keer anders doen?
Niks, want ik deed mijn uiterste best.
