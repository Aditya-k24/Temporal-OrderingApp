
# 🕒 Temporal Ordering App

A resilient, event-driven backend application built with [Temporal](https://temporal.io/) and TypeScript. This project orchestrates an **order fulfillment workflow** that includes automated steps (verification, payment, shipping) and a **human-in-the-loop approval** step — ideal for real-world e-commerce and logistics systems.

---

## 🚀 Features

- 🛠️ Built using **Temporal TypeScript SDK**
- ✅ Fault-tolerant **workflow orchestration**
- 🔁 Automatic **retries** and **timeouts** for activities
- ⏳ Delayed execution for async or real-world wait scenarios
- 🙋 **Human approval** via signal (manager approval flow)
- 🔍 **Queryable workflow status** in real-time
- 🧪 Fully testable and observable via Temporal Web UI

---

## 🧠 How It Works

1. The client triggers the `example` workflow with an order ID.
2. The workflow:
   - Verifies the order
   - Processes payment
   - Waits for **manager approval** using a Temporal **signal**
   - Times out if no approval within 15 seconds
   - Ships the order if approved
3. Client can **query status** anytime using a Temporal **query handler**.
4. All state is persisted and resilient to crashes or restarts.

---

## 🏗️ Project Structure

```
temporal-practice/
├── activities/            # Business logic (verify, pay, ship)
├── workflows/             # Temporal workflow logic
├── client.ts              # Starts workflow, sends signal, queries
├── worker.ts              # Registers and runs worker
├── tsconfig.json
└── README.md
```

---

## 📦 Prerequisites

- Node.js v18+
- Docker
- Git
- Temporal server (via Docker Compose)

---

## 🛠️ Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/Aditya-k24/Temporal-OrderingApp.git
cd Temporal-OrderingApp
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start Temporal Server (in a separate terminal)

```bash
git clone https://github.com/temporalio/docker-compose.git
cd docker-compose
docker-compose up
```

### 4. Run the Worker

```bash
npm run worker
```

### 5. Start the Client

```bash
npm run client
```

---

## 💡 Sample Output

```bash
🚀 Workflow started with ID: order-<timestamp>
📋 Status before approval: 🕓 Waiting for approval
✅ Approval signal sent.
🎉 Final Result:
✅ Done:
- Order order-999 verified
- Payment processed for order-999
- Approved by manager
- Order order-999 shipped
```

🧭 Track progress at [http://localhost:8233](http://localhost:8233)

---

## 🧩 Built With

- [Temporal.io](https://temporal.io/)
- [TypeScript](https://www.typescriptlang.org/)
- [Node.js](https://nodejs.org/)
- [Docker](https://www.docker.com/)
- [ts-node](https://typestrong.org/ts-node/)

---

## 📃 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for more info.

---

## 🙌 Author

**Aditya Kulkarni**  
[GitHub](https://github.com/Aditya-k24)

---

## 📬 Feedback or Contributions?

Feel free to open issues or pull requests. Star ⭐ the repo if you found it useful!
