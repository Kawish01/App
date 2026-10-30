/* Custom Styles for Horizon Academy */
html {
  scroll-behavior: smooth;
}

.academic-tab.active {
  background-color: #2563eb !important;
  color: #ffffff !important;
  box-shadow: 0 4px 12px rgba(37, 99, 235, 0.25);
}

.tab-content {
  animation: fadeIn 0.3s ease-in-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(6px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
// Main JavaScript Functionality for Horizon Academy Website

document.addEventListener('DOMContentLoaded', () => {
  // 1. Mobile Menu Toggle
  const mobileBtn = document.getElementById('mobile-menu-btn');
  const mobileMenu = document.getElementById('mobile-menu');

  if (mobileBtn && mobileMenu) {
    mobileBtn.addEventListener('click', () => {
      mobileMenu.classList.toggle('hidden');
    });
  }

  // 2. Academic Tabs Switching
  const tabs = document.querySelectorAll('.academic-tab');
  const tabContents = document.querySelectorAll('.tab-content');

  tabs.forEach(tab => {
    tab.addEventListener('click', () => {
      const targetId = tab.getAttribute('data-target');

      // Update Active Tab Button
      tabs.forEach(t => t.classList.remove('active', 'bg-blue-600', 'text-white'));
      tabs.forEach(t => t.classList.add('bg-white', 'text-slate-700'));
      
      tab.classList.add('active');
      tab.classList.remove('bg-white', 'text-slate-700');

      // Hide all contents and display targeted content
      tabContents.forEach(content => {
        content.classList.add('hidden');
      });

      const activeContent = document.getElementById(`tab-${targetId}`);
      if (activeContent) {
        activeContent.classList.remove('hidden');
      }
    });
  });

  // 3. Fee Estimator Calculation
  const gradeSelect = document.getElementById('grade-select');
  const transportCheck = document.getElementById('transport-check');
  const feeTotal = document.getElementById('fee-total');

  function updateFee() {
    if (!gradeSelect || !feeTotal) return;
    let baseFee = parseInt(gradeSelect.value, 10);
    if (transportCheck && transportCheck.checked) {
      baseFee += 4000;
    }
    feeTotal.textContent = `PKR ${baseFee.toLocaleString()}`;
  }

  if (gradeSelect) gradeSelect.addEventListener('change', updateFee);
  if (transportCheck) transportCheck.addEventListener('change', updateFee);

  // 4. Contact Form Submission Handling
  const contactForm = document.getElementById('contact-form');
  const formAlert = document.getElementById('form-alert');

  if (contactForm && formAlert) {
    contactForm.addEventListener('submit', (e) => {
      e.preventDefault();
      formAlert.classList.remove('hidden');
      contactForm.reset();
      setTimeout(() => {
        formAlert.classList.add('hidden');
      }, 5000);
    });
  }
});
# Horizon Academy Website

A responsive, multi-file modern school web application built with HTML5, Tailwind CSS, JavaScript, and FontAwesome icons. Ready for direct deployment on **GitHub Pages**.

## File Structure
- `index.html`: Main website structure and layout.
- `style.css`: Custom animations and active tab styles.
- `script.js`: Interactive elements (mobile drawer, tab system, tuition fee estimator, contact form).
- `README.md`: Project documentation and GitHub deployment instructions.

## Deployment Steps on GitHub Pages

1. **Create Repository:**
   - Go to [GitHub](https://github.com) -> **New Repository**.
   - Name it (e.g., `school-website` or `<your-username>.github.io`).

2. **Upload Files:**
   - Click **Add file** -> **Upload files**.
   - Drag and drop `index.html`, `style.css`, `script.js`, and `README.md`.
   - Click **Commit changes**.

3. **Enable GitHub Pages:**
   - Go to **Settings** -> **Pages** (under Code and automation).
   - Under **Source**, select `Deploy from a branch`.
   - Set Branch to `main` (or `master`) and folder to `/ (root)`.
   - Click **Save**.

4. **Access Your Live Link:**
   - GitHub will generate your free site URL: `https://<your-username>.github.io/<repository-name>/`
