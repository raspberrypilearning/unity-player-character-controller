Selecteer je Player GameObject en kies **Add Component** in de Inspector en voeg een **Character Controller** toe.

![De Character Controller component in het Inspector venster.](images/character-component.png)

Pas de collider-instellingen aan zodat de collider dezelfde hoogte heeft als de Speler en de Center y waarde de helft is van de hoogte. Pas de radius aan zodat de collider je speler bedekt.

De Character Controller-component voegt de `SimpleMove`-methode toe, die je moet aanroepen vanaf `Update` op een script dat aan de speler is gekoppeld.

Klik op **Add Component** en vervolgens op **New script**. Geef het script de naam `SimpleController` (of gebruik een naam die specifiek is voor je personage zoals `SnowmanController`.)

![De Script-component in het Inspector-venster met ingevuld 'Player Controller'-script.](images/snowman-controller.png)

Klik op het script in de Inspector om het te vinden in het projectvenster, open vervolgens het script in je Code Editor.

Voeg code toe om je personage te laten bewegen op basis van toetsenbordinvoer.


--- code ---
---
language: cs
filename: SimpleController.cs
line_numbers: false
---
public class SimpleController : MonoBehaviour
{
    public float bewegingssnelheid = 3.0f; // Standaard bewegingssnelheid
    public float draaisnelheid = 3.0f; // Standaard rotatie snelheid

    // Start wordt aangeroepen vóór de eerste frame-update
    void Start()
    {
        
    }

    // Update wordt één keer per frame aangeroepen
    void Update()
    {
        // Voeg hier indien nodig de speleranimatiecode toe
        
        // Code om de speler te laten bewegen
        CharacterController controller = GetComponent<CharacterController>();
        transform.Rotate(0, Input.GetAxis("Horizontal") * draaisnelheid, 0);
        Vector3 forward = transform.TransformDirection(Vector3.forward);
        float snelheid = bewegingssnelheid * Input.GetAxis("Vertical");
        controller.SimpleMove(forward * snelheid);
    }
}
--- /code ---

