# Awesome-QA-Platform-Administration-Console

# Awesome QA Platform Administration Console

> A curated list of top QA Platform Administration Console platforms — both SaaS/Hosted commercial device cloud admin portals and open-source alternatives for managing users, teams, devices, and access governance across testing infrastructure.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Sauce Labs Admin](#sauce-labs-admin)
  - [Perfecto Console](#perfecto-console)
  - [Kobiton Portal](#kobiton-portal)
  - [Cypress Cloud Admin](#cypress-cloud-admin)
- [Open-Source Software](#-open-source-software)
  - [noob-test-manager](#noob-test-manager)
  - [Punchlist QA](#punchlist-qa)
  - [QA Studio](#qa-studio)
  - [testrarc](#testrarc)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted QA Platform Administration Console platforms. These are not open-source but are included as reference points for feature comparison.

### Sauce Labs Admin
**Type:** Organization, team, and concurrency administration  
Sauce Labs provides a centralized admin console through **Organization Management** with dedicated tabs for Users and Teams [citation:7][citation:13]. Key administrative capabilities include:
- **Team creation** with line-of-business association and **team VM concurrency limits** (e.g., 60 concurrent VMs per team) [citation:7]
- **Team membership management**: members can access projects belonging to their teams, with **Team Admin** roles able to invite users and set team roles [citation:1]
- **User assignment**: a user can only be assigned to one team, and changing assignment removes the previous association [citation:13]
- **Deletion safeguards**: teams containing service accounts cannot be deleted; teams with only user accounts can be deleted with member reassignment [citation:7]

Only Account Owners and Org Admins can create/delete teams and change member team roles [citation:1].  
**Best for:** Enterprises needing structured team isolation with concurrency governance and clear role hierarchies for testing infrastructure.

### Perfecto Console
**Type:** Device lab administration with roles and org groups  
Perfecto's admin console (Assets and Setup > Admin) provides user management, org group creation, and role assignment [citation:2]. Key capabilities:
- **Org groups** for organizing users by manager, project, or team, though groups do **not** impact access privileges—those are controlled by roles [citation:2]
- **Standard roles** include Administrator (full lab privileges) and Handset Viewer (manual/automated testing, view/stop executions) [citation:2]
- **Legacy role matrix** covers granular permissions like INTERACTIVE, AUTOMATION, ADVANCED_AUTOMATION, HANDSET_ADMINISTRATOR, USER_ADMINISTRATOR, and more [citation:14]
- **Device management** via the Devices view, available only in private clouds [citation:8]

Roles can be changed at any time, and custom roles can be assigned to dedicated devices [citation:14].  
**Best for:** Private cloud and enterprise device lab administrators needing granular role-based access with device-level control.

### Kobiton Portal
**Type:** Organization management with predefined and custom RBAC  
Kobiton's Org Management provides user, role, and team administration [citation:15]. Key administrative features:
- **Predefined roles**: Organization Owner (all permissions, transferable), ADMIN (all permissions + device management), and MEMBER (basic login and app view) [citation:3]
- **Granular permissions** across categories including App Repo, Devices, Org Management, Settings, Sessions, and Subscriptions [citation:3]
- **Team management** for grouping users with shared permissions [citation:9]
- **User role assignment** required for all users (at least one role per user) [citation:15]

The permission model is detailed enough to separate device administration from session management and organization settings.  
**Best for:** Teams needing a clear predefined role hierarchy with granular permission categories for device cloud administration.

### Cypress Cloud Admin
**Type:** Organization-level administration with centralized AI and security controls  
Cypress Cloud's admin console is built around **organizations** as the central control plane [citation:4][citation:10]. Key administrative capabilities:
- **User and team management** with roles granting access to specific projects, enabling multiple business units to share one organization [citation:4]
- **Centralized Cloud AI toggle**: organization admins and owners can enable or disable AI capabilities (test authoring, error summaries, test analysis) for the entire organization [citation:10]
- **Member privileges**: control whether non-admin members can create public projects (visible to anyone on the internet) [citation:10]
- **Billing and usage** rollup across all projects for capacity planning and spend attribution [citation:4]
- **Organization-level integrations** for source control, issue tracking, and chat, set up once and applied across every project [citation:4]

Organization ID is available for support reference, and ownership can be transferred by granting the Owner role to another user [citation:10].  
**Best for:** Organizations wanting centralized governance of AI, security, billing, and integrations across multiple projects and teams.

---

## 🟩 Open-Source Software

Self-hosted, community-driven QA Platform Administration Console tools. The open-source ecosystem is **limited and fragmented**, with most projects focused on test management rather than full administrative consoles.

### noob-test-manager
**Stack:** Node.js / SQLite / CLI + Browser UI | **License:** Open Source  
noob-test-manager (published as `@ai-sdet/test-manager`) is a lightweight, self-hosted test case management tool with **built-in admin account provisioning** [citation:5]. Key administrative features:
- **Automatic super admin creation** on first run with a default admin account (overridable via environment variables) [citation:5]
- **App → Space → Folder → Test** hierarchy with per-space member access [citation:5]
- **Run management** with environment labels, bulk pass/fail/skip/block marking, and live pass-rate progress [citation:5]
- **AI settings** configured under Admin Settings for LLM and vector embedding providers (OpenAI, Amazon Bedrock) [citation:5]

Runs as a CLI that spins up a local server with a browser UI, storing data in a local SQLite file with no SaaS subscription [citation:5].  
**Best for:** SDETs and small QA teams wanting a self-hosted test management tool with automatic admin provisioning and local data storage, accepting the CLI-first deployment model.

### Punchlist QA
**Stack:** Node.js / PostgreSQL / Docker | **License:** Open Source  
Punchlist QA is a standalone QA testing dashboard and support widget toolkit with **multi-repo administration** . Key administrative features:
- **Multi-repo support**: a single hosted instance supports multiple projects, with repos added via dashboard and switched via dropdown 
- **Tester management**: CLI commands for inviting testers (`invite`), revoking access (`revoke`), and listing users (`users`) 
- **Admin account creation** on first visit to the hosted instance 
- **AI skills** that auto-generate test cases from codebases 

Deploys via Render blueprint (one-click) or Docker, with PostgreSQL for persistence .  
**Best for:** Teams wanting a hosted QA dashboard with multi-repo support, tester invite/revoke workflows, and GitHub issue integration, accepting a Render/Docker deployment model.

### QA Studio
**Stack:** SvelteKit / PostgreSQL / Prisma | **License:** AGPL-3.0  
QA Studio is a modern open-source test management platform with **self-hosted authentication** (bcrypt and session management) and a comprehensive REST API [citation:12]. Key administrative features:
- **Team invitations** with role-based access [citation:12]
- **Hierarchical test suites** with full traceability and test execution across environments [citation:12]
- **Rich media attachments** (screenshots, videos, logs, stack traces) with configurable storage [citation:12]
- **API-first design**: every feature available via REST API [citation:12]

Self-hostable on Vercel, Docker, or any Node.js host [citation:12].  
**Best for:** QA teams wanting a modern, API-first test management platform with self-hosted auth and role-based team invitations, accepting the Vercel Blob dependency for attachments.

### testrarc
**Stack:** Python / Rio web framework | **License:** Open Source  
testrarc is a web-based testing tracker used by the Rocky Enterprise Software Foundation to track testing of Rocky Linux release candidates . Key administrative features:
- **Admin page** at `/app/admin/TestGroups` for adding, editing, reordering, and deleting TestGroups without direct DB manipulation 
- **Role-based access**: viewer (see results, not submit), tester (submit results), admin (test editing), and lead (define AdminPass) 
- **UserRoles mapping** for one-to-many role assignments 

Includes delete guards (blocks deleting groups with tests) and op-time admin role re-checks .  
**Best for:** Linux distribution testing teams needing a focused, role-based test tracking console, accepting a narrower scope than commercial platforms.

---

## 📊 Comparison at a Glance

| Software | License | Stack | User Mgmt | Team/Org Mgmt | Role Granularity | Self-Hosted | Best For |
|----------|---------|-------|-----------|---------------|------------------|-------------|----------|
| **Sauce Labs** | Proprietary | Cloud | ✅ | ✅ Teams + LOB | Team Admin / Member | ❌ | Concurrency-governed team isolation |
| **Perfecto** | Proprietary | Cloud/On-prem | ✅ | ✅ Org groups | Granular role matrix | (Private) | Device lab with role-based access |
| **Kobiton** | Proprietary | Cloud/On-prem | ✅ | ✅ Teams | Predefined + custom | (On-prem) | Predefined RBAC with device control |
| **Cypress Cloud** | Proprietary | Cloud | ✅ | ✅ Organizations | Owner / Admin / Member | ❌ | Centralized AI + security governance |
| **noob-test-manager** | Open Source | Node.js/SQLite | ✅ Auto admin | ✅ Spaces | Per-space access | ✅ | Local test management + admin |
| **Punchlist QA** | Open Source | Node.js/Postgres | ✅ Invite/revoke | ✅ Multi-repo | Tester roles | ✅ | Multi-repo QA dashboard |
| **QA Studio** | AGPL-3.0 | SvelteKit/Postgres | ✅ | ✅ Team invites | Role-based | ✅ | API-first test management |
| **testrarc** | Open Source | Python/Rio | ✅ | ✅ TestGroups | viewer/tester/admin/lead | ✅ | Distro release testing |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source QA Platform Administration Console tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for **dedicated QA administration consoles** is **very limited** — most open-source QA tools are test management platforms rather than full administrative control planes. **noob-test-manager** and **Punchlist QA** are the closest open-source equivalents to a lightweight admin console, offering user invitation, role assignment, and multi-project/repo management [citation:5]. Commercial platforms like Sauce Labs and Cypress Cloud remain far more capable for enterprise-grade team isolation, concurrency governance, and centralized AI/security controls [citation:4][citation:7].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
