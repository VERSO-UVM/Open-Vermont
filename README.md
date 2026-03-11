# Open Vermont

A community-driven platform for Vermonters to surface local challenges, share resources, and build solutions together through open source technology.

**Live site:** [verso-uvm.github.io/Open-Vermont](https://verso-uvm.github.io/Open-Vermont)

---

## What is Open Vermont?

Open Vermont helps communities identify problems worth solving and connects people with the existing resources — organizations, tools, funding, and skills — already available to address them. The platform is built around three activities:

- **Opportunities** — Community members submit challenges they want to see addressed. Others vote to signal priority. Voting uses GitHub reactions (👍) so everything stays transparent and tied to real accounts.
- **Events** — A calendar of maker meetups, open hours, hackathons, and skillshares happening across Vermont.
- **Resources** — A directory of local libraries, makerspaces, UVM Extension offices, and open source references organized by all 14 Vermont counties.

The site is a static HTML/CSS site deployed via GitHub Pages. No framework, no build step — just files.

---

## Project Structure

```
Open-Vermont/
├── index.html          # Homepage with mission statement and code of conduct
├── opportunities.html  # Community opportunity cards with live vote counts
├── events.html         # Upcoming events calendar
├── resources.html      # Resources by Vermont county + open source topics
├── contact.html        # Contact form (Formspree) and GitHub links
├── discussions.html    # Community discussion threads (currently unlinked)
├── styles.css          # Full design system — edit this for all visual changes
├── img/
│   └── hero.jpg        # Homepage hero image
└── .github/
    └── workflows/
        └── static.yml  # GitHub Pages deployment workflow
```

---

## Running Locally

No build tools required. Open any HTML file directly in a browser, or serve with any static file server:

```bash
# Python
python -m http.server 8000

# Node
npx serve .
```

Then visit `http://localhost:8000`.

---

## Adding a New Opportunity

Opportunities are tracked as GitHub Issues with the `opportunity` label.

1. [Open a new issue](https://github.com/VERSO-UVM/Open-Vermont/issues/new) using the opportunity template
2. Add the label **`opportunity`**
3. Note the issue number GitHub assigns (shown in the URL as `/issues/N`)
4. A maintainer reviews the submission (see criteria below) and, if approved, edits `opportunities.html` to add a new `.problem` card with `data-issue="N"`

The page JavaScript will automatically fetch the 👍 reaction count from GitHub and display it as the vote total. Cards are re-sorted by vote count on page load.

**Voting:** Any GitHub user can open the issue and click 👍 to vote. No extra infrastructure required.

### Submission criteria

Good opportunities:
- Describe a real community challenge relevant to Vermonters
- Identify existing resources — organizations, tools, or funding — already available to help address it
- Are framed as challenges to solve collaboratively, not policy demands or partisan positions
- Follow the [Code of Conduct](https://verso-uvm.github.io/Open-Vermont/#conduct)

Maintainers aim to respond within 7 days. Submissions may be approved as-is, returned for edits, or declined with a brief explanation.

---

## Adding an Event

Events are static HTML in `events.html`. To add one:

1. Copy an existing `.event` block
2. Update the date badge, title, location, and description
3. Submit a pull request, or use the [contact form](https://verso-uvm.github.io/Open-Vermont/contact.html) to send the details and a maintainer will add it

---

## Adding a Resource

Resources are organized by Vermont county in `resources.html`. To add a library, makerspace, or organization:

1. Find the appropriate `<div class="resource-section" id="[county]">` block
2. Add a `.resource-item` with the organization name, address, and website
3. Submit a pull request

---

## Contact Form Setup

The contact form in `contact.html` posts to [Formspree](https://formspree.io). To activate it:

1. Create a free Formspree account
2. Create a new form and copy the form ID (looks like `xabcdefg`)
3. In `contact.html`, replace `YOUR_FORM_ID` in the form `action` attribute:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

---

## Deployment

The site deploys automatically to GitHub Pages on every push to `main` via the workflow in `.github/workflows/static.yml`. No manual steps needed.

---

## Contributing

Contributions are welcome — bug fixes, new resources, new opportunities, design improvements.

1. Fork the repository
2. Create a branch: `git checkout -b your-branch-name`
3. Make your changes
4. Open a pull request with a clear description of what changed and why

Please review the [Code of Conduct](https://verso-uvm.github.io/Open-Vermont/#conduct) before contributing. Key points: be respectful, focus on community problem-solving (not partisan framing), and assume positive intent.

---

## Affiliation

Open Vermont is a project of [VERSO](https://verso.w3.uvm.edu) at the University of Vermont. Views expressed by community contributors do not represent the University of Vermont.

---

## License

MIT License — Copyright (c) 2025 Kendall Fortney. See [LICENSE](LICENSE) for details.
