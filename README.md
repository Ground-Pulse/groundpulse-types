GroundPulse Shared Types & Contracts (`groundpulse-types`)

Shared TypeScript interfaces, Zod validation schemas, API contracts, and error definitions for the GroundPulse remote property monitoring platform.

---

## 📌 Work of This Repo
This package serves as the **single source of truth** for data contracts across the entire GroundPulse ecosystem. It defines:
- Common domain interfaces (`User`, `Property`, `Inspection`, `ChecklistItem`, `Issue`, `Repair`).
- Shared Zod validation schemas used identically on frontend forms and NestJS backend validation pipes.
- Standard API response envelopes and enum definitions (`GroundPulseErrorCode`, `InspectionStatus`, `RepairStatus`).

## ❓ Why We Created This Repo
In a microrepo architecture, keeping backend and frontend repositories synchronized is the primary challenge. Without this repository, updating a property field or changing a validation rule requires manual copy-pasting across multiple projects, leading to type drift and runtime production crashes. Importing this shared package guarantees strict end-to-end type safety between the API and all web dashboards.

## 🛠 Tech Stack
- **Language:** TypeScript 5.4+ (Strict Mode)
- **Validation:** Zod
- **Build Tooling:** `tsc` (TypeScript Compiler)

## 📁 File Structure
```text
groundpulse-types/
├── src/
│   ├── contracts/
│   │   ├── api-responses.ts
│   │   ├── error-codes.ts
│   │   └── events.ts
│   ├── models/
│   │   ├── audit.ts
│   │   ├── inspection.ts
│   │   ├── issue.ts
│   │   ├── property.ts
│   │   ├── repair.ts
│   │   └── user.ts
│   ├── schemas/
│   │   ├── inspection.schema.ts
│   │   ├── issue.schema.ts
│   │   └── property.schema.ts
│   └── index.ts
├── package.json
├── tsconfig.json
└── README.md




💻 Commands
Bash
# Install dependencies
npm install

# Build the TypeScript definitions
npm run build

# Type check
npm run type-check



📦 How to Consume in Other Repositories
Add to your package.json in groundpulse-api, groundpulse-web-owner, or groundpulse-web-ops:

JSON
{
  "dependencies": {
    "groundpulse-types": "github:Ground-Pulse/groundpulse-types#v1.0.0"
  }
}
