# Week 3 — Map It & Give It a Face

**Assignment:** Map It & Give It a Face  
**Portfolio owner:** Muhammed Aamir  
**Repository:** `mhdaamiryo/fly-ml`  
**Status:** Content map and visual identity planned; final project screenshots to be captured during implementation.

---

## 1. Portfolio identity

### One-line positioning

> I build practical solutions using machine learning, AI and web technologies, turning ideas into working projects.

### Purpose

The portfolio will present a small selection of meaningful work, explain the problem and my contribution, and make it easy for a recruiter, mentor or collaborator to explore the evidence.

### Intended audience

- Internship and entry-level software/ML recruiters
- Developers and potential collaborators
- Mentors and people interested in my projects

### Design principle

**The design should frame the work, not compete with it.** The interface will be clean and restrained. Project screenshots, explanations, working demos and code links should receive more attention than decorative effects.

---

## 2. Content map

The first version will be a responsive, single-page portfolio with clear navigation links to anchored sections. This keeps the experience simple and makes it easier to maintain.

| Section | Content | Main action |
|---|---|---|
| Hero | Name, positioning statement and short introduction | Explore projects |
| Selected work | A curated set of project cards with concise descriptions | View project |
| About | Education, interests, technologies and learning direction | Read about me |
| Experience | FlyRank ML internship work and relevant responsibilities | View evidence |
| Contact | GitHub, LinkedIn and email details | Get in touch |

### Suggested hero copy

**Muhammed Aamir**  
*Computer Science & Engineering student building with AI, machine learning and web technologies.*

I enjoy learning by building. This portfolio highlights selected projects, the decisions behind them and the work involved in turning ideas into functioning applications.

### Navigation

Home · Projects · About · Experience · Contact

### Calls to action

- **Primary:** Explore Projects
- **Secondary:** Contact Me
- Project-level: View Code · Live Demo · Read Case Study

Only show a Live Demo button when a working, publicly accessible demo exists. Do not use placeholder links.

---

## 3. Project selection — quality over quantity

The portfolio will not be a list of every exercise or tutorial. Small beginner projects are intentionally excluded so that the selected work has enough substance to discuss.

### Selected projects

| Project | Portfolio priority | What it can demonstrate | Evidence to show |
|---|---|---|---|
| FlyRank ML internship — search intelligence data contract | Featured | Working with a large dataset, data validation, feature engineering, leakage awareness and analytical judgment | Notebook screenshots, data-contract explanation, verification results and GitHub notebook |
| Two Good Co homepage recreation | Supporting | Frontend implementation, layout, styling and attention to visual detail | Full-page screenshot and selected responsive/component screenshots |
| SchoolPage — Sri Sai Inter College | Supporting, once presentable | React-based website development, UI structure and enquiry-form integration | Current website screenshots and a working demo if available |

### Conditional projects

These should be added only if the final result is complete enough to demonstrate clearly.

| Project | Decision rule |
|---|---|
| Smart Cart prototype | Include if the user flow is understandable and the prototype has a convincing visual demonstration. Label it clearly as a prototype. |
| Java Auction System | Include if the application runs reliably and its Java Swing interface and database functionality can be demonstrated. |

### Explicitly excluded

The following beginner projects will not appear in the main portfolio or resume:

- AAMIR.AI terminal chatbot
- Iris classification
- Course recommendation project

They were useful learning exercises, but they do not currently provide enough distinctive evidence for the portfolio's intended purpose.

### Project-card content standard

Every published project should answer these questions:

1. **What is it?** A one- or two-sentence explanation.
2. **Why did I build it?** The problem, task or learning objective.
3. **What did I do?** My actual contribution and important decisions.
4. **What did I use?** The relevant technologies, not an inflated skills list.
5. **What is the evidence?** Screenshots, results, code or a live demo.
6. **What are the limitations?** Be clear if it is a clone, prototype, internship exercise or unfinished project.

---

## 4. Visual identity

### Overall direction

**Minimal · Modern · Technical · Approachable**

The portfolio should feel like a thoughtful developer's workspace rather than a flashy agency landing page. Use whitespace, clear hierarchy and restrained motion.

### Colour palette

| Role | Colour | Hex |
|---|---|---|
| Primary accent | Muted blue | `#315C8C` |
| Main background | Off-white | `#F7F8FA` |
| Main text | Near-black | `#171A1F` |
| Secondary surface | Soft blue | `#DCE8F5` |
| Secondary text | Slate grey | `#667085` |
| Borders | Light grey | `#E5E7EB` |

Use the muted blue for links, buttons and small highlights. Keep most page surfaces neutral so project images remain prominent. Check text contrast before implementation.

### Typography

- **Typeface:** Inter
- **Headings:** Bold or semibold, with clear size differences between page title and section headings.
- **Body:** Regular weight, comfortable line height and readable line length.
- **Labels and metadata:** Smaller text, but never so small that it becomes difficult to read.

### Layout and components

- Responsive content container with consistent spacing.
- Simple top navigation.
- Clear hero section with one primary and one secondary action.
- Project cards with consistent image ratios and concise descriptions.
- Subtle borders and restrained corner rounding.
- Consistent button styles and visible hover/focus states.
- Mobile-first layout; no horizontal overflow.

### Motion

Use motion sparingly: small hover transitions or subtle entrance effects only where they improve feedback. Avoid distracting animations, excessive parallax and effects that delay access to project information.

### Logo / favicon direction

Use a simple **A monogram** based on the first letter of my name. It should work at small sizes, remain legible in one colour and not resemble an unrelated company logo. A text-based wordmark is sufficient for the first version; a complex logo is unnecessary.

---

## 5. Image curation plan

The key decision is whether an image provides **proof** or merely **decoration**.

### Evidence images — use real project captures

| Project | Preferred image | Why this is the right choice |
|---|---|---|
| FlyRank ML | Actual notebook showing the data contract, validation queries or feature/leakage analysis | The real notebook is evidence of the work. A generated dashboard or fake data visual would misrepresent it. |
| Two Good Co recreation | Actual browser screenshot of the implemented page | Shows the real frontend result and visual execution. |
| SchoolPage | Actual screenshot of the implemented website, ideally including a meaningful page section | Lets visitors assess the real interface rather than a concept mockup. |
| Smart Cart, if included | Actual prototype screens showing the user flow | Makes the prototype's functionality and current maturity clear. |
| Java Auction, if included | Actual application screenshot showing a meaningful workflow | Demonstrates the real desktop application. |

### Decorative images — use only when they add value

A small abstract visual, subtle texture or simple geometric accent may be used in the hero section if the page feels too empty. It must not imply a product, result or capability that does not exist.

If an AI-generated decorative asset is used:
- Keep it in the same restrained blue/neutral visual language.
- Avoid fake interfaces, fake charts, fake code and fictional product screenshots.
- Do not use generated images as proof of project completion.
- Use one coherent visual direction rather than mixing unrelated image styles.

### Curation decisions

| Candidate | Decision | Reason |
|---|---|---|
| Real screenshots of my own projects | Select | They provide direct, verifiable evidence. |
| AI-generated screenshots of project interfaces | Reject | They could falsely suggest functionality or progress. |
| Generic stock photos of people coding | Reject | They add little information about my work and make the portfolio less personal. |
| Unrelated futuristic AI artwork | Reject | It distracts from the actual projects and overstates the visual identity. |
| Simple abstract accent, if needed | Optional | Acceptable only as decoration, never as project evidence. |

### Asset capture checklist

Before publishing, capture and review:
- [ ] FlyRank notebook screenshot with sensitive credentials and tokens excluded.
- [ ] Two Good Co page screenshot at desktop width.
- [ ] Two Good Co responsive/mobile screenshot, if available.
- [ ] SchoolPage screenshot showing the actual implemented UI.
- [ ] Smart Cart or Java Auction screenshots only if either project is selected.
- [ ] Optimised image files with consistent aspect ratios and descriptive filenames.
- [ ] Alt text for meaningful images.

Do not publish private data, access tokens, personal contact information belonging to others, or restricted internship data in screenshots.

---

## 6. Design judgment and rationale

The most important design decisions are deliberate exclusions:

1. **A short project list instead of a project dump.** A few substantial projects are easier to understand and defend than many small exercises.
2. **Real screenshots instead of fabricated visuals.** Evidence must accurately represent what was built.
3. **Neutral backgrounds and restrained accent colour.** The design should make project content easier to inspect.
4. **A single-page structure for version one.** It reduces navigation complexity and keeps the first release achievable.
5. **Honest project labels.** Clones, prototypes, internship exercises and finished applications should be described accurately.
6. **No unnecessary decoration.** Every visual element should improve clarity, navigation or understanding.

### What success looks like

A visitor should be able to understand who I am, identify my strongest work, see evidence of what I personally contributed and find a way to contact me without fighting the design.

---

## 7. Implementation plan after this assignment

This document is the design and content blueprint, not a claim that the website is already built or deployed.

1. Capture the real screenshots for the selected projects.
2. Review the project descriptions and confirm which conditional projects are strong enough to include.
3. Implement the single-page portfolio using React, Vite and Tailwind CSS.
4. Test responsive layouts, links, accessibility and image loading.
5. Deploy the completed site and replace any draft links with working URLs.

### Final self-review

- [x] A clear portfolio positioning statement is defined.
- [x] Website sections and calls to action are mapped.
- [x] Projects are selected based on quality and evidence.
- [x] Beginner projects are intentionally excluded.
- [x] A consistent colour, typography and layout direction is defined.
- [x] Real evidence images are prioritised over generated images.
- [x] Image rejection decisions are documented.
- [ ] Actual project screenshots have been captured and added.
- [ ] Portfolio website has been implemented and deployed — **outside the scope of this planning document**.

---

**Submission note:** This document records the portfolio's content strategy, visual identity and image-selection judgment. The actual screenshots and website implementation are follow-up work; they are not represented as completed here.
