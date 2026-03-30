<!doctype html>
<html lang="nl">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Samen To-Do</title>
    <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
    <style>
      body {
        font-family: Arial, sans-serif;
        margin: 0;
        background: #f8fafc;
        color: #0f172a;
      }
      .wrap {
        max-width: 760px;
        margin: 0 auto;
        padding: 24px;
      }
      .card {
        background: white;
        border-radius: 16px;
        padding: 16px;
        margin-bottom: 16px;
        box-shadow: 0 2px 10px rgba(0,0,0,0.06);
      }
      input, button, select {
        width: 100%;
        padding: 12px;
        border-radius: 10px;
        border: 1px solid #cbd5e1;
        box-sizing: border-box;
        margin-top: 8px;
      }
      button {
        background: black;
        color: white;
        border: none;
        cursor: pointer;
      }
      .row {
        display: grid;
        gap: 12px;
      }
      .task {
        display: flex;
        justify-content: space-between;
        gap: 10px;
        align-items: center;
        border: 1px solid #e2e8f0;
        border-radius: 12px;
        padding: 12px;
        margin-top: 10px;
      }
      .small {
        font-size: 14px;
        color: #475569;
      }
      .hidden {
        display: none;
      }
    </style>
  </head>
  <body>
    <div class="wrap">
      <div class="card">
        <h1>Samen To-Do</h1>
        <div class="small">Voor jou en je vrouw</div>
      </div>

      <div id="authCard" class="card">
        <h2>Inloggen / registreren</h2>
        <input id="email" type="email" placeholder="E-mailadres" />
        <input id="password" type="password" placeholder="Wachtwoord" />
        <button id="signupBtn">Account maken</button>
        <button id="loginBtn">Inloggen</button>
        <div id="authMsg" class="small"></div>
      </div>

      <div id="appCard" class="hidden">
        <div class="card">
          <h2>Nieuwe taak</h2>
          <input id="taskInput" placeholder="Bijv. boodschappen doen" />
          <button id="addTaskBtn">Taak toevoegen</button>
        </div>

        <div class="card">
          <h2>Taken</h2>
          <div id="taskList"></div>
          <button id="logoutBtn">Uitloggen</button>
        </div>
      </div>
    </div>

    <script>
      const SUPABASE_URL = "VUL_LATER_IN_VERCEL_OF_HIER_IN";
      const SUPABASE_ANON_KEY = "VUL_LATER_IN_VERCEL_OF_HIER_IN";

      let supabase = null;
      let currentUser = null;

      const authCard = document.getElementById("authCard");
      const appCard = document.getElementById("appCard");
      const authMsg = document.getElementById("authMsg");
      const emailEl = document.getElementById("email");
      const passwordEl = document.getElementById("password");
      const taskInput = document.getElementById("taskInput");
      const taskList = document.getElementById("taskList");

      function showAuth() {
        authCard.classList.remove("hidden");
        appCard.classList.add("hidden");
      }

      function showApp() {
        authCard.classList.add("hidden");
        appCard.classList.remove("hidden");
      }

      function safeInit() {
        if (
          !SUPABASE_URL ||
          !SUPABASE_ANON_KEY ||
          SUPABASE_URL.includes("VUL_LATER") ||
          SUPABASE_ANON_KEY.includes("VUL_LATER")
        ) {
          authMsg.textContent = "Nog niet gekoppeld aan Supabase.";
          return false;
        }
        supabase = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);
        return true;
      }

      async function loadTasks() {
        const { data, error } = await supabase
          .from("tasks")
          .select("*")
          .eq("user_id", currentUser.id)
          .order("id", { ascending: false });

        if (error) {
          taskList.innerHTML = "<div class='small'>Kon taken niet laden.</div>";
          return;
        }

        if (!data.length) {
          taskList.innerHTML = "<div class='small'>Nog geen taken.</div>";
          return;
        }

        taskList.innerHTML = "";
        data.forEach((task) => {
          const div = document.createElement("div");
          div.className = "task";
          div.innerHTML = `
            <div>
              <strong>${task.title}</strong>
            </div>
            <button data-id="${task.id}">Verwijderen</button>
          `;
          div.querySelector("button").onclick = async () => {
            await supabase.from("tasks").delete().eq("id", task.id);
            loadTasks();
          };
          taskList.appendChild(div);
        });
      }

      document.getElementById("signupBtn").onclick = async () => {
        if (!safeInit()) return;
        const email = emailEl.value.trim();
        const password = passwordEl.value.trim();
        const { error } = await supabase.auth.signUp({ email, password });
        authMsg.textContent = error ? error.message : "Account gemaakt. Check eventueel je mail.";
      };

      document.getElementById("loginBtn").onclick = async () => {
        if (!safeInit()) return;
        const email = emailEl.value.trim();
        const password = passwordEl.value.trim();
        const { data, error } = await supabase.auth.signInWithPassword({ email, password });
        authMsg.textContent = error ? error.message : "Ingelogd";
        if (!error) {
          currentUser = data.user;
          showApp();
          loadTasks();
        }
      };

      document.getElementById("addTaskBtn").onclick = async () => {
        const title = taskInput.value.trim();
        if (!title) return;
        await supabase.from("tasks").insert({ title, user_id: currentUser.id });
        taskInput.value = "";
        loadTasks();
      };

      document.getElementById("logoutBtn").onclick = async () => {
        await supabase.auth.signOut();
        currentUser = null;
        showAuth();
      };

      showAuth();
    </script>
  </body>
</html>
