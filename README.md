**Game Projects**

Welcome to my Game Projects repository! Here you will find a collection of games I have developed, showcasing my technical skills, architectural decisions, and design capabilities.

---

### Drift of Light

---

<img width="600" height="365" alt="Screenshot 2026-05-26 225341" src="https://github.com/user-attachments/assets/e11f8b93-d35a-4490-b182-f6bf1b682568" />

**Description**

"Drift of Light" is an infinite-runner survival drifting game set in a dark forest environment. It combines arcade-style car drifting physics with a unique survival mechanic: your car's headlights are your lifeline. The light constantly fades, and the only way to recharge it is by performing high-angle drifts. The game ends if you leave the track, creating a constant tension between driving safely and taking risks to keep the lights on. The scoring system is heavily inspired by classic arcade racers, featuring multipliers based on drift angle, speed, and continuous streaks.

**Technical Highlights & Architecture**

* **Procedural Track Generation (Object Pooling):** The endless track is generated dynamically. To ensure high performance and eliminate stuttering caused by instantiation and destruction, an Object Pool manages the track chunks, smoothly teleporting them as the player advances.
* **Event-Driven Systems (Observer Pattern):** The core game loop is decoupled using the Observer Pattern. Core systems like the `ScoreManager`, `LightManager`, and `UIManager` listen for events (e.g., `DriftStart`, `DriftEnd`, `PlayerOutOfBounds`), reducing tight coupling and avoiding the overhead of constant state-polling.
* **Singleton Pattern:** Used for global systems requiring persistent state across scenes, such as the `AudioManager` (for continuous music playback during restarts) and `SaveManager` (for handling high scores).
* **Custom Arcade Physics:** Rather than relying on complex, performance-heavy tire friction models, the car utilizes a custom vector-based controller. It interpolates (Lerps) the velocity vector towards the car's orientation based on a "Grip" coefficient, allowing for highly tunable and satisfying arcade drifting mechanics.
* **Dynamic Audio Modulation:** Implemented a system that modulates the pitch of the engine based on speed, and smoothly adjusts the volume of the tire screeches based on the drift angle and speed for seamless auditory feedback.
