# groundpulse-types

Shared type definitions, Zod validation schemas, and domain interfaces for the GroundPulse platform[cite: 1].

---

## 🎯 Purpose of This Repo
This package serves as the single source of truth for all data contracts across the GroundPulse ecosystem[cite: 1]. It enables end-to-end type safety between the backend API and frontend client applications without code duplication[cite: 1].

## ❓ Why We Created This Repo
In a polyrepo setup, having independent frontend and backend repositories introduces the risk of schema drift. If an API request payload or database enum changes, client applications will fail at runtime unless they share the same contract. This repository eliminates drift by centralizing:
- Shared TypeScript interfaces and DTOs[cite: 1]
- Zod validation schemas reused across client forms and API validation pipes[cite: 1]
- Canonical enum definitions (Roles, Inspection Statuses, Repair Lifecycles)[cite: 1]
- Standard error codes (`GroundPulseErrorCode`)[cite: 1]

## 📂 File Structure
```text
groundpulse-types/
├── src/
│   ├── enums/
│   │   ├── roles.enum.ts              # OWNER, INSPECTOR, ADMIN, PROVIDER
│   │   ├── inspection-status.enum.ts  # SCHEDULED, IN_PROGRESS, SUBMITTED
│   │   ├── repair-status.enum.ts      # REQUESTED, ASSIGNED, IN_PROGRESS, COMPLETED
│   │   └── issue-category.enum.ts     # LEAK, ELECTRICAL, SECURITY, CLEANLINESS, OTHER
│   ├── interfaces/
│   │   ├── user.interface.ts
│   │   ├── property.interface.ts
│   │   ├── inspection.interface.ts
│   │   ├── checklist-item.interface.ts
│   │   ├── issue.interface.ts
│   │   └── repair.interface.ts
│   ├── schemas/                       # Shared Zod validation schemas
│   │   ├── issue.schema.ts            # flagIssueSchema
│   │   ├── inspection.schema.ts       # scheduleInspectionSchema
│   │   └── repair.schema.ts           # completeRepairSchema
│   ├── errors/
│   │   └── error-codes.ts             # Standard GroundPulse error codes
│   └── index.ts                       # Public API barrel export
├── package.json
├── tsconfig.json
└── README.md



💻 Commands
Bash
# Install dependencies
npm install

# Build the TypeScript types into dist/
npm run build

# Run type check
npm run type-check
📦 How to Consume in Other Repos
Add this dependency directly to package.json in your API and Web repositories:

JSON
{
  "dependencies": {
    "groundpulse-types": "github:Ground-Pulse/groundpulse-types#main"
  }
}
