---
layout: default
title: "Home"
---

<!-- 
  Password lock screen + empty sections.
  Fill in the sections later directly in this file.
-->

<div id="lock-screen">
  <div class="lock-card">
    <p class="lock-badge">Private portfolio</p>
    <h1 class="lock-title">Welcome</h1>
    <p class="lock-sub">
      This page is shared selectively  
      Enter the access code I sent you.
    </p>
    <form id="password-form">
      <input
        id="password-input"
        type="password"
        class="lock-input"
        placeholder="Access code"
        autocomplete="off"
        required
      />
      <button type="submit" class="lock-button">Enter</button>
      <div id="lock-error" class="lock-error"></div>
    </form>
    <p class="lock-note">
      If you received this link without a code, you can contact me for access.
    </p>
  </div>
</div>

<div id="site-content" style="display:none;">

<!-- =======================
     ABOUT SECTION (empty)
   ======================= -->

## About

<!-- Write your short bio here later -->


<!-- =======================
     CV SECTION (empty)
   ======================= -->

## CV

<!-- 
Add a link to your CV later, e.g.:

[Download my CV (PDF)](/files/cv_yourname.pdf)
-->


<!-- =======================
     PROJECTS SECTION (empty)
   ======================= -->

## Projects

<!-- 
Add your projects here later as bullet points or subheadings, e.g.:

### Project 1 title  
Short description, tools, link to GitHub repo or dashboard.
-->


<!-- =======================
     WRITING / BLOG SECTION (empty)
   ======================= -->

## Writing / Blog

<!-- 
Add links to Substack / articles later, e.g.:

- [My Substack](https://your-substack-url)
- [Technical note on PISA analysis](#)
-->

</div>

<style>
  /* Full-page overlay */
  #lock-screen {
    position: fixed;
    inset: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem;
    background: radial-gradient(circle at top, #111827 0, #020617 60%);
    z-index: 9999;
  }

  .lock-card {
    max-width: 360px;
    width: 100%;
    background: #020617;
    border-radius: 1.5rem;
    padding: 1.5rem 1.4rem 1.2rem;
    border: 1px solid #1f2937;
    box-shadow: 0 18px 40px rgba(0,0,0,0.7);
    color: #e5e7eb;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  }

  .lock-badge {
    display: inline-block;
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.04em;
    padding: 0.15rem 0.6rem;
    border-radius: 999px;
    border: 1px solid #374151;
    color: #9ca3af;
    margin: 0 0 0.6rem;
  }

  .lock-title {
    margin: 0 0 0.2rem;
    font-size: 1.3rem;
  }

  .lock-sub {
    margin: 0 0 1rem;
    font-size: 0.9rem;
    color: #9ca3af;
  }

  .lock-input {
    width: 100%;
    padding: 0.6rem 0.8rem;
    border-radius: 999px;
    border: 1px solid #374151;
    background: #020617;
    color: #e5e7eb;
    font-size: 0.95rem;
    margin-bottom: 0.6rem;
    outline: none;
  }

  .lock-input:focus {
    border-color: #38bdf8;
  }

  .lock-button {
    width: 100%;
    border-radius: 999px;
    border: none;
    padding: 0.6rem 0.8rem;
    font-size: 0.95rem;
    font-weight: 500;
    background: linear-gradient(135deg, #38bdf8, #22c55e);
    color: #020617;
    cursor: pointer;
    margin-bottom: 0.4rem;
  }

  .lock-button:hover {
    filter: brightness(1.05);
  }

  .lock-error {
    min-height: 1rem;
    font-size: 0.8rem;
    color: #f97373;
  }

  .lock-note {
    margin-top: 0.5rem;
    font-size: 0.75rem;
    color: #9ca3af;
  }
</style>

<script>
  // Simple front-door password (not real security)
  const ACCESS_CODE = "amoomi2025"; // ← change this

  const form = document.getElementById("password-form");
  const input = document.getElementById("password-input");
  const errorBox = document.getElementById("lock-error");
  const lockScreen = document.getElementById("lock-screen");
  const siteContent = document.getElementById("site-content");

  form.addEventListener("submit", function (event) {
    event.preventDefault();
    const value = input.value.trim();

    if (value === ACCESS_CODE) {
      lockScreen.style.display = "none";
      siteContent.style.display = "block";
      sessionStorage.setItem("portfolio_access_granted", "1");
    } else {
      errorBox.textContent = "Incorrect code. Try again.";
      input.value = "";
    }
  });

  const alreadyUnlocked = sessionStorage.getItem("portfolio_access_granted") === "1";
  if (alreadyUnlocked) {
    lockScreen.style.display = "none";
    siteContent.style.display = "block";
  }
</script>
