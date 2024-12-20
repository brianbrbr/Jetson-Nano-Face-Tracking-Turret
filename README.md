# Jetson-Nano-Face-Tracking-Turret
Face and eye tracking turret using Jetson Nano, CSI camera, and pan-tilt mechanism. Tracks faces, detects eyes, and lights up LEDs for demo shooting.

Demo : Video https://youtu.be/sykdySLcNLY


## 🛠️ Motivation
I saw a video on IG and couldn't stop wondering:
1. How does it work?
2. How does the machine track people and "shoot"?

The original author didn't open-source their project (sadly 😢), so I decided to build my own version with the materials I had on hand. Here's how I made it:

- **Original setup**: Husky Lens + 3D-printed Killjoy turret.
- **My version**: Jetson Nano + CSI camera + pan-tilt mechanism + LED lighting for shooting demo.

This project is a mix of **curiosity, creativity, and some good ol' engineering hustle**.

---

## 🔍 What This Code Does
### 🧰 Libraries
- Import the necessary libraries for face and eye tracking using OpenCV.

### 🕹️ Initialization
- Release GPIO resources (we're responsible engineers 💡).
- Initialize the servo motor and LED to prepare for operation.

### 🔄 Multithreading
- Use threading to optimize Jetson Nano's resource utilization. Because who doesn't love efficiency?

### 📸 Camera Setup
- Configure the CSI camera for a **320x240** resolution display.

### 🧠 Classifiers
- Use **face** and **eye classifiers** from OpenCV's GitHub repository.
- Convert images to grayscale for faster processing.

### 🎯 Face Tracking Logic
1. Detect and draw a rectangle around the face.
2. Find the rectangle's center.
3. If the rectangle's center shifts by more than 15 pixels, the servo adjusts to track the face.  
   (Hyperparameter `50` controls servo speed—feel free to tune it!)
4. Keep the servo movement between **0° and 180°**.

### 👁️ Eye Detection Logic
- Detect eyes and draw rectangles around them.
- If eyes are detected, the LED lights up (pew pew ✨). Otherwise, it stays off.

### 🛑 Resource Release
- Clean up GPIO resources like a pro.

---

## 🚀 Results & Experiments
1. **Face Test**  
   It worked well with my face (phew, no AI rebellion yet).  

2. **Glasses Test**  
   - With glasses: Eye detection was slightly less accurate.  
   - Without glasses: Detection became noticeably more precise.  

3. **Low Light Test**  
   - In darker environments, precision decreased.  
   - Brighter environments yield better results.  

4. **Ex-girlfriend Barbara Test**  
   It worked surprisingly well on her face. Jetson Nano is unforgiving.  

5. **Face Image Test**  
   Images were classified accurately, proving that a static setup can maximize tracking utility.

---

## 🌱 Potential Research Opportunities
- How can this system be optimized to **maximize expected utility** in varying environments?  
- Explore better algorithms or hardware setups for faster and more precise tracking.

---

## 🎉 Contribution
This project demonstrates the versatility of **Jetson Nano** in tracking tasks:
- **Self-media**: Create interactive media content.  
- **Security cameras**: Track intruders with precision.  
- **Film industry**: Automate dynamic shots with low-budget setups.  

---

## ⚡ Impact
A simple setup with **Jetson Nano** can open doors for creators, engineers, and researchers in multiple industries.  
With a bit of tinkering, you too can build your own smart turret to track whatever (or whoever) you like.

---

## 📝 Circuit Diagram
![Jetson-Nano-Face-Tracking-Turret-circuit](https://github.com/user-attachments/assets/60d7dce7-097a-4a1d-a8c0-687173ec7cd7)

---

## 📜 License
MIT License. Steal like an artist, but give credit where it's due. 😉

---

## 🙌 How to Run
1. Clone this repo:  
   ```bash
   git clone https://github.com/brianbrbr/jetson-nano-eye-turret.git


---

## 🤔 Questions You Might Have
1. What if my CSI camera isn't working?
Double-check the connection to the Jetson Nano.
Run v4l2-ctl --list-devices to confirm the camera is detected.

2. Why is my servo not moving?
Verify the GPIO pins are connected correctly.
Check the power supply to the servo motor.

3. Why is eye detection not accurate?
Lighting conditions matter. Test in a well-lit environment.
Adjust the hyperparameters (50 for speed tuning).

4. Can I use a USB camera instead of a CSI camera?
Yes, modify the camera setup code to support a USB camera.

5. What if I want to track objects other than faces?
Replace the face and eye classifiers with another object detection model from OpenCV.

6.Can I modify the LED to trigger something else?
Sure! Replace the LED logic with any GPIO-controlled action, such as activating a buzzer or a small water gun.
