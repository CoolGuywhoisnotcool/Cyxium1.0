<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Cyxium - Pastebin</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background-color: #0D0D0D;
      color: white;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      animation: neonPulse 6s infinite ease-in-out;
    }

    @keyframes neonPulse {
      0%, 100% { box-shadow: inset 0 0 80px rgba(0, 255, 255, 0.02); }
      50% { box-shadow: inset 0 0 120px rgba(0, 255, 255, 0.04); }
    }

    .topbar {
      background-color: #1A1A1A;
      height: 75px;
      display: flex;
      align-items: center;
      padding: 0 30px;
      box-shadow: 0 2px 6px rgba(0, 255, 255, 0.1);
    }

    .logo {
      height: 68px;
      margin-right: 30px;
      transform: translateY(1px);
    }

    .tabs {
      display: flex;
      gap: 20px;
    }

    .tab {
      color: white;
      text-decoration: none;
      font-size: 20px;
      padding: 10px 15px;
      border-radius: 6px;
      transition: background 0.3s, box-shadow 0.3s;
      cursor: pointer;
    }

    .tab:hover {
      background-color: #2A2A2A;
      box-shadow: 0 0 10px rgba(0, 255, 255, 0.3);
    }

    .content {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 40px;
      animation: fadeIn 1.5s ease-out;
    }

    .page-box {
      max-width: 800px;
      text-align: center;
      width: 100%;
    }

    .page-box h1 {
      font-size: 36px;
      margin-bottom: 20px;
      color: #00ffff;
    }

    .page-box p {
      font-size: 18px;
      line-height: 1.6;
      color: #cccccc;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    /* New Paste Form Styles */
    .paste-form {
      background: #181818;
      padding: 32px 24px 24px 24px;
      border-radius: 12px;
      box-shadow: 0 0 24px rgba(0,255,255,0.08);
      max-width: 540px;
      margin: 0 auto;
      text-align: left;
      display: flex;
      flex-direction: column;
      gap: 18px;
      animation: fadeIn 1s;
    }
    .paste-form label {
      color: #00ffff;
      font-weight: 600;
      margin-bottom: 4px;
      display: block;
      font-size: 16px;
    }
    .paste-form input[type="text"],
    .paste-form textarea {
      width: 100%;
      padding: 10px;
      border-radius: 6px;
      background: #232323;
      border: 1px solid #444;
      color: #fff;
      margin-bottom: 10px;
      font-size: 16px;
      resize: none;
    }
    .paste-form textarea {
      min-height: 200px;
      max-height: 450px;
      height: 240px;
      overflow-y: auto;
      font-family: 'Fira Mono', 'Consolas', monospace;
      font-size: 15px;
      line-height: 1.5;
    }
    .paste-form .paste-fields {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }
    .paste-form .form-actions {
      display: flex;
      justify-content: flex-end;
      gap: 8px;
    }
    .paste-form button {
      padding: 10px 28px;
      font-size: 18px;
      border-radius: 6px;
      border: none;
      cursor: pointer;
      background: linear-gradient(90deg, #00ffff, #0ed7b5);
      color: #181818;
      font-weight: 700;
      letter-spacing: 1px;
      box-shadow: 0 2px 10px rgba(0,255,255,0.16);
      transition: background 0.2s, color 0.2s;
    }
    .paste-form button:hover {
      background: linear-gradient(90deg, #0ed7b5, #00ffff);
      color: #000;
    }
    /* Responsive */
    @media (max-width: 700px) {
      .content { padding: 5vw; }
      .page-box { padding: 0; }
      .paste-form { max-width: 96vw; }
    }
  </style>
</head>
<body>
  <div class="topbar">
    <img src="https://i.imgur.com/wqej1EZ.png" alt="Logo" class="logo">
    <div class="tabs">
      <div class="tab" onclick="showPage('home')">Home</div>
      <div class="tab" onclick="showPage('new')">New</div>
      <div class="tab" onclick="showPage('search')">Search</div>
      <div class="tab" onclick="showPage('tos')">TOS</div>
    </div>
  </div>

  <div class="content">
    <div class="page-box" id="page-content">
      <!-- Home content is loaded by default -->
      <h1>Welcome to Cyxium</h1>
      <p>
        Cyxium is a free and lightweight pastebin built for the scripting and cheating community.<br><br>
        A <strong>paste</strong> is a simple way to store and share text online — usually code, scripts, or config files — using just a link.<br><br>
        Whether you're sharing Lua scripts, Python tools, or Roblox cheats, Cyxium is built to let you paste and share instantly without limits.<br><br>
        Cyxium is not just fast and easy to use — it's also made with privacy in mind. No forced accounts, no paywalls.<br><br>
        Before uploading your content, please take a moment to read our <strong>Terms of Service (TOS)</strong> to make sure your paste doesn't violate any rules. We aim to keep Cyxium safe, open, and abuse-free.
      </p>
    </div>
  </div>

  <script>
    function showPage(page) {
      const content = document.getElementById('page-content');
      if (page === 'home') {
        content.innerHTML = `
          <h1>Welcome to Cyxium</h1>
          <p>
            Cyxium is a free and lightweight pastebin built for the scripting and cheating community.<br><br>
            A <strong>paste</strong> is a simple way to store and share text online — usually code, scripts, or config files — using just a link.<br><br>
            Whether you're sharing Lua scripts, Python tools, or Roblox cheats, Cyxium is built to let you paste and share instantly without limits.<br><br>
            Cyxium is not just fast and easy to use — it's also made with privacy in mind. No forced accounts, no paywalls.<br><br>
            Before uploading your content, please take a moment to read our <strong>Terms of Service (TOS)</strong> to make sure your paste doesn't violate any rules. We aim to keep Cyxium safe, open, and abuse-free.
          </p>`;
      } else if (page === 'new') {
        content.innerHTML = `
          <h1>New Paste</h1>
          <form class="paste-form" id="pasteForm" autocomplete="off" onsubmit="return false">
            <div class="paste-fields">
              <label for="pasteTitle">Title</label>
              <input type="text" id="pasteTitle" name="title" maxlength="64" placeholder="Enter a title (optional)">
              <label for="pasteDesc">Description</label>
              <input type="text" id="pasteDesc" name="description" maxlength="120" placeholder="Add a description (optional)">
              <label for="pasteTag">Custom Tag</label>
              <input type="text" id="pasteTag" name="tag" maxlength="32" placeholder="Add a custom tag (optional)">
              <label for="pasteContent">Paste Content</label>
              <textarea id="pasteContent" name="content" required placeholder="Paste your text/code here..." spellcheck="false"></textarea>
            </div>
            <div class="form-actions">
              <button type="submit" id="createPasteBtn">Create</button>
            </div>
          </form>
        `;
        setTimeout(() => {
          const form = document.getElementById('pasteForm');
          form.onsubmit = async function () {
            // Get values
            const title = document.getElementById('pasteTitle').value.trim();
            const description = document.getElementById('pasteDesc').value.trim();
            const tag = document.getElementById('pasteTag').value.trim();
            const content = document.getElementById('pasteContent').value.trim();

            if (!content) {
              alert("Paste content can't be empty!");
              return false;
            }

            // Simulate paste ID generation: base36 timestamp + 4 random chars
            const id = (Date.now().toString(36) + Math.random().toString(36).substr(2,4)).toLowerCase();
            // Optionally, store to localStorage (for demo)
            const pasteData = { title, description, tag, content, created: Date.now() };
            localStorage.setItem('cyxium_paste_' + id, JSON.stringify(pasteData));

            // Redirect to paste link (demo: /paste/{id})
            window.location.href = '/paste/' + id;
            return false;
          }
        }, 50);
      } else if (page === 'search') {
        content.innerHTML = `
          <h1>Search Pastes</h1>
          <p>Search feature will be available soon.<br><br>We're building something awesome.</p>`;
      } else if (page === 'tos') {
        content.innerHTML = `
          <h1>Terms of Service (TOS)</h1>
          <p>
            By using Cyxium, you agree to the following terms and conditions. These rules are here to ensure a safe, fair, and abuse-free environment for all users.<br><br>
            <strong> Forbidden Content:</strong><br>
            - Harassment, threats, or any form of targeted abuse<br>
            - NSFW, explicit, or offensive adult material<br>
            - Spam, advertisements, or automated mass-pasting<br><br>
            <strong> Allowed Content:</strong><br>
            - Scripts, cheats, tools, and code sharing are allowed<br>
            - You are free to upload content related to scripting, game modifications, or automation, as long as it does not violate the points above<br><br>
            <strong> Responsibility:</strong><br>
            - You are responsible for the content you share<br>
            - Cyxium staff reserves the right to remove any paste or ban users who break the rules<br><br>
            By continuing to use Cyxium, you agree to these terms.
          </p>`;
      }
    }

    // OPTIONAL: Handle /paste/:id page (basic demo)
    window.addEventListener('DOMContentLoaded', () => {
      // If on /paste/:id, show the paste
      const match = location.pathname.match(/^\/paste\/([a-z0-9]+)/i);
      if (match) {
        const id = match[1];
        const data = localStorage.getItem('cyxium_paste_' + id);
        let html = `<h1>Paste Not Found</h1><p>This paste does not exist.</p>`;
        if (data) {
          const paste = JSON.parse(data);
          html = `
            <h1>${paste.title ? escapeHtml(paste.title) : 'Untitled Paste'}</h1>
            <p style="color:#00ffff;">${paste.tag ? '#' + escapeHtml(paste.tag) : ''}</p>
            <p style="color:#ccc;font-style:italic;margin-bottom:18px;">${paste.description ? escapeHtml(paste.description) : ''}</p>
            <pre style="text-align:left;background:#181c23;border-radius:8px;padding:18px;overflow-x:auto;white-space:pre-wrap;font-size:15px;line-height:1.5;color:#e2e2e2;">${escapeHtml(paste.content)}</pre>
            <p style="margin-top:16px;color:#777;font-size:15px;">Created at: ${new Date(paste.created).toLocaleString()}</p>
          `;
        }
        document.querySelector('.content').innerHTML = `<div class="page-box">${html}</div>`;
      }
    });

    // Simple escape for HTML
    function escapeHtml(text) {
      return text.replace(/[<>"'&]/g, function(match) {
        return ({
          '<': '&lt;',
          '>': '&gt;',
          '"': '&quot;',
          "'": '&#039;',
          '&': '&amp;'
        })[match];
      });
    }
  </script>
</body>
</html>