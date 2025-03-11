# AI-Powered-Energy-Recovery-System
"Recover power losses (like eddy currents &amp; earthing losses), store them in a battery, and optimize power flow using AI and IoT."
# AI-Powered Energy Recovery System

## 📌 Project Overview
This project aims to **recover power dissipation losses** (such as eddy currents and earthing power loss) and store the recovered energy in a **battery**. The system uses **AI/ML reinforcement learning** combined with **IoT devices** and a **microservices architecture** to optimize energy inflow and outflow. The solution also incorporates **AC/DC conversion** for efficient power management.

## 🎯 Key Features
- **AI-driven Power Optimization**: Uses reinforcement learning to control power flow.
- **IoT-based Monitoring**: Collects real-time voltage, current, and power data.
- **Microservices Architecture**: Decentralized control for better scalability.
- **Battery Charge Tracking**: Displays battery charge percentage in real time.
- **Gradio UI Dashboard**: Provides an intuitive interface to visualize power availability vs. voltage.
- **MQTT Protocol**: Enables real-time communication between IoT devices and the AI model.

## 🛠️ Tech Stack
- **Python** (AI Model, Backend Services)
- **Gradio** (Web UI for visualization)
- **MQTT (paho-mqtt)** (IoT communication protocol)
- **Matplotlib** (Graph visualization)
- **NumPy** (Data processing)
- **Google Colab** (Development environment)

## 📌 How It Works
1. **IoT devices** collect **voltage and current** readings.
2. The data is sent via **MQTT protocol** to the AI model.
3. The AI model **analyzes the power** and decides:
   - Increase Charging 🔼
   - Stop Charging 🛑
   - Maintain Power Flow ⚡
4. The **Gradio UI Dashboard** visualizes battery charge % vs. voltage.

## 🚀 Installation & Setup
### 1️⃣ Install Dependencies
```bash
pip install gradio paho-mqtt numpy matplotlib
```

### 2️⃣ Run the AI Power Management System
# AI-Powered Energy Recovery System

## 📌 Project Overview
This project aims to **recover power dissipation losses** (such as eddy currents and earthing power loss) and store the recovered energy in a **battery**. The system uses **AI/ML reinforcement learning** combined with **IoT devices** and a **microservices architecture** to optimize energy inflow and outflow. The solution also incorporates **AC/DC conversion** for efficient power management.

## 🎯 Key Features
- **AI-driven Power Optimization**: Uses reinforcement learning to control power flow.
- **IoT-based Monitoring**: Collects real-time voltage, current, and power data.
- **Microservices Architecture**: Decentralized control for better scalability.
- **Battery Charge Tracking**: Displays battery charge percentage in real time.
- **Gradio UI Dashboard**: Provides an intuitive interface to visualize power availability vs. voltage.
- **MQTT Protocol**: Enables real-time communication between IoT devices and the AI model.

## 🛠️ Tech Stack
- **Python** (AI Model, Backend Services)
- **Gradio** (Web UI for visualization)
- **MQTT (paho-mqtt)** (IoT communication protocol)
- **Matplotlib** (Graph visualization)
- **NumPy** (Data processing)
- **Google Colab** (Development environment)

## 📌 How It Works
1. **IoT devices** collect **voltage and current** readings.
2. The data is sent via **MQTT protocol** to the AI model.
3. The AI model **analyzes the power** and decides:
   - Increase Charging 🔼
   - Stop Charging 🛑
   - Maintain Power Flow ⚡
4. The **Gradio UI Dashboard** visualizes battery charge % vs. voltage.

## 🚀 Installation & Setup
### 1️⃣ Install Dependencies
```bash
pip install gradio paho-mqtt numpy matplotlib
```

### 2️⃣ Run the AI Power Management System
```python
import gradio as gr
import paho.mqtt.client as mqtt
import json
import matplotlib.pyplot as plt
import numpy as np

# Initialize battery charge
battery_charge = 50.0
voltage_data = []
power_data = []

def optimize_power(voltage, current):
    power = voltage * current
    if power < 10:
        return "Increase Charging"
    elif power > 50:
        return "Stop Charging"
    else:
        return "Maintain Power Flow"

def on_message(client, userdata, message):
    global battery_charge, voltage_data, power_data
    data = json.loads(message.payload.decode())
    voltage, current = data['voltage'], data['current']
    power = voltage * current
    battery_charge = min((power / 50) * 100, 100)
    voltage_data.append(voltage)
    power_data.append(battery_charge)
    action = optimize_power(voltage, current)
    print(f"AI Decision: {action}")

def plot_dashboard():
    plt.figure(figsize=(6,4))
    plt.plot(voltage_data, power_data, marker='o', linestyle='-', color='b', label='Battery Charge')
    plt.xlabel('Voltage (V)')
    plt.ylabel('Battery Charge (%)')
    plt.title('Power Availability vs Voltage')
    plt.legend()
    plt.grid()
    plt.savefig("dashboard.png")
    return "dashboard.png"

# MQTT Setup
client = mqtt.Client()
client.on_message = on_message
client.connect("broker.hivemq.com", 1883)
client.subscribe("power/data")
client.loop_start()

gr.Interface(fn=plot_dashboard, inputs=[], outputs="image", title="🔋 IoT Power Monitoring Dashboard", description="Real-time Power Availability vs Voltage Chart").launch()
```

## 📊 Expected Output
- A **real-time dashboard** displaying battery charge (%) vs voltage.
- AI decisions for **power optimization** printed in the console.

## 📜 License
This project is licensed under the **MIT License**.

## 🤝 Contributing
Feel free to contribute by improving the AI model, optimizing power recovery methods, or enhancing UI features!

## 🛠️ Future Enhancements
- **Reinforcement Learning**: Train AI to predict better power recovery strategies.
- **Battery Efficiency Reports**: Generate logs for power savings.
- **Edge Computing**: Optimize AI processing on IoT devices.

---
📧 **Contact**: For any queries, reach out to sivamallikarjun2601@gmail.com.

🚀 *Let’s make power recovery smarter and more efficient!*


## 📊 Expected Output
- A **real-time dashboard** displaying battery charge (%) vs voltage.
- AI decisions for **power optimization** printed in the console.

## 📜 License
This project is licensed under the **MIT License**.

## 🤝 Contributing
Feel free to contribute by improving the AI model, optimizing power recovery methods, or enhancing UI features!

## 🛠️ Future Enhancements
- **Reinforcement Learning**: Train AI to predict better power recovery strategies.
- **Battery Efficiency Reports**: Generate logs for power savings.
- **Edge Computing**: Optimize AI processing on IoT devices.

---
📧 **Contact**: For any queries, reach out to sivamallikarjun2601@gmail.com.

🚀 *Let’s make power recovery smarter and more efficient!*
For git Clone : https://github.com/PSivaMallikarjun/AI-Powered-Energy-Recovery-System
![Screenshot 2025-03-10 232334](https://github.com/user-attachments/assets/a6985f94-1d08-49f0-a05a-cd615da33767)
![Screenshot 2025-03-11 233642](https://github.com/user-attachments/assets/3d9985aa-bb84-40b9-b7ba-5c6a637d05a4)
![Screenshot 2025-03-12 003537](https://github.com/user-attachments/assets/1dd3d772-436f-4317-ac48-89ed92237335)





