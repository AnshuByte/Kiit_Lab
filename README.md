<h1 align="center">KIIT LAB</h1>
<p align="center"><strong>The Serverless, Collaborative IDE</strong></p>

---

## 🚀 Overview

**Cloud Coder** is a scalable, serverless Integrated Development Environment (IDE) that brings real-time collaboration to your browser. Built on modern cloud technologies, it lets you write, run, and share code with your team—no local setup required.

- **Serverless**: Auto-scaling compute powered by AWS Lambda.
- **Multi-language**: Supports JavaScript/TypeScript, Python, Go, and more.
- **Secure**: End-to-end encrypted sessions with Google OAuth 2.0 and JWT.

---

## 🔍 Key Features

| Feature                            | Benefit                                       |
|------------------------------------|-----------------------------------------------|
| **VS Code–style Editor**           | Familiar Monaco interface; syntax highlighting, IntelliSense, extensions. |
| **On-demand Code Execution**       | Isolated, serverless sandboxes via Judge0.    |
| **Persistent Storage**             | MongoDB Atlas . |
| **OAuth Authentication**           | Secure sign-in with Google; fine-grained access control. |
| **Built-in DevOps**                | CI/CD templates for GitHub Actions & Vercel deployments. |

---

## 🏗 Architecture

```
┌──────────────┐       ┌──────────────┐       ┌──────────────┐
│  Frontend    │──HTTP─▶ AWS API Gateway  ──▶│ AWS Lambda   │──▶ Judge0 (Docker)
│  (Next.js)   │       │ (NestJS handlers)│   └──────────────┘
└──────────────┘       └──────────────┘
          │
          └─────────────────▶ MongoDB Atlas (with GridFS)
```

1. **Next.js + Monaco Editor** serves the client.
2. **AWS API Gateway → Lambda (NestJS)** handles authentication, collaboration events, and persistence.
3. **Judge0 cluster** executes code in isolated containers.
4. **MongoDB Atlas** stores user projects, files, and session histories.

---

## 🛠 Tech Stack

| Layer             | Technologies                                             |
|-------------------|----------------------------------------------------------|
| **Client**        | Next.js, React, Monaco Editor, Tailwind CSS              |
| **Server**        | AWS Lambda, API Gateway, NestJS                          |
| **Execution**     | Judge0 self-hosted (Docker)                              |
| **Database**      | MongoDB Atlas + GridFS                                   |
| **Authentication**| Google OAuth 2.0, JWT                                    |
| **CI/CD & Hosting** | GitHub Actions, Vercel, DigitalOcean Droplets         |

---

## 📦 Installation & Local Development

1. **Clone the repository**  
   ```bash
   git clone https://github.com/AnshuByte/Kiit_Lab.git
   cd cloud-coder
   ```

2. **Install dependencies**  
   ```bash
   pnpm install    # or npm install / yarn
   ```

3. **Configure environment**  
   Copy `.env.example` to `.env.local` and fill in:
   - `NEXT_PUBLIC_API_URL`
   - `GOOGLE_OAUTH_CLIENT_ID` & `SECRET`
   - `MONGODB_URI`
   - AWS credentials (for local AWS Lambda invocation)

4. **Start development server**  
   ```bash
   pnpm dev
   ```

5. **Run backend functions locally**  
   ```bash
   pnpm workspace @cloud-coder/api start
   ```

---

## ⚙️ Usage

- Open your browser at `http://localhost:3000`
- Sign in with Google  
- Create or join a workspace  
- Invite collaborators via shareable link  
- Write, run, and debug code together in real time  



---

## 🛡 License

Distributed under the **MIT License**. See [LICENSE](./LICENSE) for details.

---

