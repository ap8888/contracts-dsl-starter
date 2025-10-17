# 🧾 Contracts DSL Starter

A modular **TypeScript-based framework** for building, evaluating, and rendering **domain-specific languages (DSL)** for legal and procurement contracts.  
Designed for automation, clause management, and jurisdiction-aware contract generation.

---

## 📂 Project Structure

```
contracts-dsl-starter/
  package.json
  tsconfig.json
  README.md
  LICENSE
  /packages
    /core
      /src
        types.ts
        eval.ts
        clauses.ts
        loader.ts
    /rules
      jurisdiction.nl.json
      procurement.twoEnvelope.json
    /clauses
      clause.governing_law.nl.md
      clause.gdpr.controller_processor.md
      clause.proc.two_envelope.md
      clause.hse.compliance.md
    /render
      /src
        htmlRenderer.ts
        docxRenderer.ts
    /cli
      /src
        index.ts
  /examples
    facts.msa-nl.json
    facts.nda-az.json
  /out
```

---

## 🧠 Core Concept

The system uses a **facts + rules + clauses + renderers** model:

| Component | Description |
|------------|--------------|
| **Facts** | JSON representation of contract metadata, parties, and context (e.g., `facts.msa-nl.json`) |
| **Rules** | JSON definitions for procurement or jurisdictional logic (`jurisdiction.nl.json`, `procurement.twoEnvelope.json`) |
| **Clauses** | Markdown-based reusable legal clauses (`clause.gdpr.controller_processor.md`) |
| **Core** | Type definitions, clause loader, evaluation engine, and logic interpreter |
| **Renderers** | Converters for HTML and DOCX outputs |
| **CLI** | Command-line interface to generate, test, and render contracts |

---

## ⚙️ Installation

```bash
git clone https://github.com/<your-username>/contracts-dsl-starter.git
cd contracts-dsl-starter
npm install
```

---

## 🧩 Usage

### 1. Build the project
```bash
npm run build
```

### 2. Run the CLI
```bash
npm start
```

### 3. Example: generate a contract
```bash
node packages/cli/src/index.js --facts examples/facts.msa-nl.json --render html
```

The system will:
- Parse input facts  
- Match applicable rules and clauses  
- Render the contract into `/out` as `msa-nl.html`

---

## 🧱 Example: Clause Definition

`packages/clauses/clause.gdpr.controller_processor.md`
```markdown
### Data Processing and GDPR Compliance

The Parties agree that data processing activities shall comply with the General Data Protection Regulation (EU 2016/679).
The Controller ensures that personal data is processed lawfully, fairly, and transparently.
```

---

## 🧰 Example: Rule Definition

`packages/rules/jurisdiction.nl.json`
```json
{
  "jurisdiction": "NL",
  "currency": "EUR",
  "governingLaw": "Dutch Civil Code",
  "defaultClauses": [
    "clause.governing_law.nl.md",
    "clause.gdpr.controller_processor.md"
  ]
}
```

---

## 🧩 Example: Facts File

`examples/facts.msa-nl.json`
```json
{
  "type": "MSA",
  "jurisdiction": "NL",
  "parties": {
    "buyer": "Company A",
    "supplier": "Company B"
  },
  "procurementModel": "twoEnvelope",
  "services": ["IT Infrastructure", "Maintenance"]
}
```

---

## 🖨️ Renderers

| Renderer | Output | Description |
|-----------|---------|-------------|
| `htmlRenderer.ts` | `.html` | Generates formatted HTML contracts |
| `docxRenderer.ts` | `.docx` | Generates editable Word documents |

---

## 🧮 Planned Features

- [ ] Multi-language clause support (EN / NL / RU / AR)
- [ ] Clause version control and comparison
- [ ] Visual contract graph (Mermaid / BPMN)
- [ ] Integration with OpenAI LLM for clause evaluation
- [ ] Web-based builder for DSL contract generation

---

## 🧑‍💻 Technologies

- **TypeScript**
- **Node.js**
- **JSON / Markdown / DOCX**
- **CLI-based modular design**
- **Pluggable renderers**

---

## 📜 License

Licensed under the **MIT License**.

```
MIT License

Copyright (c) 2025 Alexander Pavluchenko

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```

---

## 🤝 Contributing

Pull requests are welcome.  
For major changes, please open an issue first to discuss what you would like to change.

---

## 🧭 Author

**Alexander Pavluchenko**  
IT Infrastructure & Digitalization Projects  
IT Service International, Eurodesign CSC
📧 [GitHub Profile](https://github.com/ap8888)
