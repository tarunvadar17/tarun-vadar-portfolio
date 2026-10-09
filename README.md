# Tarun Vadar — Portfolio Site (Full Guide)

A cinematic, streaming-style portfolio for **Tarun Vadar**, Computer Science and Technology student at Presidency University, Bengaluru.

Every section is an "episode" and every project is an "Original". The whole site is built from one data file, so you rarely need to touch the code.

---

## 1. What's on the site

| Section | What visitors see |
| --- | --- |
| **Hero** | Your photo, name, tagline, and buttons to play the intro or view your resume |
| **Play Intro** | A short highlight reel of your education, skills, internship, projects and certificates. Controls: Space pauses, ← and → change slides, Esc closes |
| **Continue Watching** | Cards that link to the main sections |
| **About (The Pilot)** | Your intro and profile |
| **My Journey** | Seasons and episodes: school, diploma, jobs, internships, B.Tech, and what's next |
| **My Projects (Originals)** | Project cards. Click one to open the full details |
| **Top Picks** | A row of six highlights from your resume |
| **My Skills** | Skill categories. Hover or tap a skill to see where it appears |
| **My Achievements** | Internships and innovation projects, plus your certificates |
| **Resume** | View your resume PDF in the site, or download it |
| **Contact** | Email, LinkedIn and GitHub buttons |

The site also has a **Who's watching?** screen with profiles (Tarun, Recruiter, Developer, Creative). Each profile changes the order of the sections. You can switch between them with the profile icon at the top right.

---

## 2. Requirements

You need these on your computer before you start:

1. **Node.js 18 or newer.** Download the **LTS** version from nodejs.org and install it with the default settings.
2. **PowerShell.** It's already on Windows. Press the Windows key, type `PowerShell`, and open **Windows PowerShell**.

To check Node is installed, run:

```powershell
node -v
```

It should show `v18` or higher.

---

## 3. Folder layout

Your project is in this folder:

```
C:\Users\simio\Documents\tarun-portfolio\tarun-portfolio\
```

Inside it, the important files are:

```
src\data\portfolio.ts        ← ALL your content (edit this)
src\App.tsx                  ← page flow and profiles
src\components\              ← how each section looks (rarely needs editing)
public\assets\               ← resume PDF and portrait images
pic1.jpeg                    ← your high-resolution photo
pic.png                      ← your photo with the background removed
package.json                 ← project settings (don't edit)
dist\                        ← created when you build; this is the published site
```

Note the double folder name `tarun-portfolio\tarun-portfolio`. Always run commands from the inner one.

---

## 4. Run the site on your computer

Open PowerShell and run these commands one at a time:

```powershell
cd "C:\Users\simio\Documents\tarun-portfolio\tarun-portfolio"
npm install
npm run dev
```

- `npm install` downloads the required packages. It takes a minute or two. You only need to run it once, or again after the project changes.
- `npm run dev` starts the site. PowerShell shows a line like `Local: http://localhost:5173/`.
- Open that address in your browser.
- To stop the site, click the PowerShell window and press **Ctrl + C**.

The security warning "2 high severity vulnerabilities" that appears after `npm install` is common in development tools. Don't run `npm audit fix --force`, because it can break the site.

---

## 5. Edit your content

Almost everything is in **`src\data\portfolio.ts`**. Open it in Notepad or VS Code. Each block is a list of items you can edit.

### 5.1 Your profile

```ts
export const profile = {
  fullName: 'Tarun Vadar',
  role: 'Computer Science Student',
  tagline: ['Computer Science', 'Python & Java', 'Web Development'],
  intro: 'A B.Tech Computer Science & Technology student...',
  location: 'Bengaluru, India',
  email: 'tarunvadar17@gmail.com',
  links: {
    linkedin: 'https://www.linkedin.com/in/tarun-vadar-516b4627b',
    github: 'https://github.com/tarunvadar17',
  },
  ...
};
```

- **Change the text** between the single quotes. Keep the quotes and the commas.
- The three-part `tagline` shows as three short labels under your name.

### 5.2 Education

Each school is one block:

```ts
{
  school: 'Presidency University',
  place: 'Bengaluru',
  degree: 'B.Tech — Computer Science and Technology',
  period: '2024 – 2027',
  score: 'In progress',
},
```

To add a school, copy a whole block (from `{` to `},`), paste it into the list, and change the values.

### 5.3 Work and internships

```ts
{
  company: 'Datamatics Business Solutions',
  role: 'Associate – Lead Verification',
  place: 'Mumbai, Maharashtra',
  period: 'Nov 2023 – Jun 2024',
  points: ['Verified data for accuracy and completeness.'],
},
```

- `points` is a list of bullet points. Add more inside the square brackets, separated by commas. Leave it as `[]` if you have none.

### 5.4 Projects

Each project is a card. Add details as they become available:

```ts
{
  id: 'edge-ai',
  title: 'Edge AI',
  year: 'B.Tech',
  genre: 'AI • Edge Computing',
  logline: 'A one-line summary that shows on the card.',
  stack: ['Python', 'TensorFlow'],
  build: [
    'What you built, in one sentence.',
    'Another detail, such as a feature or challenge.',
  ],
  features: [],
  metrics: [],
  github: 'https://github.com/tarunvadar17/edge-ai',   // optional
  palette: { from: '#2a0610', via: '#7a0f24', to: '#0b0710', accent: '#ff3d5a' },
  motif: 'shield',
},
```

- `stack` is the list of tools. Each one appears as a tag.
- `build` is the list of details shown in the project window.
- `features` and `metrics` can stay empty (`[]`). If you have numbers, use `metrics`, for example:
  `metrics: [{ value: '92%', label: 'Accuracy' }],`
- `github` is optional. Leave the line out if the project has no public repository. Then the GitHub button doesn't appear.
- `motif` can be `'shield'`, `'flow'` or `'tenants'`. It only changes the artwork.
- `palette` sets the colours. You can change the hex codes, or copy one from another project.

**Currently listed:** Edge AI, Raspberry Pi Innovation Project, Arduino Innovation Project. These need details (see section 9).

### 5.5 Achievements and certificates

```ts
// achievements
{
  id: 'aiml-internship',
  title: '2-Month AI/ML Internship',
  org: 'Internship',
  detail: 'Completed a two-month internship in AI and Machine Learning.',
  laurel: 'AI / ML',
},

// certifications
{ issuer: 'SSC', name: 'SSC Certificate in .NET Technology', link: '' },
```

- Add a certificate link by putting the web address between the quotes after `link:`. For example:
  `link: 'https://example.com/your-certificate',`
- If a certificate has no link, leave the quotes empty.

### 5.6 Skills

```ts
{
  id: 'languages',
  title: 'Languages',
  subtitle: 'Python and Java lead the list',
  skills: [
    { name: 'Python', mono: 'Py', note: 'Core' },
    { name: 'Java', mono: 'Jv' },
  ],
},
```

- `mono` is the two-letter badge shown on the skill card.
- `note` is optional and shows a small label such as "Core".

To make a skill's hover or tap text show where it's used, add it to `skillEvidence` with the same name:

```ts
'Python': ['Edge AI project', 'Mini project: Java'],
```

Only add facts that appear on your resume or in your projects.

### 5.7 My Journey (seasons and episodes)

```ts
{
  number: 1,
  title: 'The Beginning',
  period: '2020 – 2023',
  synopsis: 'SSC in Mumbai, then a Diploma in Computer Science Engineering.',
  episodes: [
    {
      code: 'S01 E01',
      title: 'The Foundation',
      description: 'SSC at S.V.P.V, Mumbai, completed in 2020.',
      tags: ['SSC', 'Mumbai'],
      runtime: '2020',
      palette: amber,
    },
  ],
},
```

- `runtime` is the short label on the episode, usually the dates.
- To add an episode, copy an existing one and change the values. Give it the next code, such as `S02 E04`.
- `palette` uses one of the colour names defined above in the same file: `crimson`, `amber`, `ocean`, `violet`, or `jade`.

### 5.8 Top Picks

```ts
{ label: 'Core language', title: 'Python', detail: 'Also Java, C, C++, C# and PHP', palette: amber },
```

- Keep six picks for the best layout.

### 5.9 Play Intro slides

```ts
{
  kicker: 'Education',
  title: 'B.Tech · CS&T',
  lines: ['Presidency University, Bengaluru', '2024 – 2027'],
},
```

- `kicker` is the small label, `title` is the large heading, and `lines` are the supporting lines.
- `chips` (optional) shows small tags, for example `chips: ['Python', 'Java']`.

---

## 6. Save, check and rebuild

After any change:

1. Save the file in Notepad (**Ctrl + S**).
2. If `npm run dev` is running, the browser updates automatically. Check the page.
3. To make a final version for publishing, stop the dev server with **Ctrl + C**, then run:

```powershell
npm run build
```

If the build fails, the message names the file and line. Fix that line and run the build again.

---

## 7. Replace the photo

Use a clear, well-lit headshot. A plain background makes the background removal cleaner.

1. Put your high-resolution photo in the project folder as `pic1.jpeg`.
2. Remove the background and save the result as `pic.png`. You can use a free online tool such as remove.bg, then download the PNG with a transparent background.
3. Run:

```powershell
npm run images
```

This creates new portrait files in `public\assets\`. Check the homepage afterwards.

If `npm run images` fails because the `sharp` package isn't installed, run `npm install` first and try again.

---

## 8. Replace the resume

1. Save your new resume as a PDF.
2. Rename it to `Tarun_Vadar_Resume.pdf`.
3. Copy it into `public\assets\`, replacing the old file.

The site's "View Resume" and "Download" buttons will use the new file.

---

## 9. Still to add

Your resume doesn't give details for these, so the site currently shows only names:

- **Project details** for Edge AI, the Raspberry Pi project and the Arduino project: a description, tools used, and any results or numbers.
- **Certificate links** for the four certificates.
- **Mini projects** (DBMS, SEO, IoT, Java): these are mentioned in the timeline and intro slides but don't have their own cards yet.
- **LinkedIn and GitHub:** already added. If you change them, see section 5.1.

---

## 10. Publish the site on Netlify

Netlify hosts your site for free and gives you a public link you can open on any phone.

### First time

1. Run `npm run build` in the project folder. This creates the `dist` folder.
2. Open your browser and go to **app.netlify.com/drop**.
3. Sign up or log in. A free account is enough.
4. Drag the **`dist`** folder (the whole folder, not the files inside it) onto the box on the page.
5. Wait a few seconds. Netlify shows a link like `https://random-name.netlify.app`.
6. Open the link on your phone to check it.

### Change the link name

1. On Netlify, click your site.
2. Open **Site configuration** (or **Project configuration**). On some screens it's under **Site settings**.
3. Under **Site information**, click **Change site name**.
4. Enter a name such as `tarun-vadar`. Use only letters, numbers and hyphens.
5. Your link becomes `https://tarun-vadar.netlify.app`. If the name is taken, try another one.

### Update the site after changes

1. Make your changes and run `npm run build`.
2. On Netlify, open your site and go to the **Deploys** tab.
3. Drag the new `dist` folder onto the deploy area.

The link stays the same.

---

## 11. Troubleshooting

| What you see | What to do |
| --- | --- |
| `package.json` not found | You're in the wrong folder. Run `cd "C:\Users\simio\Documents\tarun-portfolio\tarun-portfolio"` |
| `npm` is not recognised | Node.js isn't installed or PowerShell was open before you installed it. Install Node.js LTS, then close and reopen PowerShell |
| "Connection refused" in the browser | The site isn't running. Check PowerShell for the `Local:` address and use exactly that address |
| The page is blank | Make sure `npm run dev` is still running. Press F12 in the browser, open the **Console** tab, and read the first red message |
| `Cannot find module` or a missing package | Run `npm install` again |
| Build error mentioning a TypeScript file | Copy the first red line. It names the file and line to check |
| Photo doesn't appear | Check that `pic.png` is in the project folder, then run `npm run images` |
| Blank page after publishing | Drag the `dist` folder itself, not the files inside it |
| Link name already taken on Netlify | Choose another name, such as `tarunvadar-portfolio` |

---

## 12. Keyboard shortcuts

- **Opening sequence:** Enter or Esc skips it
- **Play Intro:** Space pauses, ← and → change slides, Esc closes
- **Project and resume windows:** Esc closes

---

## 13. Built with

React 18, TypeScript, Vite 6, Tailwind CSS 4, Framer Motion 11, Lenis (smooth scrolling)
