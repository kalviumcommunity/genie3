# 🧞‍♂️ genie3 – Web-Based Genie

`genie3` is a magical, interactive GenAI-powered genie that grants you **three creative wishes per session**. This version is built using **Next.js**, offering a fully web-based interface with visual flair, smooth user interaction, and support for advanced GenAI techniques like prompt engineering, session tracking, and RAG (Retrieval-Augmented Generation).

---

## 🌐 Why Use Next.js?

- Fully interactive web UI (better than terminal)
- Easy integration with GenAI APIs (e.g., Gemini)
- Ideal for animations, state management, and sharing
- Supports server-side logic + client-side UI in one framework

---

## 📁 Suggested Folder Structure

```
genie3-next/
├── app/
│   ├── page.tsx (Main genie UI)
│   └── api/
│       └── wish/route.ts (API handler)
├── components/
│   ├── GenieBox.tsx
│   ├── WishCard.tsx
│   └── RiddleUnlock.tsx
├── lib/
│   ├── gemini.ts (Gemini API integration)
│   └── rag.ts (Optional: RAG logic)
├── public/
├── styles/
├── wish_log.json
├── .env.local
└── README.md
```

---

## 🧠 Core Features

### ✅ System Prompt

Sent along with every user prompt:

```
You are Genie3 — a mystical, humorous AI genie who grants users exactly three wishes per session...
```

### ✅ Wish Handling

1. User enters wish in `<GenieBox />`
2. POST to `/api/wish`
3. Gemini API called with system + user prompt
4. Structured response returned and displayed

### ✅ Tuning Parameters

Modify temperature and top_p for creative or serious outputs:

```ts
// silly-mode
const sillyConfig = {
  temperature: 1.0,
  topP: 1.0
};

// serious-mode
const seriousConfig = {
  temperature: 0.5,
  topP: 0.9
};

```

### ✅ Structured Output

Example response:

```json
{
  "wish_type": "poem",
  "title": "Ode to Procrastination",
  "response": "...",
  "humor_rating": 7,
  "tone": "sarcastic"
}
```

Display response via `<WishCard />`.

---

## 🔁 Session Control

- Use localStorage or cookies to track remaining wishes
- After 3 wishes, render `<RiddleUnlock />` component
- Correct riddle answer resets counter to 3

```ts
if (userAnswer === "m") { // "m" is the riddle answer in this example
  localStorage.setItem("wishes", "3");
}
```

---

## 🧰 RAG Support (Optional)

Use `/lib/rag.ts` to search local files like:

- `rare_facts.json`
- `weird_history.md`

Inject into Gemini context as additional prompt input.

---

## ⚙️ Tech Stack

| Part     | Tech                      |
| -------- | ------------------------- |
| Frontend | Next.js + Tailwind CSS    |
| Backend  | API Routes (route.ts)     |
| GenAI    | Gemini API (Google AI)    |
| Storage  | localStorage / JSON file  |
| Optional | FAISS, Pinecone (for RAG) |

---

## ✅ Evaluation Criteria

### ✔️ Correctness

- System + user prompt ensure Genie acts correctly
- Wishes are structured and returned accurately
- Riddle logic enforces wish limit

### ⚡ Efficiency

- Minimal API calls
- Client-side state stored locally
- Optional: cache wishes in local JSON

### 📈 Scalability

- Easily deployed on Vercel
- Stateless wish API scales horizontally
- RAG can scale using vector DBs

---

## 🔮 Future Features

- User authentication + multi-session tracking
- Shareable wish logs
- Export wishes as story PDFs
- Animated genie avatar
- Dark mode / theme support

