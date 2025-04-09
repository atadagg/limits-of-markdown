# 🐾 Virtual Pet Game 🐾

Welcome to your virtual pet! Take care of your pet by feeding it, playing with it, and keeping it happy!

## Your Pet's Status

```<pre id="pet-art">
    /\___/\
   (  o o  )
   (  =^=  ) 
    (______)
</pre>```

**Pet Stats:**
- Happiness: <span id="happiness-meter">😊 😊 😊 😊 😊</span>
- Hunger: <span id="hunger-meter">🍖 🍖 🍖 🍖 🍖</span>
- Energy: <span id="energy-meter">⚡ ⚡ ⚡ ⚡ ⚡</span>

## Take Care of Your Pet

<form id="petForm">
  <h3>What would you like to do?</h3>
  
  <div>
    <input type="radio" id="feed" name="action" value="feed">
    <label for="feed">Feed Pet 🍖</label>
  </div>
  
  <div>
    <input type="radio" id="play" name="action" value="play">
    <label for="play">Play with Pet 🎾</label>
  </div>
  
  <div>
    <input type="radio" id="sleep" name="action" value="sleep">
    <label for="sleep">Let Pet Sleep 😴</label>
  </div>
  
  <button type="submit">Do Action!</button>
</form>

<div id="feedback-message" style="margin-top: 15px; font-weight: bold;"></div>

## Pet Gallery

Here are some cute moments with your pet:

![Pet Sleeping](https://placekitten.com/200/200)
![Pet Playing](https://placekitten.com/201/201)
![Pet Eating](https://placekitten.com/202/202)

## How to Play

1. Choose an action from the form above
2. Click "Do Action!" to perform the selected action
3. Watch your pet's stats change
4. Keep your pet happy and healthy!

## Tips
- Feed your pet when hunger is low
- Play when happiness is low
- Let your pet sleep when energy is low
- Balance all activities to keep your pet healthy!

---

*Note: This is a static demonstration. For a fully interactive version, you would need JavaScript to handle the form submissions and update the pet's stats.*

<script>
document.addEventListener('DOMContentLoaded', (event) => {
    // Game State
    let happiness = 5;
    let hunger = 5;
    let energy = 5;
    const maxStat = 5;

    // Pet Art Variations
    const petArtDefault = `
    /\\___/\\
   (  o o  )
   (  =^=  ) 
    (______)
    `;
    const petArtHappy = `
    /\\___/\\
   (  ^ ^  )
   (  =^=  ) 
    (______)
    `;
     const petArtSad = `
    /\\___/\\
   (  T T  )
   (  =^=  ) 
    (______)
    `;
    const petArtAsleep = `
    /\\___/\\
   (  - -  )
   (  =^=  ) zZz
    (______)
    `;
    const petArtEating = `
    /\\___/\\
   (  o o  )
   ( >~^~< ) 
    (______)
    `;
    const petArtPlaying = `
    /\\__/\\~~
   (  @ @  )
   \  =^=  /
    (______)
    `;

    // UI Elements
    const petArtElement = document.getElementById('pet-art');
    const happinessMeter = document.getElementById('happiness-meter');
    const hungerMeter = document.getElementById('hunger-meter');
    const energyMeter = document.getElementById('energy-meter');
    const petForm = document.getElementById('petForm');
    const feedbackMessage = document.getElementById('feedback-message');

    // Update UI Function
    function updateUI(art = petArtDefault, message = "") {
        // Update Stats Meters
        happinessMeter.textContent = '😊 '.repeat(happiness) + '⚪ '.repeat(maxStat - happiness);
        hungerMeter.textContent = '🍖 '.repeat(hunger) + '🦴 '.repeat(maxStat - hunger);
        energyMeter.textContent = '⚡ '.repeat(energy) + '▫️ '.repeat(maxStat - energy);
        
        // Update Pet Art
        petArtElement.textContent = art;

        // Update Feedback Message
        feedbackMessage.textContent = message;

        // Check game over state (optional)
        if (happiness <= 0 || hunger <= 0 || energy <= 0) {
             feedbackMessage.textContent = "Oh no! Your pet isn't feeling well. Game over!";
             petArtElement.textContent = petArtSad; // Show sad pet
             // Disable form? Or add reset?
             petForm.style.display = 'none'; // Hide form on game over
        }
    }

    // Action Functions
    function feedPet() {
        let message = "";
        let art = petArtEating;
        if (hunger < maxStat) {
            hunger = Math.min(maxStat, hunger + 2);
            happiness = Math.max(0, happiness - 1); // Eating isn't always fun
            energy = Math.max(0, energy - 1);
            message = "Yummy! Your pet enjoyed the meal.";
        } else {
            message = "Your pet is already full!";
            art = petArtDefault;
            happiness = Math.max(0, happiness - 1); // Annoyed if fed when full
        }
        updateUI(art, message);
        setTimeout(() => updateUI(), 1500); // Revert art after a delay
    }

    function playWithPet() {
        let message = "";
        let art = petArtPlaying;
        if (energy > 0) {
            happiness = Math.min(maxStat, happiness + 2);
            hunger = Math.max(0, hunger - 1);
            energy = Math.max(0, energy - 1);
            message = "Whee! That was fun!";
        } else {
             message = "Your pet is too tired to play.";
             art = petArtDefault;
        }
        updateUI(art, message);
        setTimeout(() => updateUI(), 1500); // Revert art after a delay
    }

    function letPetSleep() {
        let message = "";
        let art = petArtAsleep;
        if (energy < maxStat) {
            energy = Math.min(maxStat, energy + 3); // Sleep restores more energy
            hunger = Math.max(0, hunger - 1); // Gets hungry while sleeping
            happiness = Math.max(0, happiness -1) // Might get bored sleeping
            message = "Zzz... Your pet is resting.";
        } else {
            message = "Your pet is wide awake!";
            art = petArtDefault;
        }
        updateUI(art, message);
         // No timeout needed for sleep art unless you want it to wake up automatically
    }

    // Event Listener for Form Submission
    petForm.addEventListener('submit', function(e) {
        e.preventDefault(); // Prevent actual form submission
        const selectedAction = document.querySelector('input[name="action"]:checked');
        
        if (selectedAction) {
            const action = selectedAction.value;
            feedbackMessage.textContent = ""; // Clear previous message

            if (action === 'feed') {
                feedPet();
            } else if (action === 'play') {
                playWithPet();
            } else if (action === 'sleep') {
                letPetSleep();
            }
             // Uncheck the radio button for next time
            selectedAction.checked = false; 
        } else {
            feedbackMessage.textContent = "Please select an action first!";
        }
    });

    // Initial UI Update
    updateUI();
});
</script> 