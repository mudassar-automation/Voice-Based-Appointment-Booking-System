# 🎙️ Voice-Based Appointment Booking System with ElevenLabs AI and Cal.com  

---

## 💡 What Problem Does This Workflow Solve?  

Tired of the back-and-forth involved in scheduling meetings?  
This workflow lets you offer a **seamless, voice-based appointment booking experience** powered by **ElevenLabs AI** and **Cal.com**.  

It automatically checks your Cal.com availability and either books a meeting or helps the caller choose another time — using **human-like voice interactions** for a natural, engaging experience.  

---

## ⚙️ What Does This Workflow Do?  

This automation handles the **entire appointment booking process** through natural voice conversation:  

1. **Receives an inbound voice call** (from your website, IVR, or phone system).  
2. Uses **ElevenLabs** to drive the conversation with lifelike AI-generated speech.  
3. **Checks real-time availability** from your **Cal.com** calendar.  
4. **Books a meeting** instantly if a slot is available.  
5. If not, **asks the user** for an alternate time and rechecks availability.  
6. **Confirms the booking** with a verbal response and optional **email or SMS notification**.  

---

## 🔧 Setup Guide  

### 🧠 ElevenLabs Custom Tools Setup  

Add **two custom tools** in your ElevenLabs “Custom Tools” section with the following details:

#### **Tool 1: `bookSlot`**
- **Description:** Use this tool when the user confirms their slot and appointment. Trigger it once you have the user's name and email.  
- **Method:** `POST`  
- **URL:** `{n8n_webhook_url}`  

#### **Tool 2: `checkAvailableSlot`**
- **Description:** Use this tool to check available time slots in your Cal.com calendar.  
- **Method:** `POST`  
- **URL:** `{n8n_webhook_url}`  

---

### 🗣️ ElevenLabs Prompt Configuration  

#### **First Message**  
> “Thanks for calling InfyOm Technologies. How can I help you?”

#### **System Prompt**

##### **1️⃣ Personality**
You are a **clear, helpful, and respectful assistant** focused solely on **booking appointments**.  
- **Identity:** Virtual appointment scheduler.  
- **Core Traits:** Polite, efficient, conversational, respectful.  
- **Role:** Guide users to choose a time, check availability, and finalize the booking.

##### **2️⃣ Tone**
- Polite, professional, and friendly — but always focused on completing the booking.  
- Use conversational cues like “Okay,” “Got it,” or “Sounds good.”  
- Keep the conversation warm, natural, and human-like.  

##### **3️⃣ Goal**
Your mission is simple — **book an appointment** for the client.  

---

### 🗓️ Step-by-Step Conversation Flow  

1. **Greeting & Purpose**  
   - Politely greet the caller.  
   - Example: “Hi! I’m here to help you book an appointment.”  

2. **Request Preferred Time**  
   - Ask: “Can you please tell me your preferred time slot for the appointment?”  
   - If unclear, ask for the full date (day, month, and year).  

3. **Check Availability**  
   - Use the `checkAvailableSlot` tool to verify the user’s requested time.  
   - If the slot **is available**:  
     - Confirm: “That slot is available. Should I go ahead and book it for you?”  
     - If confirmed → Use `bookSlot`.  
   - If the slot **is not available**:  
     - Say: “It looks like that time isn’t available. Would you like to check the same time on the next day?”  

4. **Handle Next-Day Option**  
   - If the user agrees, check the same time on the next day using `checkAvailableSlot`.  
   - If available → Confirm and use `bookSlot`.  
   - If not → Politely inform and ask for another time.  

5. **Close the Call**  
   - Confirm the booking and end with:  
     > “Great! Your appointment is booked. Thank you and have a wonderful day!”  

---

### 🧱 Guardrails  

- Stay strictly within the topic of **appointment booking**.  
- If the user asks about unrelated topics:  
  > “I’m only here to help with appointment bookings. For other questions, please contact our support team.”  
- Never speculate or provide data outside your scope.  
- Never ask the user to say their date in a specific format.  
  - If unclear, simply say:  
    > “Please speak the full date.”  

#### **Available Tools**
- `checkAvailableSlot` → Check available times.  
- `bookSlot` → Confirm and finalize appointments.  

#### **End Call**
> “Thanks for reaching out to us. Have a nice day.”  

---

## 📅 Cal.com API Setup  

1. Go to **[Cal.com](https://cal.com)** and generate an API key.  
2. Create new **Cal API credentials** inside n8n.  
3. Set this API key in your credentials to enable calendar access.  

---

## 🧠 How It Works  

### ☎️ 1️⃣ Incoming Call  
An inbound call triggers the workflow. The AI assistant greets the caller and starts the conversation.  

### 🧏 2️⃣ Voice Interaction (ElevenLabs)  
- ElevenLabs handles all **speech generation** and **voice interaction**.  
- The user can speak naturally, and the assistant responds in real time.  

### 🗓️ 3️⃣ Availability Check (Cal.com)  
- The assistant checks requested times against your Cal.com calendar.  
- ✅ If available → Books instantly.  
- ❌ If unavailable → Suggests alternatives.  

### 🔁 4️⃣ Retry Loop  
If the slot is unavailable:  
- The assistant asks for a new time.  
- The process repeats until a slot is found or the session ends gracefully.  

### ✅ 5️⃣ Appointment Confirmation  
Once booked, the AI verbally confirms the appointment and can also:  
- Send an **email confirmation**  
- Send an **SMS reminder** (optional)  

---

## 👤 Who Can Use This System?  

This system is perfect for:  

- 🧑‍⚕️ **Clinics or Therapists** – Automate patient scheduling through phone calls.  
- 🧑‍💼 **Consultants & Coaches** – Let clients book sessions via voice.  
- 🏢 **Sales Teams** – Schedule demos and follow-ups through inbound calls.  
- 🤖 **AI-first SaaS Companies** – Add voice scheduling to their product workflows.  

If your business relies on scheduled meetings, this **voice-first booking assistant** saves time, reduces friction, and creates a premium customer experience.  

---

## 🏁 Summary  

This **Voice-Based Appointment Booking System** combines **ElevenLabs AI** and **Cal.com** to create a natural, conversational scheduling experience.  

By merging **voice synthesis**, **real-time availability checking**, and **automated booking**, it delivers an intuitive and fully hands-free scheduling process — no forms, no friction, just **AI-powered simplicity**.  
