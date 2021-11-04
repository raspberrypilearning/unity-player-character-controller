Select your player GameObject and choose 'Add Cmponent' in the Inspector and add a 'Character Controller'.

![The Animator component in the Inspector window with 'IdleWalk' populated.](images/animator-component.png)

Adjust the collider settings so that the collider is same height as the player and Y center is half that height. Adjust the radius so that the collider covers your player. 

The 'Character Controller' component adds the `SimpleMove` method which you will need to call from `Update` on a script attached to the Player. 

Click 'Add Component' then 'New script'. Name the script 'SimpleController' (or use a name specific to your character such as 'SnowmanController'.)

![The Script component in the Inspector window with 'Player Controller' script populated.](images/snowman-controller.png)

Click on the Script in the Inspector to find it in the Project window then open the script in your Code Editor. 

Add code to move your character based on keyboard input. 

```
public class SimpleController : MonoBehaviour
{
    public float moveSpeed = 3.0F; // default move speed
    public float rotateSpeed = 3.0F; // default rotate speed

    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        CharacterController controller = GetComponent<CharacterController>();
        transform.Rotate(0, Input.GetAxis("Horizontal") * rotateSpeed, 0);
        Vector3 forward = transform.TransformDirection(Vector3.forward);
        float speed = moveSpeed * Input.GetAxis("Vertical");
        controller.SimpleMove(forward * speed);
    }
}
```

