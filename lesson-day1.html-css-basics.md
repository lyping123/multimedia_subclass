# Day 1 — HTML & CSS Foundations (24/11/2025, Monday)

## 1. Learning Outcomes
By the end of today, students will be able to:
1. Describe the basic structure of an HTML document (`<!doctype html>`, `<html>`, `<head>`, `<body>`).
2. Use common HTML elements: headings, paragraphs, images, buttons, forms, containers (`<div>`, `<section>`).
3. Apply key attributes: `class`, `id`, `type`, `name`, `placeholder`, `alt`.
4. Explain and apply basic CSS for color, spacing, alignment, fonts, borders.
5. Build and style a simple user input form (text, email, select, textarea, submit button).
6. Trigger a basic event (button click) that gives feedback using JavaScript.

## 2. Suggested Schedule (60–75 min)
| Time | Segment | Purpose |
|------|---------|---------|
| 0–5  | Welcome & Objectives | Set expectations |
| 5–15 | HTML Structure Intro | Skeleton + common tags |
| 15–25| Attributes & Semantics | Meaning + accessibility basics |
| 25–35| CSS Fundamentals | Selectors, properties demo |
| 35–45| Form Construction Demo | Build + explain each input |
| 45–60| Student Activity | Create + style form, add button effect |
| 60–70| Add Simple JS Event | Click handler + basic validation |
| 70–75| Review & Exit Ticket | Reinforce learning |

## 3. Core Concepts Cheat Sheet
- Document Skeleton: `<!doctype html>` ensures standards mode.
- Block vs Inline: `<div>`, `<p>`, `<section>` vs `<span>`, `<a>`, `<img>`.
- Attributes: `class` (styling hook), `id` (unique element), `name` (form data key), `placeholder` (hint text), `type` (input behavior), `alt` (image description for accessibility).
- CSS Rule: `selector { property: value; }`
- Common CSS Properties: `color`, `background`, `margin`, `padding`, `border`, `font-size`, `display`, `width`, `text-align`.
- Events: User actions like `click`, `focus`, `submit`, `mouseover`. Handled via JS or CSS pseudo-classes (`:hover`, `:focus`).

## 4. Live Demo Walkthrough
### 4.1 Minimal HTML Page
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Day 1 Demo</title>
  <link rel="stylesheet" href="styles-demo.css" />
</head>
<body>
  <header>
    <h1>Welcome to the Aquarium Form</h1>
    <p class="intro">Today we learn HTML & CSS basics.</p>
  </header>

  <section id="info">
    <h2>About</h2>
    <p>This page collects visitor interests for future events.</p>
    <img src="image/reef.jpeg" alt="Colorful coral reef" width="300" />
  </section>

  <section id="signup" aria-label="Visitor interest form">
    <h2>Sign Up</h2>
    <form id="interestForm" action="#" method="post">
      <div class="field">
        <label for="name">Name</label>
        <input type="text" id="name" name="name" placeholder="Your full name" required />
      </div>
      <div class="field">
        <label for="email">Email</label>
        <input type="email" id="email" name="email" placeholder="you@example.com" required />
      </div>
      <div class="field">
        <label for="favorite">Favorite Exhibit</label>
        <select id="favorite" name="favorite">
          <option value="reef">Coral Reef</option>
          <option value="shark">Sharks</option>
          <option value="jellyfish">Jellyfish</option>
        </select>
      </div>
      <div class="field">
        <label for="comments">Comments</label>
        <textarea id="comments" name="comments" rows="4" placeholder="Any interests or questions..."></textarea>
      </div>
      <button type="submit" class="primary-btn">Submit</button>
    </form>
    <div id="message" class="hidden" role="alert"></div>
  </section>

  <script src="demo.js"></script>
</body>
</html>
```

### 4.2 Basic Styles (`styles-demo.css`)
```css
*{box-sizing:border-box;font-family:system-ui,Arial,sans-serif;}
body{margin:0;background:#f5fbff;color:#0f2233;line-height:1.5;padding:1rem;}
header{text-align:center;padding:1rem 0;margin-bottom:1rem;background:#ffffff;border:1px solid #d9e6f2;border-radius:.5rem;}
.intro{color:#4b6476;}
section{max-width:720px;margin:0 auto 1.5rem;padding:1rem;background:#ffffff;border:1px solid #d9e6f2;border-radius:.5rem;}
#info img{display:block;margin:0.5rem auto;border-radius:.5rem;border:2px solid #89c8ff;}
form{display:grid;gap:1rem;}
.field{display:grid;gap:.35rem;}
label{font-weight:600;}
input,select,textarea{padding:.6rem .7rem;border:1px solid #b7c9d9;border-radius:.5rem;font-size:1rem;background:#fdfdfd;}
input:focus,select:focus,textarea:focus{outline:2px solid #0077ff;background:#ffffff;}
.primary-btn{cursor:pointer;padding:.7rem 1.1rem;font-size:1rem;border:none;border-radius:.6rem;background:#0077ff;color:#fff;font-weight:600;transition:background .3s, transform .15s;}
.primary-btn:hover{background:#005fcc;}
.primary-btn:active{transform:scale(.96);}
#message{margin-top:1rem;padding:.8rem 1rem;border-radius:.5rem;border:1px solid #0077ff;background:#e6f2ff;}
.hidden{display:none;}
@media (max-width:600px){body{padding:.5rem;}section{padding:.8rem;}form{gap:.75rem;}}
```

### 4.3 Simple JavaScript (`demo.js`)
```javascript
const form = document.getElementById('interestForm');
const message = document.getElementById('message');

form.addEventListener('submit', function(e){
  e.preventDefault(); // stop real submission for demo
  const name = form.name.value.trim();
  const favorite = form.favorite.value;
  if(!name){
    message.textContent = 'Please enter your name.';
    message.classList.remove('hidden');
    message.style.borderColor = '#cc3300';
    return;
  }
  message.textContent = `Thanks, ${name}! We noted your interest in ${favorite}.`; 
  message.classList.remove('hidden');
  form.reset();
});
```

## 5. Teaching Notes & Talking Points
- Emphasize separation of concerns: HTML (structure), CSS (presentation), JS (behavior).
- Show how `required` attribute performs built‑in validation.
- Highlight accessibility: `alt` for images, `label for` pairs, meaningful button text.
- Discuss progressive enhancement: page works without JS; JS adds feedback.

## 6. Guided Student Activity (Core)
1. Create a new HTML file `day1-form.html` with skeleton + a heading.
2. Add a paragraph describing the form purpose.
3. Insert an image with `alt` text from the provided `image/` folder.
4. Build a form: name (text), email (email), select (3 options), comments (textarea), submit button.
5. Link a new CSS file and style: background color, section borders, spacing.
6. Add hover effect to the button.
7. Add JavaScript file with a submit event that shows a custom thank‑you message.

### Stretch Goals (Optional)
- Add a second button that clears the form.
- Add a simple character counter for the textarea.
- Use `:focus-visible` for improved keyboard focus styling.
- Introduce a subtle keyframe animation on button hover (pulse). 

## 7. Quick Reference Snippets
- Linking CSS: `<link rel="stylesheet" href="styles-demo.css" />`
- Linking JS: `<script src="demo.js"></script>` (near end of `body`).
- Button hover (CSS): `.primary-btn:hover { background:#005fcc; }`
- Textarea attribute: `<textarea rows="4" placeholder="Your message..."></textarea>`

## 8. Assessment (Exit Ticket)
Ask students to answer (verbally or on a card):
1. Name two differences between `id` and `class`.
2. What does `placeholder` do in an input?
3. Where should CSS and JS links typically be placed?
4. Describe one way CSS can improve accessibility.

## 9. Homework
Create a personal feedback form:
- Fields: Name, Email, Favorite Animal, Short Feedback.
- Style with at least: custom background color, padded inputs, a hover effect on submit.
- Add JS: On submit, prevent default and show a thank‑you message including the favorite animal.
- BONUS: Add basic validation ensuring all fields are not empty.

## 10. Common Mistakes to Watch
| Mistake | Fix |
|---------|-----|
| Forgetting `<!doctype html>` | Always start with it to enable standards mode |
| Missing `alt` on images | Add descriptive `alt` text for accessibility |
| Using `<br>` repeatedly for spacing | Use CSS margin/padding instead |
| Inline styles everywhere | Prefer external stylesheet for scalability |
| Not resetting form after feedback | Call `form.reset()` when desired |

## 11. Instructor Checklist
- [ ] Objectives visible at start
- [ ] Demo files prepared (`styles-demo.css`, `demo.js`)
- [ ] Image assets accessible
- [ ] Students create file from scratch (avoid copy-paste at first)
- [ ] Reinforce accessibility and semantics
- [ ] Collect exit ticket answers

## 12. Extension Ideas (If Time Left)
- Add a Google Font (e.g., `Poppins`) and compare default vs custom.
- Introduce CSS variables for colors.
- Show form field states (`:focus`, `:disabled`, `:valid`, `:invalid`).

---
Feel free to modify timings based on class pacing. Keep explanations concise; let students build early and often.
