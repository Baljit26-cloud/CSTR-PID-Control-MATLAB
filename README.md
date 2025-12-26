# 🌡️ PID Temperature Control of a CSTR (MATLAB & Simulink)

I built this simulation to model how a PID controller maintains a steady temperature in a **Continuous Stirred Tank Reactor (CSTR)**. In chemical engineering, precise temperature control is the difference between a successful reaction and a ruined batch. This project focuses on **disturbance rejection**—specifically how the system recovers when things go wrong.


---

## 🛠️ The Control Strategy

I modeled the CSTR process as a first-order system with a **10s time constant**. The target was a constant **50°C setpoint**.

### 🧠 PID Tuning (Manual Logic)
I didn't use auto-tune; I set these gains manually to understand the trade-offs:
* **Kp = 2**: Gets the temperature moving toward the setpoint quickly.
* **Ki = 0.1**: Wipes out the steady-state error so the temp actually hits 50°C and stays there.
* **Kd = 0.5**: Acts as a "damper" to prevent the system from overshooting the target and oscillating.

### 🧱 Simulink Model Breakdown
I built the feedback loop with specific blocks to mimic real-world hardware constraints:
1. **Sum Block:** Continuously calculates the Error ($Setpoint - Actual$).
2. **Saturation Block:** **Crucial Step.** I limited the Heat Input ($Q$) between 0 and 10. Real heaters don't have infinite power, so I capped the controller's output to keep the simulation realistic.
3. **Step Block:** Used to inject a **-5 unit cooling disturbance** at the 100-second mark to test if the controller could recover from a sudden external "shock."



---

## 📊 Results: Handling the Disturbance

The simulation ran for 200 seconds. Here’s what happened on the Scope:

* **0s - 50s:** The temperature rose steadily and settled at 50°C with almost zero overshoot.
* **100s Mark:** The cooling disturbance hit. The temperature dropped immediately.
* **100s - 150s:** The PID controller "saw" the drop and ramped up the heat input. The system fought back and returned to 50°C within 30 seconds.



---

## 💡 What I Actually Learned
* **Physical Limits:** Adding the **Saturation Block** changed everything. It taught me that a PID controller is only as good as the hardware (the heater) it's controlling.
* **Disturbance vs. Setpoint:** It’s easy to stay at a setpoint in a vacuum. The real test of an engineer is how the system handles a "hit" like the cooling disturbance I added at 100s.
* **Visualizing Logic:** Seeing the signal flow in Simulink made the math from my MATLAB scripts much easier to troubleshoot.

---

## 📂 Project Structure
* `cstr_pid_model.slx`: The main Simulink block diagram.
* `cstr_pid_control.mlx`: MATLAB Live Script for gain initialization and plotting.
* `scope_output.png`: The final temperature vs. time graph.

## ⚙️ How to Run
1. Open MATLAB and run `cstr_pid_control.mlx` to load the variables.
2. Open the `cstr_pid_model.slx` file.
3. Click **Run** and open the **Scope** block to see the live response.

---

### 👩‍🔬 Contact
**Baljit Kaur** [LinkedIn](https://www.linkedin.com/in/baljit-kaur-b1ba15324/) | bk5721333@gmail.com
