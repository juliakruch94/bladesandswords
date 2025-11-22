# Runes & Swords – Game Documentation Repository

This repository contains production-ready documentation, technical specifications, and development standards for the project **Runes & Swords**, a turn-based narrative RPG inspired by tabletop mechanics.

The repo serves as the *single source of truth* for all project-related documents used by Design, Programming, Art, QA, and Production teams.

---



## 📁 Repository Structure

```plaintext
docs/
 └── gdd/
      └── Game_Design_Document.md

tech_specs/
 ├── Core_Systems_Spec.md
 └── Architecture_Overview.md

features/
 └── Feature_Template.md

qa/
 └── QA_Release_Checklist.md

publishing/
 └── Publishing_Requirements.md
```

---

## 📌 Purpose

This repository ensures that:

- All teams follow consistent documentation standards  
- Feature specs and rulebooks are easily accessible  
- Technical decisions are centralized and trackable  
- Release and QA criteria remain transparent  
- Publishing/legal requirements stay versioned  

---

## 🗂 Linked External Docs

These documents are maintained in **Confluence**, with smart links placed in Miro:

- **GDD**  
- **Technical Specifications**  
- **QA & Release Checklist**  
- **Feature Specification**  
- **Publishing Requirements**  

> If you update any Confluence title, remember to re-paste the link in Miro to refresh its smart-link metadata.

---

## 🔧 Branching Model

This project uses a lightweight branching strategy:

- **main** — production-ready documentation only  
- **dev-docs** — active work on new documentation  
- **feature/*** — optional per-feature docs updates  
- **release/*** — locked branches for milestone polishing  
- **archive/** — frozen folders for deprecated or legacy docs  

All merges into `main` must pass Producer/Technical Lead review.

---

## 🧭 Maintainers

- **Producer:** Yuliia Kriuchkova  
- **Technical Lead:** *<name>*  
- **Game Director:** *<name>*  
- **Art Director:** *<name>*  
- **QA Lead:** *<name>*  

---

## ✔ Contribution Rules

- Commit meaningful, descriptive messages  
- Keep documentation modular (one file = one topic)  
- Avoid large unstructured text blocks  
- Update diagrams separately in Miro when needed  
- All major design changes must also be reflected in the GDD  

---

## 📜 License

Internal studio documentation. Not intended for public distribution.

