# 🔬 PID-Based Temperature Control of a CSTR using MATLAB & Simulink

A simulation-based control systems project where I built and visualized a *PID-controlled temperature system* for a *Continuous Stirred Tank Reactor (CSTR). Using **MATLAB* and *Simulink, I modeled how to maintain a setpoint temperature of **50 °C*, respond to disturbances, and stabilize the system dynamically.

---

## 🧠 What I Learned
- Fundamentals of *process dynamics* and *feedback control*
- How a *PID controller* handles real-time *error correction*
- Modeling chemical systems in *MATLAB* and *Simulink*
- Importance of *tuning* and *disturbance rejection* in industrial control

---

## 💻 MATLAB Simulation – What I Coded

A 200-second simulation with:
- 📌 *Setpoint*: 50 °C  
- 🔧 *PID Gains*:  
  - Kp = 2  
  - Ki = 0.1  
  - Kd = 0.5  
- ⏱ *Time constant (T)*: 10 s  
- 🔥 *Q (Heat Input)*: Limited between 0 and 10  
- 🌬 *Disturbance*: -5 unit cooling added at 100 seconds

### 🔍 System Behavior
- The temperature rose steadily toward the setpoint.
- At 100s, the disturbance caused a sharp drop.
- The PID controller responded by adjusting heat input.
- The system re-stabilized efficiently — showcasing effective controller tuning.

---

## 🧰 Simulink Model – Visualizing the Logic

To better understand the control loop, I created a *Simulink block diagram* with:

- 📌 *Constant block* → for 50 °C setpoint  
- ➕ *Sum block* → to compute error  
- 🧠 *PID Controller block* → to adjust Q  
- 🔐 *Saturation block* → Q limited between 0 and 10  
- 🔁 *Transfer Function block* → modeled the CSTR process  
- 📉 *Step block* → to introduce the -5 unit disturbance at 100s  
- 👁 *Scope block* → to visualize the system response

---

## 📊 Scope Output – What Happened

- Early simulation: temperature gradually approached 50 °C
- At 100s: disturbance introduced a drop
- PID control kicked in with corrective action
- The system smoothly returned to the setpoint

✅ This highlighted the controller’s *robustness, fast **settling time, and **disturbance handling* capabilities.

---

## 🔗 Connect With Me

If you're interested in control systems, chemical process modeling, or just want to collaborate, feel free to reach out:

- 👩‍🔬 *Baljit Kaur*  
- 🌐 [LinkedIn](https://www.linkedin.com/in/baljit-kaur-b1ba15324/)
- 📫 Email: (bk5721333@gmail.com)

---

## 📁 Project Files

| File | Description |
|------|-------------|
| cstr_pid_control.mlx | MATLAB Live Script |
| cstr_pid_model.slx | Simulink model |
| scope_output.png | Temperature vs Time graph |
| simulink_diagram.png | Visual layout of Simulink model |
| README.md | You're reading it! 😊 |

---

### 🌟 Made with MATLAB, Simulink & a lot of curiosity.
