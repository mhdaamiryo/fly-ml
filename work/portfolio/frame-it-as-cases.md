# Frame It as Cases — Portfolio Draft

> **Status:** Working portfolio draft. The cases below are based on project notes and repository material available at the time of writing. Update any status that has changed before publishing this as a final portfolio.

## Voice card

**Direct, practical, curious, honest, simple, grounded.**

Write in clear everyday English. Keep the focus on the problem, the decisions I made, and what I learned or built. Avoid corporate buzzwords, inflated claims, and results I cannot prove. If a project is still a prototype or in progress, say so.

---

# Selected work

## 1. Content Refresh — FlyRank ML Internship

**Status:** In progress  
**Focus:** Applied machine learning, ranking, search performance

### The problem

Content and SEO teams can have many webpages to review, but limited time to decide which ones deserve attention first. Looking only at content age or one search metric can miss important signals. An old page may still perform well, while a recently updated page may be losing visibility.

### What I did

I chose the Content Refresh lane in the FlyRank ML internship. I framed the problem as a **ranking task**: the aim is to produce an ordered list of webpages for human review, rather than simply label every page as good or bad.

I explored the anonymized starter dataset, which contains 30,000 pseudonymized content records and 44 columns. The available signals include content age, impressions, clicks, CTR, average search position, and engagement measures.

For the Week 3 data-contract exercise, I worked with the gated warehouse's March 2026 daily performance data. I verified the source grain (no duplicate date-client-content keys), checked the month's coverage and GA4 availability, built five search-performance features, and ran a deliberate label-leakage experiment. The experiment showed 73.93% accuracy for a weak honest baseline and 100% when the label itself was incorrectly included as a feature; I then removed that leaked field. These are results from the executed notebook, not claimed production performance.

I also considered how the target should be defined. The ideal target would be a decline observed in a future time window. The starter dataset is a snapshot, so its rule-derived decline label is only a proxy; it is not proof of future decline. This distinction matters when evaluating any model.

For the first framing exercise, I selected **Precision@50** as the success metric. It asks how many of the top 50 recommended pages are relevant for review. An 80% score is a proposed target, not a result I have achieved.

### What came of it

I have a clearly framed ML problem, a defined unit of analysis (one webpage per row), an initial evaluation metric, and a reason to compare ML with a simple fixed rule. The work is still at the problem-framing stage; I am not claiming a trained model or measured improvement from this assignment.

**What I learned:** Before choosing an algorithm, I need to be clear about the decision being improved, what the target really represents, and what evidence would count as success.

**Project:** [FlyRank ML repository](https://github.com/mhdaamiryo/fly-ml)  
**Notebook:** [W02 — Frame Your Lane as an ML Task](https://github.com/mhdaamiryo/fly-ml/blob/main/work/notebooks/w02_ml_task_framing.ipynb)

---

## 2. Two Good Co — Frontend Website Clone

**Status:** Completed practice project  
**Focus:** HTML, CSS, JavaScript, GSAP, responsive frontend

### The problem

When I started learning frontend development, I wanted to move beyond isolated HTML and CSS exercises and understand how a complete modern website is put together.

### What I did

I recreated the Two Good Co website as a frontend practice project. I used HTML, CSS, and JavaScript to build the page structure and styling, and GSAP for animation and interaction. I treated the original site as a reference for practising layout, visual hierarchy, and motion.

This was a learning recreation, not an official website or a commercial project for Two Good Co.

### What came of it

I published the clone on Vercel, giving me a complete project I could open and review in a browser. It helped me practise connecting page structure, styling, animations, version control, and deployment in one piece of work.

**What I learned:** Recreating a real design is a useful way to notice how spacing, layout, responsive behaviour, and animation work together.

**Live demo:** [Two Good Co Clone](https://two-good-clone.vercel.app/)  
**Code:** [GitHub repository](https://github.com/mhdaamiryo/two-good-clone)

---

## 3. SchoolPage — Sri Sai Inter College Website

**Status:** In progress / project build  
**Focus:** React, Vite, Tailwind CSS, Framer Motion, EmailJS

### The problem

A college website needs to present information clearly and give prospective students or parents a straightforward way to make an enquiry. A page that only looks attractive is not enough; the important information and enquiry path also need to be easy to find.

### What I did

I started building a website for Sri Sai Inter College using React and Vite. The project uses Tailwind CSS for styling, Framer Motion for animation, React Icons for interface elements, and EmailJS for the admission enquiry form.

I organised the work as a frontend application rather than a single static HTML page. The enquiry form is intended to give visitors a direct way to contact the college.

### What came of it

The project gives me practical experience building a multi-part React website and connecting a form workflow. I am treating it as a project in progress; I am not claiming a completed launch or a measured increase in admissions.

**What I learned:** A website has to support the visitor's next step, not just display information. Forms and content structure are part of the user experience.

**Code:** [Sri Sai Inter College project repository](https://github.com/mhdaamiryo/project-srisaiintercollege) *(private repository; make public or provide access before using this link in a public portfolio).*

---

## 4. Smart Cart Prototype

**Status:** Prototype  
**Focus:** Form-based workflow, product interaction, early prototyping

### The problem

I wanted to explore a shopping-cart experience and understand how a user could interact with a simple prototype before investing time in a full application.

### What I did

I created an early Smart Cart prototype using Jotform and explored Firebase as part of the technical approach. The work was focused on prototyping the idea and testing a possible user flow, rather than presenting it as a finished production shopping platform.

### What came of it

The prototype helped me practise turning an idea into an initial interactive flow. I do not claim production deployment, real customer usage, or completed payment functionality.

**What I learned:** A prototype can help make an idea more concrete and expose workflow questions before a full implementation.

---

## 5. Java Auction System

**Status:** Academic project  
**Focus:** Java, Swing, SQL, database-backed application

### The problem

An auction workflow needs to represent items, users, and bids in an organised way. I wanted to practise building an application with a graphical interface and a database rather than writing only console-based Java programs.

### What I did

I worked on an Auction System using Java Swing for the graphical interface and SQL for database operations. The project gave me practice connecting application logic with stored data.

### What came of it

The project served as practical experience with Java GUI development and database-backed application structure. I am not claiming that it is a deployed auction service or that it has been used by real bidders.

**What I learned:** Building an application involves more than the interface; the data model and the way the application reads and writes information matter too.

**Code:** [Auction Java repository](https://github.com/mhdaamiryo/auction-java) *(private repository; make public or provide access before using this link in a public portfolio).*

---

# About

I'm Muhammed Aamir, a Computer Science and Engineering student at Viswajyothi College of Engineering and Technology in Kerala.

I enjoy learning by building things. My projects have taken me through Python, beginner machine learning, frontend development, Java, and database-backed applications. I am still developing my skills, so I try to be clear about what I have built, what is a prototype, and what I am still learning.

Right now, I am particularly interested in applied AI and machine learning, practical software development, and building useful web experiences.

# Contact

Have a project idea, an opportunity, or feedback on something I've built? I'd be happy to connect.

- **GitHub:** [github.com/mhdaamiryo](https://github.com/mhdaamiryo)
- **Email:** aamirny443@gmail.com
- **LinkedIn:** https://www.linkedin.com/in/muhammed-aamir-5201a8280/

**CTA:** [Explore my projects on GitHub](https://github.com/mhdaamiryo)

---

# Before and after: making the writing sound like me

### Generic AI version

"I'm a passionate and results-driven developer who leverages cutting-edge technologies to create innovative, scalable solutions that solve real-world problems."

### Edited version

"I'm a CSE student who learns by building. I've worked on small machine-learning projects, websites, and application prototypes. I'm still improving, and I prefer to show what I've actually built rather than make big claims."

### What changed

- Removed vague claims such as "passionate", "results-driven", and "cutting-edge".
- Replaced broad promises with specific areas of work.
- Kept the tone honest about being a student who is still learning.
- Made the writing sound like something I could comfortably say in a conversation.

---

## Final edit checklist

Before publishing this document as the final portfolio:

- [ ] Confirm every project status is still accurate.
- [ ] Add a public email address and LinkedIn URL, if you want them displayed.
- [ ] Decide whether to make the private SchoolPage and Auction repositories public, or remove their code links.
- [ ] Add screenshots or live demos only where they are available and safe to share.
- [ ] Read every paragraph out loud and remove anything that does not sound like me.
- [ ] Keep all performance claims tied to a result I can reproduce or verify.
