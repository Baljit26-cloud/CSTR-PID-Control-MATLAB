# 🌡️ PID Temperature Control of a CSTR (MATLAB & Simulink)

I built this simulation to model how a PID controller maintains a steady temperature in a **Continuous Stirred Tank Reactor (CSTR)**. In chemical engineering, precise temperature control is the difference between a successful reaction and a ruined batch. 

This project focuses on **disturbance rejection**—testing if the system can recover when an unexpected cooling load hits the reactor.


---

## 🛠️ The Control Strategy

I modeled the CSTR process as a first-order system with a **10s time constant**. The target was a constant **50°C setpoint**.

### 🧠 PID Tuning (Manual Logic)
I set these gains manually to understand how each parameter affects the physics:
* **Kp = 2**: Gets the temperature moving toward the setpoint quickly.
* **Ki = 0.1**: Wipes out the steady-state error so the temp actually hits 50°C.
* **Kd = 0.5**: Acts as a "damper" to prevent the system from overshooting.

### 🧱 Simulink Model Breakdown
I built the feedback loop to mimic real-world hardware. Here is how the logic flows:



1. **Sum Block:** Calculates the Error ($Setpoint - Actual$).
2. **Saturation Block:** I limited the Heat Input ($Q$) between 0 and 10. Real heaters don't have infinite power, so I capped the output to keep it realistic.
3. **Step Block:** Injects a **-5 unit cooling disturbance** at 100 seconds to test the controller's "reflexes."

---

## 📊 Results: Scope Output

The simulation ran for 200 seconds. The Scope shows exactly how the controller fights to keep the temperature stable.

![Scope Output Plot](visuals/scope_output.png)

### What happened in the graph?
* **0s - 50s:** The temperature rose steadily and settled at 50°C with zero overshoot.
* **100s Mark:** The cooling disturbance hit, and you can see the temperature drop immediately.
* **100s - 150s:** The PID controller ramped up the heat input. The system recovered and returned to 50°C within 30 seconds.



---

## 💡 What I Actually Learned
* **Physical Limits:** Adding the **Saturation Block** taught me that a PID controller is only as good as the heater it's controlling. If the heater is too small, no amount of tuning will fix the drop.
* **Disturbance vs. Setpoint:** It’s easy to stay at a setpoint when nothing is changing. The real test was the "hit" I added at 100s.
* **Visualizing Logic:** Seeing the signal flow in the Simulink blocks made it much easier to troubleshoot than just looking at lines of code.

---

## ⚙️ How to Run
1. Open MATLAB and run `cstr_pid_control.mlx` to load the variables.
2. Open `cstr_pid_model.slx`.
3. Click **Run** and open the **Scope** block to see the live response.

---

### 👩‍🔬 Contact
**Baljit Kaur** [LinkedIn](https://www.linkedin.com/in/baljit-kaur-b1ba15324/) | bk5721333@gmail.com
