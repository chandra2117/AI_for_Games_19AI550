# Ex.No: 10  Implementation of 2D/3D game Coin Collection Game
### DATE: 31/05/2026                                                                           
### REGISTER NUMBER : 212223240019
### AIM: 
To develop a 2D Coin Collection Game using Unity where the player collects coins to increase the score, and a "Level Finished" message is displayed when all coins are collected.
### Algorithm:
```
Create a new 2D Unity project.
Add a Ground GameObject with a BoxCollider2D.
Add a Player GameObject with Rigidbody2D and BoxCollider2D.
Create a Coin GameObject and add a CircleCollider2D with "Is Trigger" enabled.
Create multiple coin instances and place them at different positions.
Create and attach a PlayerMovement script to control player movement using keyboard input.
Create and attach a CoinScript to detect coin collection.
Create a UI Text object to display the score.
Create a ScoreManager script to update the score and display it on the screen.
Create a FinishText UI object and disable it initially.
When the player collects a coin, increase the score and destroy the coin.
Check whether all coins have been collected.
If all coins are collected, display the "LEVEL FINISHED!" message.
Run the game and verify the score and level completion functionality.
```  
### Program:
#### playermovement.cs
```
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float speed = 5f;

    void Update()
    {
        float move = Input.GetAxis("Horizontal");
        transform.Translate(Vector2.right * move * speed * Time.deltaTime);
    }
}
```
#### coinscript.cs
```
using UnityEngine;

public class CoinScript : MonoBehaviour
{
    private void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.CompareTag("Player"))
        {
            ScoreManager.score++;
            Destroy(gameObject);
        }
    }
}
```
#### ScoreManager.cs
```
using UnityEngine;
using TMPro;

public class ScoreManager : MonoBehaviour
{
    public static int score = 0;

    public TextMeshProUGUI scoreText;
    public GameObject finishText;

    public int totalCoins = 5;

    void Update()
    {
        scoreText.text = "Score : " + score;

        if (score >= totalCoins)
        {
            finishText.SetActive(true);
            Time.timeScale = 0;
        }
    }
}
```
### Output:
<br>
<img width="1920" height="1020" alt="Screenshot 2026-06-01 085052" src="https://github.com/user-attachments/assets/4b9bbcc1-9785-4f01-99e8-7a3051a024ec" />
<br><br>

### Result:
Thus, the Coin Collection Game was successfully developed and executed using Unity.
